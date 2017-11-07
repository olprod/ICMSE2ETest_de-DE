# <a name="platform-specific-walkthroughs"></a>Plattform bestimmte Exemplarische Vorgehensweisen

Probieren Sie eine Beispiel-REST-Aufrufs in unseren [API-Explorer](https://graph.microsoft.io/graph-explorer).

Sobald Sie fertig sind wieder hierher Erkunden der API, und wählen Sie Ihre bevorzugten Plattform auf der linken Seite. Wir werden Sie durch die Schritte zum Schreiben einer einfachen Anwendung zum Abrufen von e-Mails, die mit dem Microsoft Graph leiten.

Wenn Ihre bevorzugte Plattform noch nicht aufgeführt ist, mit dem Fortfahren Sie lesen auf dieser Seite. Gehen wir über dieselben Schritte mithilfe von unformatierten HTTP-Anforderungen.

## <a name="getting-started-with-the-microsoft-graph-api-and-rest"></a>Erste Schritte mit dem Microsoft Graph-API und REST

Der Zweck dieses Handbuchs wird Schritt für Schritt durch den Prozess von der Microsoft Graph zum Abrufen von e-Mail-Nachrichten in Office 365 und Outlook.com aufrufen. Im Gegensatz zu den plattformspezifische Exemplarische Vorgehensweisen konzentriert sich auf die OAuth und REST-Anforderungen und Antworten in diesem Handbuch. Es wird die Abfolge der Anforderungen und Antworten, die eine app verwendet zum Authentifizieren und Abrufen von Nachrichten behandelt.

## <a name="using-oauth-20-to-authenticate"></a>Verwenden von OAuth 2.0 zum Authentifizieren

Um die Microsoft Graph aufrufen, benötigt Ihre app ein Zugriffstoken von Azure Active Directory (AD Azure). Im folgenden Beispiel implementiert die app den Ablauf Autorisierung Code erteilen, um das Zugriffstoken von Azure AD, folgende von [OAuth 2.0-Protokolle](http://tools.ietf.org/html/rfc6749)zu erhalten.

### <a name="registering-an-app"></a>Registrieren einer app

Derzeit gibt es zwei Optionen zum Registrieren der app:

  1. Registrieren einer app mithilfe des Objektmodells, die Office 365 kommerzielle Benutzer unterstützt, Arbeit oder Schule nur Konten.
 
  Dieses Modell funktioniert nur mit professionellen Office 365-Dienstangebote informieren. Sobald Sie Ihre app registriert haben, können Sie es über das [Azure-Verwaltungsportal](https://manage.windowsazure.com)verwalten.

  2. Registrieren Sie die neuesten Funktionalität verwenden, die funktioniert für Verbraucher und kommerziellen Office 365-Dienste (nennen wir Auth Endpunkt v2. 0).
 
  Für die Arbeit oder Schule und persönliche Konten ein einzigen Authentifizierungsdienst ist jetzt verfügbar. Dieses Modell bietet einen einzigen Authentifizierungsdienst für sowohl Arbeit und School (Azure AD) sowie persönliche (Microsoft) Identitäten. Nun müssen Sie nur eine authentifizierungsfluss in Ihrer app zum Aktivieren von Benutzern die Verwendung von Arbeit oder Schule Konten, wie Office 365 oder OneDrive für Unternehmen, oder persönliche Konten, wie Outlook.com oder OneDrive implementieren.
   
Verwenden der [Anwendung Registrierung Portal](https://apps.dev.microsoft.com/) zum Registrieren Ihrer app und Arbeit und Schule und persönliche Konten unterstützen.

Bitte beachten Sie, dass der v2. 0-Endpunkt wächst schrittweise alle Szenarios aus der vorherigen Auth Endpunkt abzudecken. Auswählen, ob das richtige für Sie [diesen Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/) lesen ist

Nach der Registrierung erhalten einer Client-ID und geheimen Schlüssel Sie. Diese Werte werden in der Autorisierung Code Grant Ablauf verwendet.

Der Rest dieses Dokuments wird davon ausgegangen eine Registrierung für das Modell v2. 0. Ein vollständiges Handbuch zur die Abläufe in der v2. 0-Endpunkt unterstützt finden Sie [in diesem Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-flows/), für ein vollständiges Handbuch zur Autorisierung Code Grant-Fluss [in diesem Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oauth-code/) finden Sie unter

### <a name="getting-an-authorization-code"></a>Abrufen eines Autorisierungscodes

Der erste Schritt bei der Autorisierung Code Grant-Ablauf besteht darin einen Autorisierungscode abzurufen. Dieser Code wird zur app vom autorisierungsserver zurückgegeben, wenn Benutzer meldet sich und auf die Zugriffsebene die app angefordert zustimmt.

Zunächst erstellt die app Anmelde-URL für den Benutzer. Diese URL muss in einem Browser geöffnet werden, damit der Benutzer anmelden und seine Zustimmung bereitstellen kann.

Die base-URL für die Anmeldung sieht wie `https://login.microsoftonline.com/common/oauth2/v2.0/authorize`.

Die app fügt Abfrageparametern auf dieser Basis-URL können Sie die Authentifizierungsserver wissen, welche app angeforderte Zugriffstyp der Anmeldung und was es fordert Berechtigungen.

- `client_id`-Die Client-ID, Registrieren der app beim generiert. Auf diese Weise können Azure AD wissen, welche app die Anmeldung aufgefordert wird.
- `redirect_uri`-Der Speicherort, auf den Azure einmal der Benutzer umleitet wurde Zustimmung der App gewährt. Dieser Wert muss der Wert der **URI umleiten** verwendet, wenn die app zu registrieren entsprechen.
- `response_type`-Die Art der Reaktion der app erwartet. Dieser Wert ist `code` für den Ablauf der Autorisierung Code erteilen.
- `scope`-Eine durch Leerzeichen getrennte Liste der Bereiche, die die app angefordert werden. Weitere Informationen in [diesem Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)
- `state`– Ein Wert enthalten, in der Anforderung, die auch in der token Antwort zurückgegeben wird.

Die URL der Anforderung für unsere Anwendung, die erfordert Lesezugriff auf den Mail würde beispielsweise folgendermaßen aussehen.

```http
GET https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=<CLIENT ID>&redirect_uri=http%3A%2F%2Flocalhost/myapp%2F&response_type=code&state=1234&scope=https%3A%2F%2Fgraph.microsoft.com%2Fmail.read
```

Im nächsten Schritt Umleiten des Benutzers an den Anmelde-URL ein. Dem Benutzer wird eine Anmeldeseite angezeigt werden, die den Namen der app angezeigt wird. Nachdem sie sich anmelden, wird der Benutzer die app ist erforderlich und aufgefordert werden, gewähren oder verweigern mit einer Liste der Berechtigungen angezeigt. Vorausgesetzt, dass sie den erforderlichen Zugriff ermöglichen, werden im Browser auf die Umleitung umgeleitet URI in die erste Anforderung mit den Autorisierungscode in der Abfragezeichenfolge angegeben.

```http
http://localhost/myapp/?code=AwABAAAA...cZZ6IgAA&state=1234
```

Wenn Sie auch OpenId Verbindung für einmaliges Anmelden verwenden, sind zusätzliche Parameter erforderlich, finden Sie unter [in diesem Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oidc/) finden Sie weitere Informationen. 

Im nächste Schritt wird zum Austauschen von des Autorisierungscode für ein Zugriffstoken zurückgegeben.

### <a name="getting-an-access-token"></a>Erste ein Zugriffstoken

Wenn ein Zugriffstoken erhalten möchten, sendet die app-Formular-codierten Parameter an den tokenanforderung-URL (`https://login.microsoftonline.com/common/oauth2/v2.0/token`) mit den folgenden Parametern.

- `client_id`: Die Client-ID registrieren der app beim generiert.
- `client_secret`: Den geheimen Clientschlüssel Registrieren der app beim generiert.
- `code`: Die Autorisierungscode aus dem vorherigen Schritt abgerufen.
- `redirect_uri`: Dieser Wert muss identisch mit der in der Anforderung Autorisierung des Codes verwendete Wert sein.
- `grant_type`: Der Typ des erteilen, die die app Transportmethode verwendet. Dieser Wert ist `code` für den Ablauf der Autorisierung Code erteilen.
- `scope`-Eine durch Leerzeichen getrennte Liste der Bereiche, die die app angefordert werden. Weitere Informationen in [diesem Artikel](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)

Die Anforderungs-URL für die Anwendung mit dem Code aus dem vorherigen Schritt, würde wie folgt aussehen.

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

Der Server antwortet mit einer JSON-Nutzlast, die Zugriffstoken enthält.

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

Das Zugriffstoken befindet sich der `access_token` der Nutzlast JSON-Feld. Die app verwendet den Wert den Authorization-Header fest, wenn der REST der API-aufrufen.

## <a name="calling-the-microsoft-graph"></a>Das Aufrufen der Microsoft Graph

Sobald die app ein Zugriffstoken verfügt, kann er, rufen Sie das Microsoft Graph. Da in diesem Beispiel-app Nachrichten abrufen ist, verwenden Sie eine HTTP GET-Anforderung an den `https://graph.microsoft.com/v1.0/me/messages` Endpunkt.

### <a name="refining-the-request"></a>Optimieren der Anforderung

Apps können das Verhalten des GET-Anfragen mithilfe von Abfrageparametern OData steuern.  Es wird empfohlen, dass apps diese Parameter verwenden, um die Anzahl der Ergebnisse zu begrenzen, die zurückgegeben werden und die Felder zu beschränken, die für jedes Element zurückgegeben werden. 

Unser Beispiel-app werden in einer Tabelle, die zeigt den Betreff, Absender, und das Datum und Zeit, die die Nachricht empfangen wurde, Fehlermeldungen angezeigt. Die Tabelle zeigt maximal 25 Zeilen und sortiert ist, sodass die zuletzt empfangene Nachricht am Anfang befindet. Die app verwendet die folgenden Abfrageparameter, um diese Ergebnisse zu erzielen.

- Die `$select` Parameter wird verwendet, um nur angeben, die `subject`, `sender`, und `dateTimeReceived` Felder.
- Die `$top` Parameter wird verwendet, um bis zu 25 Elemente anzugeben.
- Die `$orderby` Parameter dient zum Sortieren der Ergebnisse nach dem `dateTimeReceived` dar.

Dies führt die folgenden Anforderung.

```http
GET https://graph.microsoft.com/v1.0/me/messages?$select=subject,from,receivedDateTime&$top=25&$orderby=receivedDateTime%20DESC
Accept: application/json
Authorization: Bearer eyJ0eXAi...b66LoPVA
```

Nun, wie Sie Aufrufe an das Microsoft Graph haben, können Sie die API-Referenz erstellt eine beliebige andere Arten von Anrufen, die Ihre app muss, verwenden. Seien Sie jedoch sich, die Ihre app muss die entsprechenden Berechtigungen für die app-Registrierung für das Aufrufen von es durch konfiguriert haben.


