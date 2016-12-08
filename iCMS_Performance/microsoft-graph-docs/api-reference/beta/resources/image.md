# <a name="image-resource-type"></a>Bildressourcentyp

**Die Bildressource** steht für Elemente, die eine Bitmap oder Grafik darstellen.


## <a name="properties"></a>Eigenschaften

| Eigenschaft   | Typ  | Beschreibung                                |
|:-----------|:------|:-------------------------------------------|
| **Höhe** | Int32 | Die Höhe des Bilds in Pixeln. Schreibgeschützt. |
| **Breite**  | Int32 | Breite des Bilds in Pixeln. Schreibgeschützt.  |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.image"
}-->

```json
{
  "height": 1024,
  "width": 1024
}

```

## <a name="remarks"></a>Hinweise

In OneDrive for Business wird diese Ressource Elemente zurückgegeben, die Bilder basierend auf Erweiterung vorhanden sein. Diese Ressource zurückgegeben keine Eigenschaften in OneDrive for Business.


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "image resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
