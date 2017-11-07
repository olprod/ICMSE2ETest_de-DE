# <a name="chartpoint-resource-type"></a>Ressourcentyp ChartPoint

Stellt einen Punkt einer Datenreihe in einem Diagramm dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartPoint](../api/chartpoint_get.md) | [ChartPoint](chartpoint.md) |Lesen Sie Eigenschaften und Beziehungen ChartPoint-Objekts.|
|[Liste](../api/chartpoint_list.md) | [ChartPoint](chartpoint.md) -Auflistung |Rufen Sie ChartPoint objektauflistung. |
|[Itemat](../api/chartpointscollection_itemat.md)|[ChartPoint](chartpoint.md)|Abrufen eines Punkts basierend auf ihre Position in der Datenreihe an.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|value|object|Gibt den Wert eines Diagramms Punkts zurück. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartPointFormat](chartpointformat.md)|Kapselt das Format Eigenschaften Datenpunkts. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartPoint"
}-->

```json
{
  "value": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartPoint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->