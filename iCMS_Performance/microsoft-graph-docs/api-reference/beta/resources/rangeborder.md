# <a name="rangeborder-resource-type"></a>Ressourcentyp RangeBorder

Stellt den Rahmen eines Objekts dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von RangeBorder](../api/rangeborder_get.md) | [RangeBorder](rangeborder.md) |Lesen Sie Eigenschaften und Beziehungen RangeBorder-Objekts.|
|[Update](../api/rangeborder_update.md) | [RangeBorder](rangeborder.md) |RangeBorder-Objekt zu aktualisieren. |
|[Liste](../api/rangeborder_list.md) | [RangeBorder](rangeborder.md) -Auflistung |Rufen Sie RangeBorder-Auflistung-Objekts. |
|[Itemat](../api/rangebordercollection_itemat.md)|[RangeBorder](rangeborder.md)|Ruft ein Border-Objekt über diesen index|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|color|string|HTML-Farbcode, der die Farbe der Rahmenlinie, des Formulars #RRGGBB (z. B. "FFA500") oder als eine benannte HTML-Farbe (z. B. "orange").|
|id|string|Stellt Rahmen Bezeichner. Possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. Schreibgeschützt.|
|sideIndex|string|Konstanter Wert, der angibt, die bestimmte Seiten des Rahmens. Possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. Schreibgeschützt.|
|style|string|Eine der Konstanten der Linienart die Linienart für den Rahmen angeben. Possible values are: `None`, `Continuous`, `Dash`, `DashDot`, `DashDotDot`, `Dot`, `Double`, `SlantDashDot`.|
|weight|string|Gibt die Stärke des Rahmens um einen Bereich. Mögliche Werte sind: `Hairline`, `Thin`, `Medium`, `Thick`.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeBorder"
}-->

```json
{
  "color": "string",
  "id": "string",
  "sideIndex": "string",
  "style": "string",
  "weight": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "RangeBorder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->