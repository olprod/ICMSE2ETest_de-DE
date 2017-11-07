# <a name="sortfield-resource-type"></a>SortField-Ressourcentyp

Stellt eine Bedingung in einem Sortiervorgang dar.

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Aufsteigend|boolean|Stellt dar, ob die Sortierung in aufsteigender Weise erfolgt.|
|color|string|Stellt die Farbe, die als Ziel für die Bedingung wird, falls der Sortierung auf Schriftart oder einer Zelle Farbe angezeigt wird.|
|dataOption|string|Weitere Sortieroptionen für dieses Feld darstellt. Mögliche Werte sind: `Normal`, `TextAsNumber`.|
|Key|int|Stellt die Spalte (oder Zeile, je nach Ausrichtung der Sortierung), in der die Bedingung ist. Dargestellt als Offset aus der ersten Spalte (oder Zeile) ein.|
|sortOn|string|Stellt den Typ der Sortierung der diese Bedingung. Mögliche Werte sind: `Value`, `CellColor`, `FontColor`, `Icon`.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Symbol|[Symbol](icon.md)|Stellt das Symbol, das das Ziel der Bedingung ist, wenn der Sortierung auf die Zelle Symbol befindet.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sortField"
}-->

```json
{
  "ascending": true,
  "color": "string",
  "dataOption": "string",
  "key": 1024,
  "sortOn": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "SortField resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->