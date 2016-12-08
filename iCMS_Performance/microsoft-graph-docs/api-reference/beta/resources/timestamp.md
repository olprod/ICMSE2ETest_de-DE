# <a name="timestamp-resource-type"></a>Zeitstempel Ressourcentyp

Datum und Uhrzeit, Informationen für einen Punkt in Zeit.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.timeStamp"
}-->

```json
{
  "date": "String (timestamp)",
  "time": "String (timestamp)",
  "timeZone": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|date|Date|Das der Zeitstempel Datumsteil.|
|Uhrzeit|TimeOfDay|Den Zeitbereich des der Zeitstempel.|
|Zeitzone|String|Timezone Teil der Zeitstempel, der einen der 24 Länge Bereiche in der ganzen Welt ist.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "timeStamp resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->