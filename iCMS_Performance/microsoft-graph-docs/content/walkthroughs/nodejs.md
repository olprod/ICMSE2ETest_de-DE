# <a name="call-microsoft-graph-with-a-nodejs-app"></a>Rufen Sie mit einer app Node.js Microsoft Graph

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden Ihrer Anwendung zu Office 365, und rufen Sie die Microsoft Graph-API ein. Wir verwenden Code aus die [Verbindung zu Office 365 Node.js Beispiel mit Microsoft Graph](https://github.com/microsoftgraph/nodejs-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen.

![Office 365 verbinden Node.js Beispiel screenshot](./images/web-screenshot.png)

## <a name="overview"></a>Übersicht

Um die Microsoft Graph-API aufzurufen, muss Ihre Web-app die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory 
2. Installieren der Azure Active Directory-Clientbibliothek für Knoten
3. Umleiten des im Browser zu der Seite Anmeldung
4. Empfangen eines Autorisierungscodes in der Antwort-URL-Seite
5. Verwenden Sie `adal-node` ein Zugriffstoken anfordern
6. Wenden Sie sich an die Microsoft Graph-API

<!--<a name="register"/>-->
## <a name="register-your-application-in-azure-active-directory"></a>Registrieren Sie Ihre Anwendung in Azure Active Directory

Bevor Sie das Arbeiten mit Office 365 beginnen können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph Services.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung für den Zugriff eines Benutzers Arbeit "oder" Schule Konto, mit dem die [Anwendung Registration-Tool](https://dev.office.com/app-registration)auf registrieren. Verwalten, die Sie benötigen, um [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com) zu wechseln

Alternativ dazu finden Sie im Abschnitt [Registrieren Ihrer Anwendung Server mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Geben Sie eine Seite in Ihrer app Node.js als die **Sign-on URL** in Schritt 6. Im Fall der Connect-Beispiel ist die URL http://localhost: 8080/anmelden, der die [/login](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L33) Route zugeordnet ist.
* [Konfigurieren der **delegierten Berechtigungen** ](https://github.com/microsoftgraph/nodejs-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) , die Ihre app benötigt. Beispiel für Connect erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung.

* Client-ID
* Ein gültiger-Schlüssel
* Eine Antwort-URL

Sie benötigen diese Werte als Parameter für den Ablauf des OAuth in Ihrer app.

<!--<a name="adal">-->
## <a name="install-the-azure-active-directory-client-library-for-node"></a>Installieren der Azure Active Directory-Clientbibliothek für Knoten

Das ADAL für Node.js Bibliothek vereinfacht Node.js Applications AAD authentifizieren, um AAD geschützten Webressourcen zugreifen.
Hinzufügen adal Knoten zum vorhandenen `package.json` Geben Sie Folgendes in Ihrer bevorzugten Terminal.

`npm install adal-node --save`

Weitere Informationen zu der adal-Knoten-Clientbibliothek finden Sie unter seiner Paketinfo auf [Npm](https://www.npmjs.com/package/adal-node).
Probleme, Quellcode und die neuesten in Kürze verfügbare Funktionen und Fixes finden Sie unter adal-Knoten des Projekts auf [Github](https://github.com/AzureAD/azure-activedirectory-library-for-nodejs).

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>Umleiten von im Browser zur Seite-Anmeldung

Ihre app muss im Browser zur Seite Anmeldung zum Abrufen eines Autorisierungscodes und weiterhin den Ablauf des OAuth 2.0 umzuleiten.

Im Beispiel verbinden die URL der Authentifizierung von [`authHelper.js#getAuthUrl`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js#L17) umgeleitet wird, durch die [`login.hbs#login`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/views/login.hbs#L2) Funktion über eine mithilfe der clientseitigen `onclick` Ereignis.

**authHelper.js#getAuthUrl**
```javascript
/**
 * Generate a fully formed uri to use for authentication based on the supplied resource argument
 * @return {string} a fully formed uri with which authentcation can be completed
 */
function getAuthUrl() {
    return credentials.authority + "/oauth2/authorize" +
        "?client_id=" + credentials.client_id +
        "&response_type=code" +
        "&redirect_uri=" + credentials.redirect_uri;
};
```

**Login.hbs#Login**
```javascript
function login() {
    window.location = '{{auth_url}}'.replace(/&amp;/g, '&'); // transform HTML special char from .hbs template rendering
}
```

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>Erhalten Sie einen Autorisierungscode in der Antwort-URL-Seite

Nachdem der Benutzer anmeldet, gibt der Ablauf der Browser auf die Antwort-URL in Ihrer app. Der Autorisierungscode gemäß der `code` Abfragezeichenfolgen-Variable.

```javascript
router.get('/<application reply url>', function (req, res, next) {
  var authCode = req.query.code;
  // your router's implementation
});
```

Finden Sie unter den [entsprechenden Code](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L34) in der Connect-Beispiel

<!--<a name="accesstoken"/>-->
## <a name="use-adal-node-to-request-an-access-token"></a>Verwenden Sie `adal-node` ein Zugriffstoken anfordern

Nachdem wir mit Azure Active Directory authentifiziert haben, besteht der nächste Schritt darin ein Zugriffstoken über adal-Knoten zu erwerben. Nachdem wir entworfen haben, werden wir vornehmen von REST-Anforderungen für die Microsoft Graph-API bereit sein.

Um ein Zugriffstoken anfordern, enthält adal Knoten zwei Rückruffunktionen.

|                          Funktion                         |                                      Params                                      | Beschreibung                                                                                             |
|:---------------------------------------------------------:|:--------------------------------------------------------------------------------:|---------------------------------------------------------------------------------------------------------|
| `AuthenticationContext.acquireTokenWithAuthorizationCode` | `authCode`, `redirect_uri`, `resource`, `client_id`, `client_secret`, `callback` | enthält ein Zugriffstoken für eine angegebene Ressource basierend auf den Autorisierungscode zurückgegeben, bei der Anmeldung |
| `AuthenticationContext.acquireTokenWithRefreshToken`      | `token`, `client_id`, `client_secret`, `resource`, `callback`                    | bietet ein Zugriffstoken für ein angegebenes basierend auf einer Aktualisierungstoken Ressourcen zugewiesen                             |

Im Beispiel Connect Anforderungen durch weitergeleitet [`authHelper.js`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js) , damit die `client_id` und `client_secret` hinzugefügt werden können.

```javascript
// The application registration (must match Azure AD config)
var credentials = {
    authority: "https://login.microsoftonline.com/common",
    client_id: "<your client id here>",
    client_secret: "<your client secret>",
    redirect_uri: "http://localhost:8080/login"
};

/**
 * Gets a token for a given resource.
 * @param {string} code An authorization code returned from a client.
 * @param {string} res A URI that identifies the resource for which the token is valid.
 * @param {AcquireTokenCallback} callback The callback function.
 */
function getTokenFromCode(res, code, callback) {
    var authContext = new AuthenticationContext(credentials.authority);
    authContext.acquireTokenWithAuthorizationCode(code, credentials.redirect_uri, res, credentials.client_id, credentials.client_secret, function (err, response) {
        if (err) {
            callback(null);
        }
        else {
            callback(response);
        }
    });
};
```

<!--<a name="request"/>-->
## <a name="make-a-request-to-the-microsoft-graph-api"></a>Wenden Sie sich an die Microsoft Graph-API

Unsere Anforderungen an das Diagramm-API um zu ermitteln, müssen unsere Anfragen mit signiert werden eine `Authorization` Header, enthält das Zugriffstoken für alle Web-service Ressource wir anfordern. Ein ordnungsgemäß gebildeten Authorization-Header enthält das Zugriffstoken vom adal Knoten und dauert das folgende Format.

`Authorization: Bearer <access token>`

Mit `adal-node`, zusammen mit der unsere Authentifizierungslogik aus dem vorherigen Abschnitt, wir können nun unsere Zugriffstoken um Anfragen zu signieren.

```javascript
/* GET home page. */
router.get('/<application reply url>', function (req, res, next) {
    var authCode = req.query.code;
    authHelper.getTokenFromCode('https://graph.microsoft.com/', req.query.code, function (token) {
        if (token !== null) {
            // Use this token to sign requests
            var headers = {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + token
                };
            // request implementation...
        } else {
            // error handling
        }
    });
});
```

Das Microsoft Graph ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden kann. Checken Sie die [API-Referenz](http://graph.microsoft.io/docs/api-reference/v1.0) zum untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

<!--## Additional resources

- [Office 365 Node.js Connect sample using Microsoft Graph](https://github.com/OfficeDev/O365-Nodejs-Unified-API-Connect)-->

