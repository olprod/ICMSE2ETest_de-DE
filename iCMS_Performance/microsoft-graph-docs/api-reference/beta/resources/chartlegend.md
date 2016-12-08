# <a name="chartlegend-resource-type"></a>Ressourcentyp ChartLegend

Stellt die Legende in einem Diagramm dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartLegend](../api/chartlegend_get.md) | [ChartLegend](chartlegend.md) |Lesen Sie Eigenschaften und Beziehungen des ChartLegend-Objekts.|
|[Update](../api/chartlegend_update.md) | [ChartLegend](chartlegend.md) |ChartLegend-Objekt zu aktualisieren. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Overlay|boolean|Boolescher Wert für gibt an, ob die Legende mit den Hauptteil des Diagramms überlappt werden sollen.|
|Position|string|Die Position der Legende im Diagramm darstellt. Possible values are: `Top`, `Bottom`, `Left`, `Right`, `Corner`, `Custom`.|
|visible|boolean|Ein boolescher Wert, die Sichtbarkeit eines ChartLegend-Objekts darstellt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartLegendFormat](chartlegendformat.md)|Stellt die Formatierung einer Diagrammlegende an, die Füllung und die schriftartformatierung enthält. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartLegend"
}-->

```json
{
  "overlay": true,
  "position": "string",
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartLegend resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->