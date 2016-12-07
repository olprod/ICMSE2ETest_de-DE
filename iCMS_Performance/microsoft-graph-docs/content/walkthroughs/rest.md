# <a name="platform-specific-walkthroughs"></a>Plattformspezifische Vorgehensweisen

Testen Sie einen beispielhaften REST-Aufruf in unserem [API Explorer](https://graph.microsoft.io/graph-explorer).

Kehren Sie, sobald Sie mit dem Testen der API fertig sind, hierher zurück, und wählen Sie Ihre bevorzugten Plattform auf der linken Seite aus. Sie werden durch das Schreiben einer einfachen Anwendung zum Abrufen von E-Mails mithilfe der Microsoft Graph-API geführt.

Wenn Ihre bevorzugte Plattform nicht aufgeführt ist, fahren Sie mit dem Lesen dieser Seite fort. Hier werden die gleichen Schritte unter Verwendung von unformatierten HTTP-Anforderungen beschrieben.

## <a name="getting-started-with-the-microsoft-graph-api-and-rest"></a>Erste Schritte mit der Microsoft Graph-API und REST

In diesem Leitfaden werden Sie schrittweise durch den Prozess des Aufrufs der Microsoft Graph-API zum Abrufen und Senden von Nachrichten in Office 365 und Outlook.com geführt. Im Gegensatz zu den plattformspezifischen Vorgehensweisen liegt in diesem Leitfaden der Fokus auf OAuth- und REST-Anforderungen und Antworten. Es wird die Abfolge der Anforderungen und Antworten behandelt, die eine App zum Authentifizieren und Abrufen von Nachrichten verwendet.

## <a name="using-oauth-20-to-authenticate"></a>Verwenden der OAuth 2.0-Authentifizierung

Zum Aufrufen von Microsoft Graph benötigt Ihre App einen Zugriffstoken aus Azure Active Directory (Azure AD). Die App implementiert den Authorization Code Grant-Datenfluss zum Abrufen der Zugriffstoken aus Azure AD. Die App muss registriert sein, um die Authentifizierung und den Autorisierungsdatenfluss gemäß den [OAuth 2.0-Protokollen](http://tools.ietf.org/html/rfc6749) für den ordnungsgemäßen Authorization Code Grant-Datenfluss zu verwenden.

### <a name="registering-an-app"></a>Registrieren einer App

Es gibt derzeit zwei Optionen zur Registrierung einer App.

  1. Registrieren unter Verwendung des allgemein verfügbaren Modells für eine App für die Interaktion mit kommerziellen Office 365-Benutzern, mit Geschäfts- und Schulkonten.
 
  This model only works with Office 365 commercial offerings. Once you've registered your app, you can manage it through the [Azure Management Portal](https://manage.windowsazure.com).

  2. Register using the latest functionality that works for both consumer and commercial Office 365 services (we call it Auth endpoint v2.0).
 
  Ein einziger Authentifizierungsdienst für Geschäfts- oder Schulkonten und persönliche Konten ist nun in der Vorschau verfügbar. Dieses Modell bietet einen Authentifizierungsdienst für Geschäfts- und Schulkonten (Azure AD) und für persönliche Konten (Microsoft). Jetzt müssen Sie nur einen Authentifizierungsfluss in Ihrer App implementieren, um Benutzern das Verwenden von Geschäfts- oder Schulkonten, z. B. Office 365 oder OneDrive for Business, oder persönlichen Konten wie Outlook.com oder OneDrive zu ermöglichen.
   
Use the [Application Registration Portal](https://apps.dev.microsoft.com/) to register your app and support both work and school and personal accounts.

Please note that the v2.0 endpoint is gradually growing to cover all the scenarios from the previous auth endpoint. To choose whether is right for you read [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/)

Beim Registrieren der App erhalten Sie eine Client-ID und einen geheimen Schlüssel. Diese Werte werden in dem Authorization Code Grant-Datenfluss verwendet.

The rest of this document assumes a registration on the v2.0 model. For a complete guide to the flows supported in the v2.0 endpoint see [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-flows/), for a complete guide to the Authorization Code Grant flow see [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oauth-code/)

### <a name="getting-an-authorization-code"></a>Abrufen eines Autorisierungscodes

Im ersten Schritt des Authorization Code Grant-Datenflusses wird der Autorisierungscode abgerufen. Dieser Code wird von Azure AD an die App zurückgegeben, wenn der Benutzer sich anmeldet und der Zugriffsstufe zustimmt, die die App erfordert.

Die App generiert zunächst eine Anmelde-URL für den Benutzer. Diese URL muss in einem Browser geöffnet werden, damit der Benutzer sich anmelden und seine Zustimmung erteilen kann.

Die Basis-URL für die Anmeldung sieht wie folgt aus: https://login.microsoftonline.com/common/oauth2/authorize`https://login.microsoftonline.com/common/oauth2/v2.0/authorize`.

Die App fügt Abfrageparameter an diese Basis-URL an, um Azure AD mitzuteilen, welche App die Anmeldung anfordert und welche Berechtigungen angefordert werden.

- client_id`client_id` Die beim Registrieren der App generierte Client-ID. Anhand dieser erkennt Azure AD, welche App die Anmeldung anfordert.
- redirect_uri`redirect_uri` Der Speicherort, zu dem Azure umleitet, nachdem der Benutzer seine Zustimmung für diese App erteilt hat. Dieser Wert muss mit dem Wert des beim Registrieren der App verwendeten **Umleitungs-URI** übereinstimmen.
- response_type`response_type` Der Antworttyp, den die App erwartet. Dieser Wert ist code`code` für den Authorization Code Grant-Datenfluss.
- `scope` - A space-separated list of scopes that the app is requesting. More information in [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)
- `state` - A value included in the request that will also be returned in the token response.

Die Anforderungs-URL für unsere Anwendung, die den Lesezugriff auf E-Mails anfordert, sieht beispielsweise wie folgt aus.

```http
GET https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=<CLIENT ID>&redirect_uri=http%3A%2F%2Flocalhost/myapp%2F&response_type=code&state=1234&scope=https%3A%2F%2Fgraph.microsoft.com%2Fmail.read
```

Leiten Sie dann den Benutzer zu der Anmelde-URL weiter. Es wird ein Anmeldefenster mit dem Namen der App angezeigt. Nach dem Anmelden wird eine Liste der Berechtigungen angezeigt, die die App anfordert, und der Benutzer wird aufgefordert, diesen zuzustimmen oder sie zu verweigern. Wenn Benutzer dem erforderlichen Zugriff zustimmen, erfolgt im Browser eine Umleitung an den Umleitungs-URI, der in der ursprünglichen Anforderung mit dem Autorisierungscode in der Abfragezeichenfolge angegeben wurde.

```http
http://localhost/myapp/?code=AwABAAAA...cZZ6IgAA&state=1234
```

If you are also using OpenId Connect for Single Sign On, additional parameters are required, see [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oidc/) for more information. 

Im nächsten Schritt wird der von Azure AD für ein Zugriffstoken zurückgegebene Autorisierungscode ausgetauscht.

### <a name="getting-an-access-token"></a>Abrufen eines Zugriffstokens

Zum Abrufen eines Zugriffstokens stellt die App fomularcodierte Parameter für die Tokenanforderungs-URL (https://login.microsoftonline.com/common/oauth2/token`https://login.microsoftonline.com/common/oauth2/v2.0/token`) mit den folgenden Parametern bereit.

- client_id`client_id` Die beim Registrieren der App generierte Client-ID.
- client_secret`client_secret` Der beim Registrieren der App generierte geheime Clientschlüssel.
- code`code` Der im vorherigen Schritt abgerufene Autorisierungscode.
- redirect_uri`redirect_uri` Dieser Wert muss mit dem in der Autorisierungscodeanforderung verwendeten Wert übereinstimmen.
- grant_type`grant_type` Der von der App verwendete Typ des Zugriffs. Dieser Wert ist code`code` für den Authorization Code Grant-Datenfluss.
- `scope` - A space-separated list of scopes that the app is requesting. More information in [this article](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)

Die Anforderungs-URL für unsere Anwendung sieht unter Verwendung des Codes aus dem vorherigen Schritt wie folgt aus.

```http
POST https://login.microsoftonline.com/common/oauth2/v2.0/token
Content-Type: application/x-www-form-urlencoded

{
  grant_type=authorization_code
  &code=AwABAAAA...cZZ6IgAA
  &redirect_uri=http%3A%2F%2Flocalhost%2Fmyapp%2F
  &resource=https%3A%2F%2Fgraph.microsoft.com%2F
  &scope=https%3A%2F%2Fgraph.microsoft.com%2Fmail.read
  &client\_id=<CLIENT ID>
  &client\_secret=<CLIENT SECRET>
}
```

Azure AD antwortet mit einer JSON-Nutzlast, die das Zugriffstoken enthält.

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "token_type":"Bearer",
  "expires_in":"3600",
  "access_token":"eyJ0eXAi...b66LoPVA",
  "scope":"https://graph.microsoft.com/mail.read",
  ...
}
```

Das Zugriffstoken befindet sich im Feld access_token`access_token` der JSON-Nutzlast. Die App verwendet diesen Wert zum Festlegen des Autorisierungsheaders bei REST-Aufrufen für die API.

## <a name="calling-the-microsoft-graph"></a>Aufrufen von Microsoft Graph

Wenn die App über ein Zugriffstoken verfügt, kann Microsoft Graph aufgerufen werden. Da diese Beispiel-App Nachrichten abruft, verwendet sie eine HTTP-GET-Anforderung für den https://graph.microsoft.com/v1.0/me/messages`https://graph.microsoft.com/v1.0/me/messages`-Endpunkt.

### <a name="refining-the-request"></a>Optimieren der Anforderung

Apps können das Verhalten der GET-Anforderungen mithilfe von OData-Abfrageparametern steuern.  Diese Parameter sollten von den Apps verwendet werden, um die Anzahl der zurückgegebenen Ergebnisse und der für jedes Element zurückgegebenen Felder einzuschränken. 

In unserer Beispiel-App werden die Nachrichten in einer Tabelle angezeigt, in der Betreff, Absender und der Zeitpunkt enthalten sind, zu dem die Nachricht empfangen wurde. In der Tabelle werden maximal 25 Zeilen angezeigt, wobei diese so sortiert sind, dass zuletzt empfangene Nachrichten oben aufgeführt sind. Die App verwendet die folgenden Abfrageparameter, um diese Ergebnisse zu erzielen.

- Der $select-Parameter wird dazu verwendet, dass nur die Felder subject, sender und dateTimeReceived angezeigt werden.
- Der $top`$top`-Parameter wird zum Festlegen der maximalen Anzahl von 25 Elementen verwendet.
- Der Parameter $orderby`$orderby` wird zum Sortieren der Ergebnisse nach dem Feld dateTimeReceived`dateTimeReceived` verwendet.

Als Ergebnis erhält man die folgende Anforderung.

```http
GET https://graph.microsoft.com/v1.0/me/messages?$select=subject,from,receivedDateTime&$top=25&$orderby=receivedDateTime%20DESC
Accept: application/json
Authorization: Bearer eyJ0eXAi...b66LoPVA
```

Da Sie nun gelernt haben, wie Aufrufe für Microsoft Graph getätigt werden, können Sie anhand der API-Referenz beliebige Arten von Aufrufen erstellen, die für Ihre App erforderlich sind. Denken Sie daran, dass entsprechende Berechtigungen für die App bei der App-Registrierung für die Aufrufe konfiguriert sein müssen.


