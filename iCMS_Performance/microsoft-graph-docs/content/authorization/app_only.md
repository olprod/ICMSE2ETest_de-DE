# <a name="call-microsoft-graph-in-a-service-or-daemon-app"></a>Aufrufen von Microsoft Graph in einer app-Dienst oder Filterdaemon

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden der einzelnen Mandanten Service oder Filterdaemon-app mit Office 365, und rufen Sie die Microsoft Graph-API.

## <a name="overview"></a>Übersicht

Wenn Sie die Microsoft Graph-API in einer app-Dienst oder Filterdaemon anrufen, müssen Sie die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory.
2. Fordern Sie ein Zugriffstoken aus dem Endpunkt Ausstellen von Token.
3. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API.

## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Sie benötigen, um [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com) verwalten zu gelangen.

Alternativ dazu finden Sie im Abschnitt [Registrieren Ihrer Anwendung Server mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Nachdem Sie die Anwendung registriert haben, konfigurieren Sie die **Berechtigungen** , die Ihre app Dienst oder Filterdaemon erforderlich sind.

Beachten Sie die folgenden Werte in der Seite zum Konfigurieren der Azure-Anwendung, da Sie diese Werte zum Konfigurieren des OAuth-Ablauf in Ihrer app-Dienst oder Filterdaemon benötigen.

* Client-ID (eindeutig für die Anwendung)
* Eine Anwendungsschlüssel (eindeutig für Ihre Anwendung)
* Ihre app OAuth 2.0 token Endpunkt
  * Suchen Sie nach dieser Wert durch Klicken auf die *Ansicht Endpunkten* am unteren Rand der Azure-Verwaltungsportal in Ihrer app-Seite. Der Endpunkt sieht wie folgt aus `https://login.microsoftonline.com/<tenantId>/oauth2/token`.

## <a name="request-an-access-token-from-the-token-issuing-endpoint"></a>Fordern Sie ein Zugriffstoken aus dem Endpunkt Ausstellen von token

Der Dienst oder Filterdaemon app kann im Gegensatz zu Client-apps haben einen Benutzer anmelden und die Anwendung zu autorisieren. In diesem Fall muss die Anwendung OAuth 2.0 Client Anmeldeinformationen Grant Flow implementieren, mit der sie eine eigene Anmeldeinformationen, die Client-ID und einen Anwendungsschlüssel verwenden, um beim Aufrufen der Microsoft Graph anstelle von Identitätswechsel bei einem Benutzer zu authentifizieren. Details zu den authentifizierungsfluss finden Sie unter [Dienst Service-Anrufe mithilfe von Clientanmeldeinformationen](https://msdn.microsoft.com/en-us/library/azure/dn645543.aspx) .

Stellen Sie eine HTTP POST-Anforderung an das Token ausstellen Endpunkt mit den folgenden Parametern, ersetzen `<clientId>` und `<clientSecret>` mit Ihrer app-Client-ID und die Anwendungsschlüssel, jeweils.

```http
POST https://login.microsoftonline.com/<tenantId>/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
&client_id=<clientId>
&client_secret=<clientSecret>
&resource=https://graph.microsoft.com
```

Die Antwort wird ein Token und Ablauf Zugriffsinformationen enthalten.

```json
{ 
  "token_type": "Bearer",
  "expires_in": "3599",
  "scope": "User.Read",
  "expires_on": "1449685363",
  "not_before": "1449681463",
  "resource": "https://graph.microsoft.com",
  "access_token": "<token>"
}
```

## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. Ihre app muss das Zugriffstoken an den **Authorization** -Header jeder Anforderung anfügen.

Eine app-Dienst oder Filterdaemon kann beispielsweise alle Benutzer in einem Mandanten abrufen, vollständige Profile für alle Benutzer mit der Berechtigung *Lesen* in der Azure-Verwaltungsportal ausgewählt hat. 

```http
GET https://graph.microsoft.com/v1.0/users
Authorization: Bearer <token>
```

Das Microsoft Graph ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden kann. Checken Sie die [API-Referenz](http://graph.microsoft.io/docs/api-reference/v1.0) zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.
