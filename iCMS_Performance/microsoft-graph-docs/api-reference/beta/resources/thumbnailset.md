# <a name="thumbnailset-resource-type"></a>Ressourcentyp thumbnailSet

Der **ThumbnailSet** -Typ ist eine verschlüsselte Auflistung von [Miniaturansicht](thumbnail.md) -Objekten. Es wird verwendet, um eine Reihe von Miniaturansichten im Zusammenhang mit einer einzigen Datei auf OneDrive darstellen.


## <a name="methods"></a>Methoden

| Methode                                         | Rückgabetyp                     | Beschreibung                                               |
|:-----------------------------------------------|:--------------------------------|:----------------------------------------------------------|
| [Abrufen von thumbnailSet](../api/thumbnailset_get.md) | [thumbnailSet](thumbnailset.md) | Lesen Sie Eigenschaften und Beziehungen des ThumbnailSet-Objekts. |

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ                      | Beschreibung                                                                       |
|:---------|:--------------------------|:----------------------------------------------------------------------------------|
| id       | String                    | Die Id innerhalb des Elements. Schreibgeschützt.                                                |
| große    | [Miniaturansicht](thumbnail.md) | Eine skalierte 1920 x 1920-Miniaturansicht.                                                     |
| Mittel   | [Miniaturansicht](thumbnail.md) | Eine skalierte 176 x 176-Miniaturansicht.                                                       |
| kleine    | [Miniaturansicht](thumbnail.md) | 48 x 48 zugeschnittene Miniaturansicht.                                                        |
| Quelle   | [Miniaturansicht](thumbnail.md) | Ein benutzerdefinierter Miniaturbild oder das ursprüngliche Bild verwendet, um andere Miniaturansichten zu generieren. |


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "source"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.thumbnailSet"
}-->

```json
{
  "id": "string (identifier)",
  "large": {"@odata.type": "microsoft.graph.thumbnail"},
  "medium": {"@odata.type": "microsoft.graph.thumbnail"},
  "small": {"@odata.type": "microsoft.graph.thumbnail"},
  "source": {"@odata.type": "microsoft.graph.thumbnail"}
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "thumbnailSet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
