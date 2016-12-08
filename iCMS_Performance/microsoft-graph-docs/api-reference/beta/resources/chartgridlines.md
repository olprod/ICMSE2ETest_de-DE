# <a name="chartgridlines-resource-type"></a>Ressourcentyp ChartGridlines

Stellt Haupt- oder Hilfsgitternetzlinien auf einer Diagrammachse dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartGridlines](../api/chartgridlines_get.md) | [ChartGridlines](chartgridlines.md) |Lesen Sie Eigenschaften und Beziehungen ChartGridlines-Objekts.|
|[Update](../api/chartgridlines_update.md) | [ChartGridlines](chartgridlines.md)    |ChartGridlines-Objekt zu aktualisieren. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|visible|boolean|Boolescher Wert, wenn die Gitternetzlinien sichtbar sind.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartGridlinesFormat](chartgridlinesformat.md)|Stellt die Formatierung des Diagramm-Gitternetzlinien. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartGridLines"
}-->

```json
{
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartGridlines resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->