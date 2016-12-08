# <a name="chartdatalabels-resource-type"></a>Ressourcentyp ChartDataLabels

Stellt eine Auflistung aller datenbeschriftungen an einem Diagramm Punkt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartDataLabels](../api/chartdatalabels_get.md) | [ChartDataLabels](chartdatalabels.md) |Lesen Sie Eigenschaften und Beziehungen des ChartDataLabels-Objekts.|
|[Update](../api/chartdatalabels_update.md) | [ChartDataLabels](chartdatalabels.md) |Aktualisieren Sie ChartDataLabels-Objekts. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|position|string|DataLabelPosition-Wert, der die Position der Datenbeschriftung darstellt. Possible values are: `None`, `Center`, `InsideEnd`, `InsideBase`, `OutsideEnd`, `Left`, `Right`, `Top`, `Bottom`, `BestFit`, `Callout`.|
|Separator|string|Eine Zeichenfolge, die das Trennzeichen für die datenbeschriftungen in einem Diagramm darstellt.|
|showBubbleSize|boolean|Boolean-Wert, der darstellt, wenn die Daten Blasengröße bezeichnen ist sichtbar oder nicht.|
|showCategoryName|boolean|Boolean-Wert, darstellt, wenn die Daten Kategoriename bezeichnen ist sichtbar oder nicht.|
|showLegendKey|boolean|Boolean-Wert, wenn die Daten, Legendensymbol bezeichnen darstellt ist sichtbar oder nicht.|
|showPercentage|boolean|Boolean-Wert zurück, wenn die Daten Prozentsatz bezeichnen darstellt ist sichtbar oder nicht.|
|showSeriesName|boolean|Boolean-Wert zurück, wenn die Daten Datenreihennamen bezeichnen darstellt ist sichtbar oder nicht.|
|showValue|boolean|Boolean-Wert zurück, wenn die Daten Wert beschriften darstellt ist sichtbar oder nicht.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartDataLabelFormat](chartdatalabelformat.md)|Stellt das Format des Diagramms klickt, das Füllung und die Formatierung der Schriftart enthält. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartDataLabels"
}-->

```json
{
  "position": "string",
  "separator": "string",
  "showBubbleSize": true,
  "showCategoryName": true,
  "showLegendKey": true,
  "showPercentage": true,
  "showSeriesName": true,
  "showValue": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartDataLabels resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->