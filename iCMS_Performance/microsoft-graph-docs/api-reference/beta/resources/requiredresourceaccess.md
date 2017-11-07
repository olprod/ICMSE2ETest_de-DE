# <a name="requiredresourceaccess-resource-type"></a>Ressourcentyp requiredResourceAccess

Gibt den Satz von OAuth 2.0 berechtigungsbereiche und app-Rollen unter der angegebenen Ressource, der eine Anwendung Zugriff auf erforderlich ist. Die angegebene OAuth 2.0 berechtigungsbereiche möglicherweise angefordert werden-Clientanwendungen (über die **RequiredResourceAccess** -Auflistung) Wenn eine Anwendung Resource aufrufen. Die Eigenschaft **RequiredResourceAccess** der [Anwendung](application.md) Entität ist eine Auflistung von **ReqiredResourceAccess**.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.requiredResourceAccess"
}-->

```json
{
  "resourceAccess": [{"@odata.type": "microsoft.graph.resourceAccess"}],
  "resourceAppId": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|resourceAccess|[ResourceAccess](resourceaccess.md) -Auflistung|Die Liste der OAuth2.0 berechtigungsbereiche und app-Rollen, die die Anwendung aus der angegebenen Ressource benötigt.|
|resourceAppId|String|Der eindeutige Bezeichner für die Ressource, der die Anwendung Zugriff auf erforderlich ist.  Dies sollte der **AppId** für die Zielanwendung für die Ressource deklarierten gleich sein.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "requiredResourceAccess resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
