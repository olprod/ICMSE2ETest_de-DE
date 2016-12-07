# <a name="share-resource-type"></a>share resource type



## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "items"
  ],
  "@odata.type": "microsoft.graph.share"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string",
  "owner": {"@odata.type": "microsoft.graph.identitySet"}
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| ReadOnly|
|name|String||
|Besitzer|[identitySet](identityset.md)||

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Items|[driveItem](driveitem.md) collection| Read-only. Nullable.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get share](../api/share_get.md) | [share](share.md) |Read properties and relationships of share object.|
|[Erstellen eines Listenelements](../api/share_post_items.md) |[driveItem](driveitem.md)| Create a new item by posting to the items collection.|
|[List items](../api/share_list_items.md) |[driveItem](driveitem.md) collection| Get a item object collection.|
|[Update](../api/share_update.md) | [share](share.md)   |Update share object. |
|[delete()](../api/share_delete.md) | Keine |Delete share object. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "share resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
