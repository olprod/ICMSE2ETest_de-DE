# <a name="fileattachment-resource-type"></a>Ressourcentyp fileAttachment

Eine Datei (beispielsweise eine Textdatei oder Word-Dokument), ein Ereignis, Nachrichten- oder Bereitstellungsnotiz zugeordnet ist. Die **ContentBytes** -Eigenschaft enthält den base64-codierten Inhalt der Datei.  

Wenn eine Dateianlage zu erstellen, berücksichtigen Sie Folgendes im Textkörper Anforderung:
* `"@odata.type": "#microsoft.graph.fileAttachment"`
* Die erforderlichen Eigenschaften **Name** und **ContentBytes**.

[Anlage](attachment.md)abgeleitet.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von fileAttachment](../api/fileattachment_get.md) | [fileAttachment](fileattachment.md) |Lesen Sie Eigenschaften und Beziehungen des FileAttachment-Objekts.|
|[Löschen](../api/attachment_delete.md) | Keine |FileAttachment-Objekt zu löschen. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|contentBytes|Binary|Der binäre Inhalt der Datei.|
|contentId|String|Die ID der Anlage im Exchange-Speicher.|
|contentLocation|String|Der URI Uniform Resource Identifier (), der den Speicherort des Inhalts der Anlage entspricht.|
|contentType|String|Der Inhaltstyp der Anlage.|
|id|String|Die Anlage-ID|
|isInline|Boolean|True, wenn dies eine Inlineanlage ist festgelegt.|
|lastModifiedDateTime|DateTimeOffset|Datum und Uhrzeit der letzten die Anlage Änderung.|
|name|String|Der Name, den unterhalb des Symbols, das die eingebettete Anlage darstellt angezeigte Text darstellt. Dies muss nicht der tatsächliche Dateiname sein.|
|size|Int32|Die Größe der Anlage in Byte.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.fileAttachment"
}-->

```json
{
  "contentBytes": "binary",
  "contentId": "string",
  "contentLocation": "string",
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
  "description": "fileAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
