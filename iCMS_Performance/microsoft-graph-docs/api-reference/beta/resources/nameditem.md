# <a name="nameditem-resource-type"></a>GetNamedItem Ressourcentyp

Stellt einen definierten Namen für einen Bereich von Zellen oder Wert dar. Namen primitiven benannte Objekte (wie in der folgenden Typ dargestellt), "range"-Objekt; Verweis auf einen Bereich. Dieses Objekt kann verwendet werden, um Range-Objekt zugeordneten Namen zu erhalten.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[GetNamedItem abrufen](../api/nameditem_get.md) | [GetNamedItem](nameditem.md) |Lesen Sie Eigenschaften und Beziehungen GetNamedItem-Objekts.|
|[Update](../api/nameditem_update.md) | [GetNamedItem](nameditem.md)   |GetNamedItem-Objekt zu aktualisieren. |
|[Bereich](../api/nameditem_range.md)|[Bereich](range.md)|Gibt das Range-Objekt, das mit dem Namen zugeordnet ist. Löst eine Ausnahme aus, wenn das benannte Element Typ kein Bereich ist.|
|[Liste](../api/nameditem_list.md) | [GetNamedItem](nameditem.md) -Auflistung |Auflistung der getNamedItem-Objekts abrufen. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|name|string|Der Name des Objekts. Schreibgeschützt.|
|Typ|string|Gibt an, welche Art von Bezug den Namen zugeordnet ist. Mögliche Werte sind: `String`, `Integer`, `Double`, `Boolean`, `Range`. Schreibgeschützt.|
|value|object|Stellt die Formel, die auf der Namen definiert ist finden Sie unter. Diese Vorgaben unter = Sheet14! $B$ 2: $H$ 12 = 4,75, usw.. Schreibgeschützt.|
|visible|boolean|Gibt an, ob das Objekt sichtbar ist.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.namedItem"
}-->

```json
{
  "name": "string",
  "type": "string",
  "value": {"@odata.type": "microsoft.graph.range"},
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "NamedItem resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->