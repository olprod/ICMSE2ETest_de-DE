# <a name="responsestatus-resource-type"></a>ResponseStatus Ressourcentyp

Der Antwortstatus eine Besprechungsanfrage.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Antwort|String|Die Art der Antwort: None = 0, Organisator = 1, TentativelyAccepted = 2, akzeptierte = 3, abgelehnt = 4, NotResponded = 5. Possible values are: `None`, `Organizer`, `TentativelyAccepted`, `Accepted`, `Declined`, `NotResponded`.|
|Uhrzeit|DateTimeOffset|Datum und Uhrzeit, zu der die Antwort zurückgegeben wurde. Sie ISO 8601-Format verwendet und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.responseStatus"
}-->
```json
{
  "response": "String",
  "time": "String (timestamp)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "responseStatus resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
