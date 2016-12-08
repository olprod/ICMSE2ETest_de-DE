# <a name="rangefont-resource-type"></a>Ressourcentyp RangeFont

Dieses Objekt stellt die Schriftattribute (Name der Schriftart, Schriftgrad, Farbe usw.) für ein Objekt dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von RangeFont](../api/rangefont_get.md) | [RangeFont](rangefont.md) |Lesen Sie Eigenschaften und Beziehungen RangeFont-Objekts.|
|[Update](../api/rangefont_update.md) | [RangeFont](rangefont.md)   |RangeFont-Objekt zu aktualisieren. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bold|boolean|Stellt den Schriftart fett Status dar.|
|color|string|HTML-Farbe Code Darstellung der Textfarbe. Diese Vorgaben unter #FF0000 für Rot.|
|italic|boolean|Stellt den Status die Schriftart kursiv formatiert.|
|name|string|Name der Schriftart (z. B. "Calibri")|
|Schriftgröße|double|Schriftgrad.|
|underline|string|Typ der Unterstreichung auf die Schriftart. Mögliche Werte sind: `None`, `Single`, `Double`, `SingleAccountant`, `DoubleAccountant`.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeFont"
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
  "description": "RangeFont resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->