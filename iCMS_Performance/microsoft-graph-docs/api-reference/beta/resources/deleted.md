# <a name="deleted-resource-type"></a>Ressourcentyp gelöscht

Die Ressource **gelöscht** gibt an, dass das Element gelöscht wurde. In dieser Version der API gibt das Vorhandensein der Ressourcenwert (ungleich Null), dass die Datei gelöscht wurde. Ein Wert null (oder fehlenden) gibt an, dass die Datei nicht gelöscht wird.

[Ansicht Änderungen für ein Element](../api/item_delta.md) Weitere Informationen finden Sie unter.

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ   | Beschreibung                               |
|:---------|:-------|:------------------------------------------|
| Zustand    | String | Stellt den Zustand des gelöschten Elements dar. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
  "state"
  ],
  "@odata.type": "microsoft.graph.deleted"
}-->
```json
{
  "state": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "deleted resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
