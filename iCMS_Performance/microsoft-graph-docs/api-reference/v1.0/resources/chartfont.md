# <a name="chartfont-resource-type"></a>ChartFont resource type

Dieses Objekt stellt die Zeichenformatierung (Schriftart, Schriftgrad, Farbe usw.) für ein Diagrammobjekt dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get ChartFont](../api/chartfont_get.md) | [ChartFont-Objekt](chartfont.md) |Read properties and relationships of chartFont object.|
|[Update](../api/chartfont_update.md) | [ChartFont-Objekt](chartfont.md)   |Update ChartFont object. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bold|boolean|Stellt den Fett-Status der Schriftart dar.|
|color|string|HTML-Farbcodedarstellung der Textfarbe. #ff0000 stellt beispielsweise Rot dar.|
|Kursiv|boolean|Stellt den Kursiv-Status der Schriftart dar.|
|name|string|Schriftartname (z. B. "Calibri")|
|Schriftgröße|double|Der Schriftgrad (z. B. 11)|
|Unterstreichen|string|Art der auf die Schriftart angewendete Unterstreichung. Die folgenden Werte sind möglich: Keine, einfache.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

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