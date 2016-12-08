# <a name="charttitle-resource-type"></a>ChartTitle Ressourcentyp

Stellt ein Diagrammobjekt Titel eines Diagramms dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[ChartTitle abrufen](../api/charttitle_get.md) | [ChartTitle](charttitle.md) |Lesen Sie Eigenschaften und Beziehungen zwischen ChartTitle-Objekt.|
|[Update](../api/charttitle_update.md) | [ChartTitle](charttitle.md)    |Aktualisieren Sie die ChartTitle-Objekt. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Overlay|boolean|Boolescher Wert, wenn Sie der Titel des Diagramms Überlagerung werden.|
|text|string|Stellt den Titeltext eines Diagramms dar.|
|visible|boolean|Ein boolescher Wert, die Sichtbarkeit eines Diagramms Titel-Objekts darstellt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[ChartTitleFormat](charttitleformat.md)|Stellt die Formatierung der Titel eines Diagramms, das Füllung und die schriftartformatierung enthält. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartTitle"
}-->

```json
{
  "overlay": true,
  "text": "string",
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartTitle resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->