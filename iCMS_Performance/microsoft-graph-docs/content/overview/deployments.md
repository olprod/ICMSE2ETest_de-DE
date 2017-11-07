# <a name="sovereign-cloud-deployments"></a>Unabhängigen Cloud-Bereitstellungen


Dieser Artikel enthält Informationen über die verschiedenen unabhängigen Cloud Instanzen von Microsoft Graph und ihren Funktionen, die Entwickler zur Verfügung stehen. 


## <a name="microsoft-graph-operated-by-21vianet-in-china"></a>Microsoft Graph von 21Vianet in China betrieben

Dieser Abschnitt enthält Informationen zu Microsoft Graph handelt, das von 21Vianet und die Funktionen, die Entwickler zur Verfügung stehen.

### <a name="service-root-endpoints"></a>Stamm-Endpunkte
| Microsoft Graph handelt, das von 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://microsoftgraph.chinacloudapi.CN | https://Graph.Microsoft.com|

### <a name="microsoft-graph-explorer"></a>Microsoft Graph-Explorer
| Microsoft Graph handelt, das von 21Vianet | Microsoft Graph|
|---------------------------|----------------|
|https://graphexplorerchina.azurewebsites.NET| https://graphexplorer2.azurewebsites.NET|

### <a name="azure-openid-connect-and-oauth20"></a>Verbinden von Azure OpenID und OAuth2.0
Die Endpunkte verwendet, um das Token für die Anmeldung zu erwerben oder zum Aufrufen von Microsoft Graph handelt, das von 21Vianet unterscheiden sich von denen anderer Angebote. 

| Microsoft Graph handelt, das von 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://Login.chinacloudapi.CN | https://Login.microsoftonline.com|
 
Verwenden Sie https://login.chinacloudapi.cn/common/oauth2/authorize, um den Benutzer und https://login.chinacloudapi.cn/common/oauth2/token zum Erwerben eines Tokens für Ihre app zum Aufrufen von 21Vianet betrieben wird Microsoft Graph authentifizieren.

> **HINWEIS**: die neuesten [v2. 0 autorisieren und Endpunkte token](https://azure.microsoft.com/en-us/documentation/articles/active-directory-appmodel-v2-overview/) sind NICHT verfügbar für die Verwendung mit Microsoft Graph von 21Vianet betrieben wird.  Apps können nur Unternehmensdaten und nicht die Consumer-Daten zugreifen. 

### <a name="service-capabilities-offered-by-microsoft-graph-operated-by-21vianet"></a>Service-Funktionen von 21Vianet betrieben wird Microsoft Graph
Im Allgemeinen stehen die folgenden Features von Microsoft Graph (auf der `/v1.0` Endpunkt):

* Benutzer
* Gruppen
* Dateien
* E-Mails
* Kalender
* Persönliche Kontakte 
* Erstellen, lesen, update und delete-Operationen (CRUD)
* Cross-Origin Resource sharing (CORS) zu unterstützen.

Die folgenden Features von Microsoft Graph stehen ebenfalls zur Verfügung, in der Vorschau (klicken Sie auf die `/beta` Endpunkt):

* Organisatorische Kontakte
* Anwendungen
* Dienstprinzipale
* Directory-Erweiterungen
