# <a name="externalreference-resource-type"></a>Ressourcentyp externalReference

Die Ressource ExternalReference stellt die Metadaten eines Verweises (Anlagen wie etwa Datei URL). Es ist der Wert der Eigenschaft-Wert-Paaren in der [ExternalReferenceCollection](externalreferencecollection.md).

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.externalReference"
}-->

```json
{
  "alias": "string",
  "lastModifiedBy": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "previewPriority": "string",
  "type": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Alias|String| Ein Alias Name um den Verweis zu beschreiben. |
|lastModifiedBy|String| Schreibgeschützt. Benutzer-Id mit dem dies geändert wird. |
|lastModifiedDateTime|DateTimeOffset| Schreibgeschützt. Datum und Uhrzeit, an dem dieses geändert wird. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|previewPriority|String| Zum Festlegen der Reihenfolge der relativen Priorität in der der Verweis angezeigt werden sollen, als Vorschau für den Vorgang verwendet. |
|Typ|String| Verwendet, um den Typ des Verweises zu beschreiben. Zählen: `PowerPoint`, `Word`, `Excel`, `Other`.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "externalReference resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->