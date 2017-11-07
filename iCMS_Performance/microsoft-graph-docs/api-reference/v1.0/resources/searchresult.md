# <a name="searchresult-resource-type"></a>SearchResult Ressourcentyp

Die Ressource **SearchResult** gibt an, als ein Element, das die Antwort auf eine Suche ist.



## <a name="properties"></a>Eigenschaften

| Eigenschaft            | Typ   | Beschreibung                                                                                                                                                                         |
|:--------------------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| onClickTelemetryUrl | String | Eine Callback-URL, die zum Aufzeichnen von Telemetriedaten verwendet wird. Die Anwendung sollte einen GET auf diese URL senden, falls dieses Element, um die Qualität der Ergebnisse zu verbessern, dem der Benutzer interagiert. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
  "onClickTelemtryUrl"
  ],
  "@odata.type": "microsoft.graph.searchResult"
}-->

```json
{
  "onClickTelemetryUrl": "url"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "searchResult resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
