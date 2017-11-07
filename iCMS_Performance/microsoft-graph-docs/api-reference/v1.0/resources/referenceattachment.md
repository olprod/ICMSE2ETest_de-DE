# <a name="referenceattachment-resource-type"></a>Ressourcentyp referenceAttachment

Ein Link zu einer Datei (beispielsweise eine Textdatei oder Word-Dokument) auf eine OneDrive for Business Cloud Laufwerk oder andere unterstützt Speicherorte, ein Ereignis, eine Nachricht oder ein Beitrag zugeordnet ist.

[Anlage](attachment.md)abgeleitet.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von referenceAttachment](../api/referenceattachment_get.md) | [referenceAttachment](referenceattachment.md) |Lesen Sie Eigenschaften und Beziehungen des ReferenceAttachment-Objekts.|
|[Löschen](../api/attachment_delete.md) | Keine |ReferenceAttachment-Objekt zu löschen. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|contentType|String|Der Inhaltstyp der Anlage.|
|id|String|Die Anlage-ID  Schreibgeschützt.|
|isInline|Boolean|Legen Sie auf "true" Wenn die Anlage Inline im Textkörper der das Einbetten von-Objekt angezeigt wird.|
|lastModifiedDateTime|DateTimeOffset|Datum und Uhrzeit der letzten die Anlage Änderung. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|name|String|Der Text, der unterhalb des Symbols, das die eingebettete Anlage darstellt angezeigt wird. Dies muss nicht der tatsächliche Dateiname sein.|
|size|Int32|Die Größe der Anlage in Byte.|


## <a name="relationships"></a>Beziehungen
Keine



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.referenceAttachment"
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
  "description": "referenceAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
