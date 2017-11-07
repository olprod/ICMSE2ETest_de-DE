# <a name="resourceaccess-resource-type"></a>Ressourcentyp resourceAccess

Gibt ein Berechtigungsbereich OAuth 2.0 oder eine app-Rolle, die eine Anwendung funktioniert. Die **ResourceAccess** -Eigenschaft des Typs [RequiredResourceAccess](requiredResourceAccess.md) ist eine Auflistung von **ResourceAccess**.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.resourceAccess"
}-->

```json
{
  "id": "guid",
  "type": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|Guid|Der eindeutige Bezeichner für eine der [oAuth2Permission](oauth2permission.md) oder [AppRole](approle.md) -Instanzen, die die Anwendung für die Ressource verfügbar macht.|
|Typ|String|Gibt an, ob die **Id** -Eigenschaft eines [oAuth2Permission](oauth2permission.md) oder einer [AppRole](approle.md)verweist. Mögliche Werte sind "Bereich" oder "Rolle".|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "resourceAccess resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
