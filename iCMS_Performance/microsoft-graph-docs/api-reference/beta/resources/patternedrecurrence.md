# <a name="patternedrecurrence-resource-type"></a>Ressourcentyp patternedRecurrence

Das Serienmuster und Bereich.

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Muster|[RecurrencePattern](recurrencepattern.md)|Die Häufigkeit eines Ereignisses.|
|Bereich|[RecurrenceRange](recurrencerange.md)|Die Dauer eines Ereignisses.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.patternedrecurrence"
}-->

```json
{
  "pattern": {"@odata.type": "microsoft.graph.recurrencePattern"},
  "range": {"@odata.type": "microsoft.graph.recurrenceRange"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "patternedRecurrence resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->