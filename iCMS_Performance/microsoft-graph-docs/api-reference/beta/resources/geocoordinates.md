# <a name="geocoordinates-resource-type"></a>geoCoordinates resource type

The geographic coordinates and elevation of a location.

This resource groups geographic location-related data on OneDrive into a single structure. It is available on the **location** property of item resources that have an associated geographic location.


## <a name="properties"></a>Eigenschaften

| Eigenschaft  | Typ   | Beschreibung                                                    |
|:----------|:-------|:---------------------------------------------------------------|
| Altitude  | Double | The altitude (height), in feet,  above sea level for the item. |
| Latitude  | Double | The latitude, in decimal, for the item.                        |
| Longitude | Double | The longitude, in decimal, for the item.                       |

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource

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
