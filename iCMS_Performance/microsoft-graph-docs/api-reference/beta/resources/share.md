# <a name="share-resource-type"></a>Freigeben von Ressourcentyp



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

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
|id|String| Schreibgeschützt.|
|name|String||
|Besitzer|[identitySet](identityset.md)||

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Items|[DriveItem](driveitem.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen der Freigabe](../api/share_get.md) | [Freigeben](share.md) |Lesen Sie Eigenschaften und Beziehungen des Freigabe-Objekts.|
|[Element erstellen](../api/share_post_items.md) |[driveItem](driveitem.md)| Erstellen Sie ein neues Element, indem Sie das Veröffentlichen in der Items-Auflistung.|
|[Listenelemente](../api/share_list_items.md) |[DriveItem](driveitem.md) -Auflistung| Rufen Sie eine Auflistung der Item-Objekts.|
|[Update](../api/share_update.md) | [Freigeben](share.md)   |Update-Freigabe-Objekts. |
|[Löschen](../api/share_delete.md) | Keine |Freigabe-Objekt zu löschen. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "share resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
