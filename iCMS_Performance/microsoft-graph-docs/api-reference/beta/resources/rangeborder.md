# <a name="rangeborder-resource-type"></a>RangeBorder resource type

Stellt den Rahmen eines Objekts dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get RangeBorder](../api/rangeborder_get.md) | [RangeBorder](rangeborder.md) |Read properties and relationships of rangeBorder object.|
|[Update](../api/rangeborder_update.md) | [RangeBorder](rangeborder.md) |Update RangeBorder object. |
|[List](../api/rangeborder_list.md) | [RangeBorder](rangeborder.md) collection |Get rangeBorder object collection. |
|[Itemat](../api/rangebordercollection_itemat.md)|[RangeBorder](rangeborder.md)|Ruft ein Rahmen-Objekt ab, das den Namen verwendet|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|color|string|HTML-Farbcode, der die Farbe der Rahmenlinie, des Formulars #RRGGBB (z. B.  "FFA500") oder als benannte HTML-Farbe (z. B. "orange") darstellt.|
|id|string|Represents border identifier. Possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. Read-only.|
|sideIndex|string|Konstanter Wert, der die bestimmte Seiten des Rahmens angibt. Schreibgeschützt. Die folgenden Werte sind möglich: EdgeTop, EdgeBottom, EdgeLeft, EdgeRight, InsideVertical, InsideHorizontal, DiagonalDown, DiagonalUp.|
|style|string|Einer der Konstanten der Linienart, die die Linienart für den Rahmen angibt. Die folgenden Werte sind möglich: None, Continuous, Dash, DashDot, DashDotDot, Dot, Double, SlantDashDot.|
|weight|string|Gibt die Stärke des Rahmens um einen Bereich an. Die folgenden Werte sind möglich: Haarlinie, Dünn, Mittel, Dick.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

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