
# <a name="microsoft-graph-app-authorization"></a>Microsoft Graph-app-Autorisierung


In diesem Artikel wird erläutert, wie Authentifizieren eines Benutzers, ein Zugriffstoken abzurufen und ein Zugriffstoken verwenden ein Aktualisierungstoken erneuern.
Der authentifizierungsfluss kann zwei grundlegende Schritte aufgeteilt werden:

1. Anfordern eines Autorisierungscodes
2. Verwenden Sie Autorisierungscode anfordern ein Zugriffstoken und Token zu aktualisieren. 

>  **Hinweis**: Sie können die Aktualisierungstoken verwenden, um ein neues Zugriffstoken erwerben, wenn das aktuelle Zugriffstoken läuft ab.

<!--To call the Microsoft Graph API, you have to complete the following tasks.

1. Register the application in Azure Active Directory
2. Authenticate a user and get an access token by calling methods on the Azure AD Authentication Library (ADAL)
3. Use ADAL to get an access token
4. Use the access token in a request to the Microsoft Graph API
5. Disconnect the session

In this article:

- [Authenticate a user and get app authorized](#msg_get_app_authorized)
- [Acquire access token](#msg_get_app_authenticated)
- [Renew access token using refresh token](#msg_renew_access_token)

 <a name="msg_get_app_authorized"> </a> -->
 
###<a name="authenticate-a-user-and-get-app-authorized"></a>Authentifizieren eines Benutzers und erste app autorisiert
Wenn Ihre app autorisiert erhalten möchten, müssen Sie den Benutzer zuerst authentifiziert abrufen. Zu diesem Zweck die Umleitung an den Endpunkt des Azure Active Directory (AD Azure)-Autorisierung, zusammen mit Ihrer app-Informationen zur Anmeldung bei ihrem Office 365-Konto des Benutzers. Nachdem der Benutzer angemeldet ist, und bewilligen Hiermit die Berechtigungen von Ihrer app angefordert (wenn der Benutzer nicht bereits geschehen ist), erhält Ihre app einen Autorisierungscode erforderlich, um ein OAuth-Zugriffstoken zu erwerben.

> **Hinweis**: Sie können hierzu durch Aufrufen von Methoden für die [Azure AD Authentication-Bibliothek (ADAL)](https://msdn.microsoft.com/en-us/library/azure/jj573266.aspx). Weitere Informationen zu autorisierungsflusses finden Sie unter [Authorization Codefluss erteilen](https://msdn.microsoft.com/en-us/library/azure/dn645542.aspx).

Autorisieren einer app beginnt mit senden eine HTTPS GET-Anforderung mithilfe der folgenden URL:
 
```GET https://login.microsoftonline.com/common/oauth2/authorize?response_type=code&redirect_uri=<uri>&client_id=<id>```

**Erforderliche Abfragezeichenfolgen-Parameter**

| Parametername  | Wert  | Beschreibung                                                                                            |
|:----------------|:-------|:-------------------------------------------------------------------------------------------------------|
| *client_id*     | string | Die Client-ID erstellt, die für Ihre app. Dies ist Ihre app- **CLIENT-ID** -Wert in Azure-Mandanten der Anwendungsregistrierungsdienst festgelegt.                                                                  |
| *response_type* | string | Gibt die Art der angeforderten Antwort an. In einer Anforderung Autorisierung des Codes Grant muss der Wert Code entsprechen. |
| *redirect_uri*  | string | Die umleitungs-URL, die der Browser gesendet wird, wenn die Authentifizierung abgeschlossen ist.  Dieser Wert muss die app vorkonfigurierten **ANTWORT-URL** -Wert übereinstimmen.                        |
 


Im folgenden finden ein Beispiel für eine solche Anforderung gemäß der Implementierung in einer aktiven Anwendung:


```GET https://login.microsoftonline.com/common/oauth2/authorize?response_type=code&redirect_uri=http%3a%2f%2flocalhost:1339/auth/azureoauth/callback&client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940``` 

Diese Anforderung gibt eine `200 OK` Antwort und stellt die Azure AD-Konto Anmeldeseite. 

Nachdem der Benutzer bei sich über gültige Anmeldeinformationen und Berechtigungen für die app sendet die Anmeldeseite bewilligen Hiermit eine `POST` Anforderung in Azure. Wenn die Anforderung erfolgreich ist, Azure antwortet mit einer `302 Found` Nachricht zum Weiterleiten des Anrufs an der app umleitungs-URI für die app erforderliche Zugriffstoken empfangen. Die weitergeleitete URI in der Antwort angegeben `Location` Kopfzeile, entspricht der app-ANTWORT-URL mit zwei Abfrageparameter verwendet `code=...` und `session_state=...` angehängt wird. Das folgende Beispiel zeigt einen Auszug aus einer solchen Antwort: 

```no-highlight 
HTTP/1.1 302 Found
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: text/html; charset=utf-8
Expires: -1
Location: http://localhost:1339/auth/azureoauth/callback?code=AAABAAAAvPM...&session_state=a9556cd3-cae6-4bc9-bf51-672f7b79b7c6
Server: Microsoft-IIS/8.5
P3P: CP="DSP CUR OTPi IND OTRi ONL FIN"

..... 
```

In diesem Beispiel wird der app-ANTWORT-URL ist `http://localhost:1339/auth/azureoauth/callback`. Bei der Verarbeitung dieser Antwort, extrahieren Sie die `code` Parameter Wert herunter, und für die anfängliche OAuth 2.0 Zugriff zu erwerben und Aktualisierung von Token (siehe nächsten Abschnitt).

> Das `302 Found` Antwort oben unterscheidet sich von der `302 Found` Antwort Sie erhalten, falls Sie anhand den Anmeldevorgang gestartet die `https://login.windows.net/<tenantId>/oauth2/authorize?...` URL. Im letzteren Fall die `302 Found` Antwort leitet die Anforderung an `login.microsoftonline.com`.
 
<!---<a name="msg_get_app_authenticated"> </a> -->

###<a name="acquire-an-access-token"></a>Ein Zugriffstoken erwerben
Um Microsoft Graph-API-Ressourcen zugreifen zu können, muss Ihre app eine gültige OAuth 2.0-Zugriffstoken jede HTTP-Anforderung enthalten. Sie können das Zugriffstoken verwenden die folgenden POST-Anforderung erhalten:

```no-highlight 
POST https://login.microsoftonline.com/common/oauth2/token HTTP/1.1
content-type : application/x-www-form-urlencoded
content-length : 144
```
 
Diese Anforderung erfordert eine URL-codierte Nutzlast mit der folgenden Syntax:
 
```no-highlight 
grant_type=authorization_code
&redirect_uri=<uri>
&client_id=<id>
&client_secret=<secret_key>
&code=<code>
&resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

**Erforderliche Abfragezeichenfolgen-Parameter**

| Parametername  | Wert  | Beschreibung                                                                                            |
|:----------------|:-------|:-------------------------------------------------------------------------------------------------------|
| *client_id*     | string | Die Client-ID für Ihre app erstellt haben.  |
| *client_secret*  | string | Der Schlüssel für Ihre app erstellt haben. Dieser Wert ist, den gleichen Wert im Abschnitt **Schlüssel** der app-Konfigurationsseite auf dem Azure-Verwaltungsportal|
| *redirect_uri*  | string | Die umleitungs-URL, die der Browser gesendet wird, wenn die Authentifizierung abgeschlossen ist.  |
| *Code*  | string | Den Autorisierungscode an. Die `code` Abfragen der Wert des Parameters aus der Antwort auf die Anforderung Autorisierung zurückgegeben. |
| *Ressource*   | string | Die Ressource, den, die Sie zugreifen möchten. Legen Sie zum Aufrufen der Microsoft Graph-API in diesem Parameterwert auf "https://graph.microsoft.com/".|

Der folgende Codeausschnitt zeigt ein Beispiel für die Anforderungsnutzlast verwendet, um die anfänglichen OAuth 2.0 Zugriff erhalten token:

```no-highlight  
grant_type=authorization_code&
redirect_uri=http%3A%2F%2Flocalhost%3A1339%2Fauth%2Fazureoauth%2Fcallback&
client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940&client_secret=PJW3dznGfyNSm3rM9aHeXWGKsTMepKXT1Eqy45XXdU4%3D&
code=AAABAAAAvPM1KaPlrEqdFSBzjqfTGBLRVQc6BtQmJ_9DQZUg8Tb7TJgTmbTE7AHM93qB5EKc4Bf-bOgzt3mebAywK-09X1uBHwOluuqSWfd9LU2HHgZtxcZFIYI5UL7L1UEvhrJRvX2iHhfz9ZSRMZMVL55n_K79gCOxtSATeCUw52zPk5ZaQ87Y42SCLsRZN4Y_zddhD3mMpkObiHVT8HzfhBUiT0oX0e-Q439vkbZoKiq1HaqMR3IPHiCXDbPPH5u7a4NTe5xAhh-o2MUIe6s4Xqql86sv1-IwyroOJJMueGUarkfbgwqmYL9Tm-jWab8o-BAK_plVsN73GU8cXO8ts30wa2YmNR5ZxSkw8oiB4mSZwGzGQlch55DRnucDs0SZBgj5etGi3SeXv5jhKlDU2S0bAPnGxF3QAH0N_zBpfakETVlcsHKi714u-tn9da6aTPQsE0IYKTAYgxjTMei6zfRFvCZi-tKdFR6X9TvvmF2iPdGQGWKeLw8CMWUzU8VmOhiHc0aBKG6RaXAOTM067J_9WKYPxMopcytD2z8HVkL1QhggAA&
resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

Wenn diese Anforderung erfolgreich ist, wird eine `200 OK` Antwort zurückgegeben wird. Ein Beispiel ist wie folgt:

```no-highlight  
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 2978
Access-Control-Allow-Origin: *

{
    "token_type":"Bearer",
    "expires_in":"3599",
    "expires_on":"1426551729",
    "not_before":"1426547829",
    "resource":"https://graph.microsoft.com/",
    "access_token":"eyJ0eXAiOiJKV1QiLCJhb...",
    "refresh_token":"AAABAAAAvPM1KaPlrEqd...",
    "scope": "Calendar.ReadWrite Directory.Read.All Files.ReadWrite Group.ReadWrite.All Mail.ReadWrite Mail.Send User.ReadBasic.All",
    "id_token":"eyJ0eXAiOiJKV1QiLCJhbGci..."
}
```

 
Der Antworttext ist eine JSON-formatierte Zeichenfolge, enthält das Zugriffstoken (`access_token`). Sie müssen dieses Token an alle nachfolgenden HTTP-Anforderungen auf Microsoft Graph-API-Ressourcen zugreifen angeben. 

Die `scope` -Eigenschaftswert sollte die Berechtigungen für die app während der Registrierung der app entspricht.

Bleibt das Zugriffstoken innerhalb des angegebenen Zeitintervalls gültig (`3599` im obigen Beispiel) Sekunden (oder 1 Stunde) ab dem Zeitpunkt der Veröffentlichungslizenz, als gemäß der `expires_in` Eigenschaft. Das Ergebnis enthält auch ein Aktualisierungstoken (`refresh_token`), die ein Zugriffstoken ablaufende oder abgelaufene erneuern verwendet werden muss. 

In der Produktionscode muss Ihre app sehen Sie sich für den Ablauf der diese Token und erneuern ablaufende Zugriffstoken vor Ablauf der Aktualisierungstoken. 


<!---<a name="msg_renew_access_token using refresh token"> </a> -->

###<a name="renew-expiring-access-token-using-refresh-token"></a>Erneuern Sie ablaufende Zugriffstoken Aktualisierungstoken verwenden
Um abgelaufene Zugriffstoken zu aktualisieren, verwenden Sie eine POST-Anforderung ähnlich dem folgenden Beispiel (vorausgesetzt, dass der Aktualisierungstoken nicht abgelaufen):

```no-highlight  
POST https://login.microsoftonline.com/common/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 897


grant_type=refresh_token
&redirect_uri=http%3A%2F%2Flocalhost%3A1339%2Fauth%2Fazureoauth%2Fcallback
&client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940
&client_secret=PJW3dznGfyNSm3rM9aHeXWGKsTMepKXT1Eqy45XXdU4%3D
&refresh_token=AAABAAAAvPM1KaPlrEqdFSBzjqfTGM74--...
&resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

**Erforderliche Abfragezeichenfolgen-Parameter**

| Parametername  | Wert  | Beschreibung                                                                                                                                         |
|:----------------|:-------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| *client_id*     | string | Die Client-ID für die Anwendung erstellt.  |
| *redirect_uri*  | string | Die umleitungs-URL, die der Browser gesendet wird, wenn die Authentifizierung abgeschlossen ist. Dies sollte den *Redirect_uri* -Wert, der in die erste Anforderung übereinstimmen. |
| *client_secret* | string | Einer der Schlüssel-Werte für Ihre Anwendung erstellt.                                                                                                     |
| *refresh_token* | string | Der Aktualisierungstoken, die Sie zuvor erhalten haben.    |
| *Ressource*      | string | Die Ressource, den, die Sie zugreifen möchten.|

Hinweis: Diese Anforderung auf die ursprünglichen token Erwerb Anforderung fast identisch ist. Sind zwei Unterschiede in der Anforderungsnutzlast, nämlich die `grant_type` Parameter enthält nun den Wert der `refresh_token` (anstelle von `code`).
 
Die erfolgreiche Antwort gibt Nutzlast ein JSON-Zeichenfolge zurück, die ähnlich wie die folgende Ausgabe:

```no-highlight 
{
    "token_type":"Bearer",
    "expires_in":"3600",
    "expires_on":"1426561346",
    "not_before":"1426557446",
    "resource":"https://graph.microsoft.com/",
    "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOi...", 
    "refresh_token":"AAABAAAAvPM1KaPlrEqdFSBzj...",
   "scope":"Graph.Read",
    "pwd_exp":"6553342",
    "pwd_url":"https://portal.microsoftonline.com/ChangePassword.aspx"
}
```
 
Als die fehlende `id_token` -Eigenschaft; diese Antworttext hat, die identische Syntax und Semantik wie die der ersten Token Erwerb Antwort. Die Zeiten Lebensdauer des neu zurückgegebenen `access_token` und `refresh_token` Werte erweitert werden. Die neue Ablaufzeit für das Zugriffstoken ist die Anzahl der Sekunden, die gemäß der `expires_in` Wert, von dem Zeitpunkt, wann die Anforderung Token aktualisieren erfolgreich übermittelt wurde. 
 
Nach Ablauf der Aktualisierungstoken kann keine abgelaufenen Zugriffstoken der soeben beschriebenen POST-Anforderung mit erneuert werden. Stattdessen müssen Sie die [app-Autorisierung und Authentifizierung](#msg_get_app_authorized) neu starten.


<!--##Additional Resources##

- [Hands on lab: Deep dive into the Office 365 unified API](http://dev.office.com/hands-on-labs/4585)  -->

