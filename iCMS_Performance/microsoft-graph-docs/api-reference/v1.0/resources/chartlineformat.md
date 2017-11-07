# <a name="chartlineformat-resource-type"></a>Ressourcentyp ChartLineFormat

Enapsulates die Formatierungsoptionen für Zeile Elemente.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von ChartLineFormat](../api/chartlineformat_get.md) | [ChartLineFormat](chartlineformat.md) |Lesen Sie Eigenschaften und Beziehungen des ChartLineFormat-Objekts.|
|[Update](../api/chartlineformat_update.md) | [ChartLineFormat](chartlineformat.md) |ChartLineFormat-Objekt zu aktualisieren. |
|[Deaktivieren](../api/chartlineformat_clear.md)|Keine|Deaktivieren Sie das Format Zeile eines Diagrammelements.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|color|string|HTML-Farbcode, die Farbe der Zeilen im Diagramm darstellt.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartLineFormat"
}-->

```json
{
  "color": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartLineFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->