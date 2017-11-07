# <a name="video-resource-type"></a>Video Ressourcentyp

**Die Videoressourcen** gibt an, eines Elements ist eine Datei Videomedien und finden Sie Informationen über das Video.

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ  | Beschreibung                               |
|:---------|:------|:------------------------------------------|
| Bitrate  | Int32 | Bitrate des Videos in Bits pro Sekunde. |
| duration | Int64 | Dauer der Datei in Millisekunden.     |
| height   | Int32 | Die Höhe des Videos in Pixel.           |
| width    | Int32 | Die Breite des Videos in Pixel.            |



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.video"
}-->

```json
{
  "bitrate": 1024,
  "duration": 1024,
  "height": 1024,
  "width": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "video resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
