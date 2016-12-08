# <a name="chartseries-resource-type"></a>Ressourcentyp ChartSeries

Stellt eine Datenreihe in einem Diagramm dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartSeries](../api/chartseries_get.md) | [ChartSeries](chartseries.md) |Lesen Sie Eigenschaften und Beziehungen ChartSeries-Objekts.|
|[Erstellen von ChartPoints](../api/chartseries_post_points.md) |[ChartPoints](chartpoint.md)| Erstellen Sie eine neue ChartPoints, durch die Veröffentlichung auf der Points-Auflistung.|
|[Liste Punkt](../api/chartseries_list_points.md) |[ChartPoints](chartpoint.md) -Auflistung| Rufen Sie eine Auflistung der ChartPoints-Objekts.|
|[Update](../api/chartseries_update.md) | [ChartSeries](chartseries.md) |Aktualisieren Sie ChartSeries-Objekts. |
|[Liste](../api/chartseries_list.md) | [ChartSeries](chartseries.md) -Auflistung |Rufen Sie ChartSeries Auflistung-Objekts. |
|[Itemat](../api/chartseriescollection_itemat.md)|[ChartSeries](chartseries.md)|Ruft eine Reihe basierend auf seine Position in der Auflistung|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|name|string|Stellt den Namen einer Reihe in einem Diagramm dar.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartSeriesFormat](chartseriesformat.md)|Stellt die Formatierung von einer Diagrammdatenreihe dar, die Füllung und die Formatierung der Zeile enthält. Schreibgeschützt.|
|Punkte|[ChartPoints](chartpoint.md) -Auflistung|Stellt eine Auflistung aller Punkte in der Datenreihe. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartSeries"
}-->

```json
{
  "name": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartSeries resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->