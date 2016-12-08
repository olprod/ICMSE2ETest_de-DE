# <a name="geocoordinates-resource-type"></a>Ressourcentyp geoCoordinates

Die geografische Koordinaten und Ausweitung von einem Speicherort.

Diese Ressource gruppiert geografische Standort-Daten im Zusammenhang mit in OneDrive in einer einzelnen Struktur. Es steht auf der **Location** -Eigenschaft des Elements Ressourcen mit einer zugeordneten geografischen Standort.


## <a name="properties"></a>Eigenschaften

| Eigenschaft  | Typ   | Beschreibung                                                    |
|:----------|:-------|:---------------------------------------------------------------|
| Höhe  | Double | Die Höhe (Höhe) in Fuß, über gefährliche Ebene für das Element. |
| Breitengrad  | Double | Die Breite in dezimaler für das Element.                        |
| Längengrad | Double | Die Länge Dezimal, für das Element.                       |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.geoCoordinates"
}-->

```json
{
  "altitude": 1024.13,
  "latitude": 26.13246,
  "longitude": 24.34616
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "geoCoordinates resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
