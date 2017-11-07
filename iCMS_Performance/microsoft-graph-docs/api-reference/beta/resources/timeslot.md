# <a name="timeslot-resource-type"></a>Zeitrahmen Ressourcentyp

Ein Zeitraum.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.timeSlot"
}-->

```json
{
  "end": {"@odata.type": "microsoft.graph.timeStamp"},
  "start": {"@odata.type": "microsoft.graph.timeStamp"}
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Ende|[Zeitstempel](timestamp.md)|Die eine Frist beginnt.|
|Start|[Zeitstempel](timestamp.md)|Den Zeitpunkt der Zeitraum beendet wird.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "timeSlot resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->