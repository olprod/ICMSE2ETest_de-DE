# <a name="chart-resource-type"></a>Diagramm Ressourcentyp

Stellt ein Chart-Objekt in einer Arbeitsmappe dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Chart abrufen](../api/chart_get.md) | [Diagramm](chart.md) |Eigenschaften lesen und Beziehungen des Chart-Objekt.|
|[Erstellen von ChartSeries](../api/chart_post_series.md) |[ChartSeries](chartseries.md)| Erstellen Sie eine neue ChartSeries, durch die Veröffentlichung auf der Series-Auflistung.|
|[Liste Datenreihe](../api/chart_list_series.md) |[ChartSeries](chartseries.md) -Auflistung| Rufen Sie eine Auflistung der ChartSeries-Objekts.|
|[Update](../api/chart_update.md) | [Diagramm](chart.md)   |Chart-Objekt zu aktualisieren. |
|[Bild](../api/chart_image.md)|Bild base64-codierte Zeichenfolge|Rendert das Diagramm als Bild base64-codierten Skalierung des Diagramms an die angegebenen Maße angepasst.|
|[Löschen](../api/chart_delete.md)|Keine|Löscht das Chart-Objekt.|
|[SetData](../api/chart_setdata.md)|Keine|Setzt die Quelldaten für das Diagramm zurück.|
|[SetPosition](../api/chart_setposition.md)|Keine|Positioniert das Diagramm relativ zur Zellen im Arbeitsblatt.|
|[Liste](../api/chart_list.md) | [Diagramm](chart.md) -Auflistung |Rufen Sie die Auflistung des Chart-Objekts. |
|[Itemat](../api/chartcollection_itemat.md)|[Diagramm](chart.md)|Dient zum Abrufen eines Diagramms basierend auf seiner Position in der Auflistung.|
|[Fügen Sie hinzu](../api/chartcollection_add.md)|[Diagramm](chart.md)|Erstellt ein neues Diagramm.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|height|double|Die Höhe in Punkt des Chart-Objekts darstellt.|
|id|string|Dient zum Abrufen eines Diagramms basierend auf seiner Position in der Auflistung. Schreibgeschützt.|
|left|double|Der Abstand zwischen der linken Seite des Diagramms in Arbeitsblatt Ursprung in Punkt.|
|name|string|Den Namen des eines Chart-Objekts darstellt.|
|top|double|Stellt den Abstand in Punkt vom oberen Rand des Objekts an den Anfang der Zeile 1 (auf einem Arbeitsblatt) oder im oberen Bereich des Diagrammbereichs (in einem Diagramm).|
|width|double|Die Breite in Punkt des Chart-Objekts darstellt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Achsen|[ChartAxes](chartaxes.md)|Achsen Diagramm repräsentiert. Schreibgeschützt.|
|dataLabels|[ChartDataLabels](chartdatalabels.md)|Die Datalabels im Diagramm darstellt. Schreibgeschützt.|
|Format|[ChartAreaFormat](chartareaformat.md)|Die Formateigenschaften für den Diagrammbereich kapselt. Schreibgeschützt.|
|Legende|[ChartLegend](chartlegend.md)|Stellt die Legende für das Diagramm dar. Schreibgeschützt.|
|Datenreihe|[ChartSeries](chartseries.md) -Auflistung|Stellt dar, das eine einzelne Datenreihe oder eine Auflistung von Datenreihen im Diagramm. Schreibgeschützt.|
|title|[ChartTitle](charttitle.md)|Stellt den Titel des angegebenen Diagramms, einschließlich Text, Sichtbarkeit, Position und Formatierung des Titels dar. Schreibgeschützt.|
|worksheet|[Arbeitsblatt](worksheet.md)|Das Arbeitsblatt, das aktuelle Diagramm enthält. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chart"
}-->

```json
{
  "height": 1024,
  "id": "string",
  "left": 1024,
  "name": "string",
  "top": 1024,
  "width": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Chart resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->