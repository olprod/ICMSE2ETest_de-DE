# <a name="sharepointids-resource-type"></a>Ressourcentyp SharePointIds

Die Ressource **SharepointIds** gruppiert die verschiedenen Bezeichner für ein Element in einer SharePoint-Website oder OneDrive for Business in einer einzelnen Struktur gespeichert.

### <a name="properties"></a>Eigenschaften

| Eigenschaft          | Typ    | Beschreibung                                                          |
|:------------------|:--------|:---------------------------------------------------------------------|
| listId            | string  | Der eindeutige Bezeichner für das Element Liste in SharePoint.                          |
| listItemId        | string  | Ein Integer-Bezeichner für das Element innerhalb der Liste.                    |
| listItemUniqueId  | string  | Der eindeutige Bezeichner für das Element innerhalb von OneDrive für Busienss oder einer SharePoint-Website. |
| Website-ID            | string  | Der eindeutige Bezeichner für das Element-Websitesammlung. |
| Web-ID             | string  | Der eindeutige Bezeichner für das Element Website.                          |

### <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sharepointIds"
}-->
```json
{
    "listId": "string",
    "listItemId": "string",
    "listItemUniqueId": "string",
    "siteId": "string",
    "webId": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharepointIds resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->