# <a name="call-microsoft-graph-in-a-php-app"></a>Rufen Sie Microsoft Graph in eine PHP-app 

In diesem Artikel betrachten wir die minimalen Aufgaben erforderlich, um eine Access token Abrufen von Azure Active Directory (AD), und rufen Sie die Microsoft Graph-API. Wir verwenden Code aus dem [Office 365 PHP verbinden Beispiel mithilfe von Microsoft Graph](https://github.com/microsoftgraph/php-connect-rest-sample) die wichtigsten Konzepte erläutern, die Sie in Ihrer app implementieren müssen.

![Office 365 verbinden PHP Beispiel screenshot](./images/web-screenshot.png)

## <a name="overview"></a>Übersicht

Um die Microsoft Graph-API-aufrufen, muss Ihre app PHP die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory
2. Umleiten des im Browser zu der Seite Anmeldung
3. Empfangen eines Autorisierungscodes in der Antwort-URL-Seite
4. Fordern Sie ein Zugriffstoken aus der Endpunkt-token
5. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

<!--<a name="register"/>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ dazu finden Sie im Abschnitt [Registrieren Ihrer Anwendung Server mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Geben Sie eine Seite in Ihrer app PHP als die **Sign-on URL** in Schritt 6. Im Beispiel verbinden sich diese Seite ist [`Callback.php`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/app/callback.php).
* [Konfigurieren der **delegierten Berechtigungen** ](https://github.com/microsoftgraph/php-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) , die Ihre app benötigt. Beispiel für Connect erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung.

* Client-ID
* Ein gültiger-Schlüssel
* Eine Antwort-URL

Sie benötigen diese Werte als Parameter in der OAuth-Ablauf in Ihrer app.

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>Umleiten des im Browser zu der Seite Anmeldung

Ihre app muss im Browser zur Seite Anmeldung zum Abrufen eines Autorisierungscodes und weiterhin den OAuth-Ablauf umleiten.

Im Beispiel Verbinden der Code, der den Browser umleitet befindet sich in der [`AuthenticationManager.connect`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/AuthenticationManager.php#L41) Funktion.

```php
// Redirect the browser to the authorization endpoint. Auth endpoint is
// https://login.microsoftonline.com/common/oauth2/authorize
$redirect = Constants::AUTHORITY_URL . Constants::AUTHORIZE_ENDPOINT . 
            '?response_type=code' . 
            '&client_id=' . urlencode(Constants::CLIENT_ID) . 
            '&redirect_uri=' . urlencode(Constants::REDIRECT_URI);
header("Location: {$redirect}");
exit();
```

> **Hinweis:** <br />
> Sie müssen den **Location** -Header vor dem Schreiben von keine Ausgabe auf der Seite senden.

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>Empfangen eines Autorisierungscodes in der Antwort-URL-Seite

Nachdem der Benutzer auf Anzeichen für die Einwahl gibt der Ablauf der Browser zur URL Antwort in Ihrer app. Azure fügt einen Autorisierungscode an die Abfragezeichenfolge an. Das Connect-Beispiel verwendet die [`Callback.php`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/app/callback.php) Seite für diesen Zweck.

Der Autorisierungscode erfolgt der `code` Abfragezeichenfolgen-Variable. Beispiel für Connect speichert der Code in einer Sitzungsvariablen, ihn später zu verwenden.

```php
if (isset($_GET['code'])) {
    $_SESSION['code'] =  $_GET['code'];
}
```

<!--<a name="accesstoken"/>-->
## <a name="request-an-access-token-from-the-token-endpoint"></a>Fordern Sie ein Zugriffstoken vom token Endpunkt

Nachdem Sie den Autorisierungscode haben, können Sie sie an die Client-ID wichtige und Beantworten von URL-Werte, die Sie von Azure AD Zugriff anfordern token erhalten haben. 

> **Hinweis:** <br />
> Die Anforderung muss auch eine Ressource angeben, die wir nutzen möchten. Im Fall von Microsoft Graph-API, wird der Wert der `https://graph.microsoft.com`.

Beispiel für Connect fordert ein Token mithilfe des Codes in der [`AuthenticationManager.acquireToken`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/AuthenticationManager.php#L62) Funktion. Es folgt der höchsten relevante Code.

```php
$tokenEndpoint = Constants::AUTHORITY_URL . Constants::TOKEN_ENDPOINT;

// Send a POST request to the token endpoint to retrieve tokens.
// Token endpoint is:
// https://login.microsoftonline.com/common/oauth2/token
$response = RequestManager::sendPostRequest(
    $tokenEndpoint, 
    array(),
    array(
        'client_id' => Constants::CLIENT_ID,
        'client_secret' => Constants::CLIENT_SECRET,
        'code' => $_SESSION['code'],
        'grant_type' => 'authorization_code',
        'redirect_uri' => Constants::REDIRECT_URI,
        'resource' => Constants::RESOURCE_ID
    )

// Store the raw response in JSON format.
$jsonResponse = json_decode($response, true);

// The access token response has the following parameters:
// access_token - The requested access token.
// expires_in - How long the access token is valid.
// expires_on - The time when the access token expires.
// id_token - An unsigned JSON Web Token (JWT).
// refresh_token - An OAuth 2.0 refresh token.
// resource - The App ID URI of the web API (secured resource).
// scope - Impersonation permissions granted to the client application.
// token_type - Indicates the token type value.
foreach ($jsonResponse as $key=>$value) {
    $_SESSION[$key] = $value;
}
```

> **Hinweis:** <br />
> Die Antwort enthält mehr Informationen als nur das Zugriffstoken, beispielsweise Ihre app erhalte eine Aktualisierung token neues Zugriffstoken anfordern, ohne dass des Benutzers explizit Anmeldung.

Ihre app PHP können jetzt die Sitzungsvariable `access_token` zum Ausstellen von authentifizierter Anforderungen für die Microsoft Graph-API.

<!--<a name="request"/>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. Ihre app muss das Zugriffstoken im **Authorization** -Header jeder Anforderung bereitstellen.

Beispiel für Connect sendet eine e-Mail mithilfe des **SendMail** -Endpunkts in der Microsoft Graph-API. Der Code befindet sich in der [`MailManager.sendWelcomeMail`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/MailManager.php#L40) Funktion. Dies ist der Code, der zeigt, wie der Zugriffscode im Authorization-Header gesendet.

```php
// Send the email request to the sendmail endpoint, 
// which is in the following URI:
// https://graph.microsoft.com/v1.0/me/microsoft.graph.sendMail
// Note that the access token is attached in the Authorization header
RequestManager::sendPostRequest(
    Constants::RESOURCE_ID . Constants::SENDMAIL_ENDPOINT,
    array(
        'Authorization: Bearer ' . $_SESSION['access_token'],
        'Content-Type: application/json;' . 
                      'odata.metadata=minimal;' .
                      'odata.streaming=true'
    ),
    $email
);
```

> **Hinweis:** <br />
> Senden der Anforderung muss auch einen **Content-Type** -Header mit einem Wert von beispielsweise die Microsoft Graph-API akzeptiert `application/json;odata.metadata=minimal;odata.streaming=true`.

Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die API-Referenz zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

<!--## Additional resources

-  [Office 365 PHP Connect sample using Microsoft Graph API](https://github.com/OfficeDev/O365-PHP-Unified-API-Connect)-->
