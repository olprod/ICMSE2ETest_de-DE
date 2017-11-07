# <a name="rangefill-resource-type"></a>Ressourcentyp RangeFill

Stellt den Hintergrund eines Range-Objekts dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von RangeFill](../api/rangefill_get.md) | [RangeFill](rangefill.md) |Lesen Sie Eigenschaften und Beziehungen des RangeFill-Objekts.|
|[Update](../api/rangefill_update.md) | [RangeFill](rangefill.md)   |Aktualisieren Sie RangeFill-Objekts. |
|[Deaktivieren](../api/rangefill_clear.md)|Keine|Setzt den Hintergrund des Bereichs zurück.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|color|string|HTML-Farbcode, der die Farbe der Rahmenlinie, des Formulars #RRGGBB (z. B. "FFA500") oder als eine benannte HTML-Farbe (z. B. "orange")|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeFill"
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
  "description": "RangeFill resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->