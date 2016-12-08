# <a name="attachment-resource-type"></a>Anlage Ressourcentyp

Eine Datei, Element (Kontakt, Ereignis oder einer Nachricht) oder Verknüpfung mit einer Datei, die ein [Ereignis](../resources/event.md), eine [Nachricht](../resources/message.md)oder [Buchen](../resources/post.md)zugeordnet ist. Die Angabe zu  
entsprechende [FileAttachment](../resources/fileattachment.md) [ItemAttachment](../resources/itemattachment.md)und [ReferenceAttachment](../resources/referenceattachment.md) Ressourcen werden alle von der **Anlage** Ressource abgeleitet.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Anlagen abrufen](../api/attachment_get.md) | [Anlage](attachment.md) |Lesen Sie Eigenschaften und Beziehungen zwischen Attachment-Objekt.|
|[Hinzufügen eines Ereignisses des Attachment-Objekts](../api/event_post_attachments.md) | [Anlage](attachment.md) |Hinzufügen einer Datei, Element oder die Anlage auf ein Ereignis verknüpft.|
|[Hinzufügen einer Anlage](../api/message_post_attachments.md) | [Anlage](attachment.md) |Hinzufügen einer Datei, Element oder die Anlage an eine Nachricht verknüpft.|
|[Hinzufügen einer Nachricht in einer Anlage](../api/post_post_attachments.md) | [Anlage](attachment.md) |Hinzufügen einer Datei, item oder Verknüpfen einer Nachricht in einer Anlage.|
|[Liste der Anlagen eines Ereignisses](../api/event_list_attachments.md) | [Anlage](attachment.md) -Auflistung | Abrufen einer Liste von Anlagen für ein Ereignis. |
|[Anlagen Auflisten einer Nachricht](../api/message_list_attachments.md) | [Anlage](attachment.md) -Auflistung | Abrufen einer Liste von Anlagen für eine Nachricht an. |
|[Anlagen Auflisten einer Bereitstellung](../api/post_list_attachments.md) | [Anlage](attachment.md) -Auflistung | Abrufen einer Liste von Anlagen für einen Beitrag. |
|[Löschen](../api/attachment_delete.md) | Keine |Attachment-Objekt zu löschen. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|contentType|String|Den MIME-Typ.|
|id|String| Schreibgeschützt.|
|isInline|Boolean|`true`Wenn die Anlage eine Inlineanlage ist. andernfalls `false`.|
|lastModifiedDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|name|String|Dateiname der Anlage.|
|size|Int32|Die Länge der Anlage in Byte.|

## <a name="relationships"></a>Beziehungen
Keine

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.attachment"
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
  "description": "attachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
