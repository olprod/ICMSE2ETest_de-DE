# <a name="recurrencerange-resource-type"></a>Ressourcentyp recurrenceRange

Die Dauer eines Ereignisses.

## <a name="properties"></a>Eigenschaften

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|endDate|Date|Das Enddatum der Datenreihe.|
|numberOfOccurrences|Int32|Wie oft das Ereignis wiederholt werden sollen.|
|recurrenceTimeZone|String |Die Zeitzone für die **StartDate** und **EndDate** -Eigenschaften. |
|startDate|Date|Das Startdatum der Datenreihe.|
|Typ|String|Den Serienbereich: EndDate = 0, NoEnd = 1, Nummerierung = 2. Mögliche Werte sind: `EndDate`, `NoEnd`, `Numbered`.||


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.recurrencerange"
}-->

```json
{
  "endDate": "String (timestamp)",
  "numberOfOccurrences": 1024,
  "recurrenceTimeZone": "string",
  "startDate": "String (timestamp)",
  "type": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "recurrenceRange resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
