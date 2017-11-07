# <a name="itemattachment-resource-type"></a>Ressourcentyp itemAttachment

Ein Kontakt, Ereignis oder Nachricht, die an ein anderes Ereignis, Nachricht oder Post angefügt ist.  

[Anlage](attachment.md)abgeleitet.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von itemAttachment](../api/itemattachment_get.md) | [itemAttachment](itemattachment.md) |Lesen Sie Eigenschaften und Beziehungen des ItemAttachment-Objekts.|
|[Löschen](../api/attachment_delete.md) | Keine |ItemAttachment-Objekt zu löschen. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|contentType|String|Der Inhaltstyp der Anlage.|
|id|String| Die Anlage-ID|
|isInline|Boolean|Legen Sie auf "true" Wenn die Anlage Inline, beispielsweise ein eingebettetes Bild in den Textkörper des Elements ist.|
|lastModifiedDateTime|DateTimeOffset|Letzte Datum und die Uhrzeit, die das Attachment-Objekt geändert wurde.|
|name|String|Der Anzeigename der Anlage.|
|size|Int32|Die Größe der Anlage in Byte.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Element|[OutlookItem](outlookitem.md)|Die Anlage oder das Ereignis. Navigationseigenschaft.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "item"
  ],
  "@odata.type": "microsoft.graph.itemAttachment"
}-->

```json
{
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": 1024
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "itemAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
