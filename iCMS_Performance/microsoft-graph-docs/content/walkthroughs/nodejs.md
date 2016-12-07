# <a name="call-microsoft-graph-with-a-nodejs-app"></a>Call Microsoft Graph with a Node.js app

In diesem Artikel werden Aufgaben beschrieben, die zum Herstellen einer Verbindung zwischen Ihrer Anwendung und Office 365 und zum Aufrufen der Microsoft Graph-API mindestens erforderlich sind. Wir verwenden den Code aus [Office 365 Angular Connect-Beispiel unter Verwendung von Microsoft Graph](https://github.com/microsoftgraph/nodejs-connect-rest-sample), um die wichtigsten Konzepte zu erläutern, die Sie in Ihrer App implementieren müssen.

![Office 365 Node.js Connect sample screenshot](./images/web-screenshot.png)

## <a name="overview"></a>Übersicht

Zum Aufrufen der Microsoft Graph-API muss Ihre iOS-App die folgenden Aufgaben ausführen:

1. Registrieren der Anwendung in Azure Active Directory 
2. Install the Azure Active Directory Client Library for Node
3. Redirect the browser to the sign-in page
4. Receive an authorization code in your reply URL page
5. Verwenden des Autorisierungscodes zum Anfordern eines Zugriffstokens.
6. Verwenden des Zugriffstokens in einer Anforderung an die Microsoft Graph-API

<!--<a name="register"/>-->
## <a name="register-your-application-in-azure-active-directory"></a>Registrieren der Anwendung in Azure Active Directory

Bevor Sie  mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und die Berechtigungen für die Verwendung der Microsoft Graph-Dienste festlegen. Mithilfe des [App-Registrierungstools](https://dev.office.com/app-registration) können Sie mit nur wenigen Klicks Ihre Anwendung für den Zugriff auf ein Geschäfts- oder Schulkonto des Benutzers registrieren. Zum Verwalten müssen Sie das [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com) verwenden.

Alternativ können Sie die App manuell registrieren. Die Anweisungen dazu finden Sie im Abschnitt [Registrieren der Webserver-App mithilfe des Azure-Verwaltungsportals](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp). Beachten Sie dabei Folgendes:

* Specify a page in your Node.js app as the **Sign-on URL** in step 6. In the case of the Connect sample, the URL is http://localhost:8080/login, which maps to the [/login](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L33) route.
* Konfigurieren Sie die **delegierten Berechtigungen**, die für Ihre App erforderlich sind. Für das Connect-Beispiel ist die Berechtigung zum **Senden von E-Mails als angemeldeter Benutzer** erforderlich.

Notieren Sie sich die folgenden Werte auf der Seite **Konfigurieren** Ihrer Azure-Anwendung.

* Client-ID
* A valid key
* A reply URL

Sie benötigen diese Werte zum Konfigurieren des OAuth-Flusses in Ihrer App.

<!--<a name="adal">-->
## <a name="install-the-azure-active-directory-client-library-for-node"></a>Install the Azure Active Directory Client Library for Node

The ADAL for Node.js library makes it easy for Node.js applications to authenticate to AAD in order to access AAD protected web resources. To add adal-node to your existing `package.json` enter the following into your preferred terminal.

`npm install adal-node --save`

For more information about the adal-node client library, see its package info on [npm](https://www.npmjs.com/package/adal-node). For issues, source code, and the latest in upcoming features and fixes, see adal-node's project on [Github](https://github.com/AzureAD/azure-activedirectory-library-for-nodejs).

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>Redirect the browser to the sign-in page

Your app needs to redirect the browser to the sign-in page to get an authorization code and continue the OAuth 2.0 flow.

In the Connect sample, the authentication URL from [`authHelper.js#getAuthUrl`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js#L17) is redirected by the [`login.hbs#login`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/views/login.hbs#L2) function through a client-side `onclick` event.

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

**login.hbs#login**
```javascript
function login() {
    window.location = '{{auth_url}}'.replace(/&amp;/g, '&'); // transform HTML special char from .hbs template rendering
}
```

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>Receive an authorization code in your reply URL page

After the user signs in, the flow returns the browser to the reply URL in your app. The authorization code is provided in the `code` query string variable.

```javascript
router.get('/<application reply url>', function (req, res, next) {
  var authCode = req.query.code;
  // your router's implementation
});
```

See the [relevant code](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L34) in the Connect sample

<!--<a name="accesstoken"/>-->
## <a name="use-adal-node-to-request-an-access-token"></a>Verwenden des Autorisierungscodes zum Anfordern eines Zugriffstokens.

Now that we've authenticated with Azure Active Directory, our next step is to acquire an access token via adal-node. After we've done that, we'll be ready to make REST requests to the Microsoft Graph API.

To request an access token, adal-node provides two callback functions.

|                          Funktion                         |                                      Params                                      | Beschreibung                                                                                             |
|:---------------------------------------------------------:|:--------------------------------------------------------------------------------:|---------------------------------------------------------------------------------------------------------|
| `AuthenticationContext.acquireTokenWithAuthorizationCode` | `authCode`, `redirect_uri`, `resource`, `client_id`, `client_secret`, `callback` | provides an access token for a specified resource based on the authorization code returned during login |
| `AuthenticationContext.acquireTokenWithRefreshToken`      | `token`, `client_id`, `client_secret`, `resource`, `callback`                    | provides an access token for a specified resourced based on a refresh token                             |

In the Connect sample, requests are routed through [`authHelper.js`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js) so that the `client_id` and `client_secret` can be added.

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
## <a name="make-a-request-to-the-microsoft-graph-api"></a>Verwenden des Zugriffstokens in einer Anforderung an die Microsoft Graph-API

To identify our requests to the Graph API, our requests must be signed with an `Authorization` header containing the access token for any web service resource we request. A properly formed authorization header will include the access token from adal-node and will take the following form.

`Authorization: Bearer <access token>`

Using `adal-node`, combined with our authentication logic from the previous section, we can now use our access token to sign requests.

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

Microsoft Graph ist eine leistungsfähige einheitliche API, die für die Interaktion mit beliebigen Microsoft-Daten verwendet werden kann. Informationen zu weiteren Möglichkeiten mit der Microsoft Graph-API finden Sie in der [API-Referenz](http://graph.microsoft.io/docs/api-reference/v1.0).

<!--## Additional resources

- [Office 365 Node.js Connect sample using Microsoft Graph](https://github.com/OfficeDev/O365-Nodejs-Unified-API-Connect)-->

