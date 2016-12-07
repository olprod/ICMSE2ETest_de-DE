# <a name="thumbnail-resource-type"></a>thumbnail resource type

The **thumbnail** resource type represents a thumbnail for an image, video, document, or any file or folder on OneDrive that has a graphical representation.

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ   | Beschreibung                                  |
|:---------|:-------|:---------------------------------------------|
| height   | Int32  | Optional. Die Höhe des Steuerelements in Pixeln.      |
| URL      | String | The URL used to fetch the thumbnail content. |
| width    | Int32  | Die Breite oder Höhe des Bilds in Pixel.       |


## <a name="relationships"></a>Beziehungen

| Name    | Typ   | Beschreibung         |
|:--------|:-------|:--------------------|
| Inhalt | Stream | The content stream. |


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": ["content", "height", "width"],
  "@odata.type": "microsoft.graph.thumbnail"
}-->

```json
{
  "url": "string",
  "height": 1024,
  "width": 1024,
  "content": "stream"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "thumbnail resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
