# <a name="outlookgeocoordinates-resource-type"></a>Ressourcentyp outlookGeoCoordinates

Die geografischen Koordinaten, Erhöhung und deren Grad der Genauigkeit für einen physischen Standort.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.outlookGeoCoordinates"
}-->

```json
{
  "accuracy": 1024,
  "altitude": 1024,
  "altitudeAccuracy": 1024,
  "latitude": 1024,
  "longitude": 1024
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Genauigkeit|double|Die Genauigkeit der Breiten- und Längengrad. Beispielsweise kann die Genauigkeit in Meter, gemessen werden, wie die Breiten- und Längengrad auf 50 m genau sind.|
|Höhe|double|Die Höhe des Speicherorts.|
|altitudeAccuracy|double|Die Genauigkeit der Höhe.|
|Breitengrad|double|Die Breite des Speicherorts.|
|Längengrad|double|Die Länge des Speicherorts.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "outlookGeoCoordinates resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->