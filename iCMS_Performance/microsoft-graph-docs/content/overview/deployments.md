# <a name="sovereign-cloud-deployments"></a>Sovereign cloud deployments


This article provides information about the different sovereign cloud instances of Microsoft Graph and their capabilities that are available to developers. 


## <a name="microsoft-graph-operated-by-21vianet-in-china"></a>Microsoft Graph operated by 21Vianet in China

This section provides information about Microsoft Graph operated by 21Vianet, and the capabilities that are available to developers.

### <a name="service-root-endpoints"></a>Service root endpoints
| Microsoft Graph operated by 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://microsoftgraph.chinacloudapi.cn | https://graph.microsoft.com|

### <a name="microsoft-graph-explorer"></a>Microsoft Graph Explorer
| Microsoft Graph operated by 21Vianet | Microsoft Graph|
|---------------------------|----------------|
|https://graphexplorerchina.azurewebsites.net| https://graphexplorer2.azurewebsites.net|

### <a name="azure-openid-connect-and-oauth20"></a>Azure OpenID Connect and OAuth2.0
The endpoints used to acquire tokens for sign-in or to call Microsoft Graph operated by 21Vianet differ from those of other offerings. 

| Microsoft Graph operated by 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://login.chinacloudapi.cn | https://login.microsoftonline.com|
 
Use https://login.chinacloudapi.cn/common/oauth2/authorize to authenticate the user and https://login.chinacloudapi.cn/common/oauth2/token to acquire a token for your app to call Microsoft Graph operated by 21Vianet.

> **NOTE**: The latest [v2.0 authorize and token endpoints](https://azure.microsoft.com/en-us/documentation/articles/active-directory-appmodel-v2-overview/) are NOT available for use with Microsoft Graph operated by 21Vianet.  Apps can only access organizational data and not consumer data. 

### <a name="service-capabilities-offered-by-microsoft-graph-operated-by-21vianet"></a>Service capabilities offered by Microsoft Graph operated by 21Vianet
Die folgenden Microsoft Graph-API-Features sind allgemein verfügbar:

* Benutzer
* Gruppen
* Dateien
* E-Mails
* Kalender
* Persönliche Kontakte 
* CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen)
* CORS-Unterstützung (Cross-Origin Resource Sharing)

The following Microsoft Graph features are also available in preview (on the `/beta` endpoint):

* Organisationskontakte
* Anwendungen
* Dienstprinzipale
* Verzeichnisschemaerweiterungen
