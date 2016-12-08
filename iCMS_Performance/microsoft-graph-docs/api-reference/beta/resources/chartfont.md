# <a name="chartfont-resource-type"></a>ChartFont-Ressourcentyp

Dieses Objekt stellt die Schriftattribute (Name der Schriftart, Schriftgrad, Farbe usw.) für ein Diagrammobjekt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[ChartFont abrufen](../api/chartfont_get.md) | [ChartFont](chartfont.md) |Lesen Sie Eigenschaften und Beziehungen zwischen ChartFont-Objekt.|
|[Update](../api/chartfont_update.md) | [ChartFont](chartfont.md)   |ChartFont-Objekt zu aktualisieren. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bold|boolean|Stellt den Schriftart fett Status dar.|
|color|string|HTML-Farbe Code Darstellung der Textfarbe. Diese Vorgaben unter #FF0000 für Rot.|
|italic|boolean|Stellt den Status die Schriftart kursiv formatiert.|
|name|string|Name der Schriftart (z. B. "Calibri")|
|Schriftgröße|double|Der Schriftgrad (z. B. 11)|
|Unterstreichen|string|Typ der Unterstreichung auf die Schriftart. Mögliche Werte sind: `None`, `Single`.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartFont"
}-->

```json
{
  "bold": true,
  "color": "string",
  "italic": true,
  "name": "string",
  "size": 1024,
  "underline": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartFont resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->