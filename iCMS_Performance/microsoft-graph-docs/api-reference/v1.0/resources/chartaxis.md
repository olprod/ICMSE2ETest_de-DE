# <a name="chartaxis-resource-type"></a>Ressourcentyp ChartAxis

Stellt eine einzelne Achse in einem Diagramm dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartAxis](../api/chartaxis_get.md) | [ChartAxis](chartaxis.md) |Lesen Sie Eigenschaften und Beziehungen ChartAxis-Objekts.|
|[Update](../api/chartaxis_update.md) | [ChartAxis](chartaxis.md)   |ChartAxis-Objekt zu aktualisieren. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|majorUnit|object|Stellt das Intervall zwischen zwei Hauptteilstriche dar. Kann auf einen numerischen Wert oder eine leere Zeichenfolge festgelegt werden.  Der zurückgegebene Wert ist immer eine Zahl.|
|maximum|object|Stellt den Maximalwert für die Größenachse.  Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt sein.  Der zurückgegebene Wert ist immer eine Zahl.|
|minimum|object|Stellt den kleinsten Wert für die Größenachse. Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt werden.  Der zurückgegebene Wert ist immer eine Zahl.|
|minorUnit|object|Stellt das Intervall zwischen zwei Hilfsteilstriche dar. "Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt werden. Der zurückgegebene Wert ist immer eine Zahl.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartAxisFormat](chartaxisformat.md)|Stellt die Formatierung der ein Chart-Objekt, die Zeile und die schriftartformatierung enthält. Schreibgeschützt.|
|majorGridlines|[ChartGridlines](chartgridlines.md)|Gibt ein Gridlines-Objekt, das die Haupt-Gitternetzlinien für die angegebene Achse darstellt. Schreibgeschützt.|
|minorGridlines|[ChartGridlines](chartgridlines.md)|Gibt ein Gridlines-Objekt, das die Hilfsgitternetz-Linien der angegebenen Achse darstellt. Schreibgeschützt.|
|title|[ChartAxisTitle](chartaxistitle.md)|Stellt den Titel der Rubrikenachse. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartaxis"
}-->

```json
{
  "majorUnit": "string",
  "maximum": "string",
  "minimum": "string",
  "minorUnit": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartAxis resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->