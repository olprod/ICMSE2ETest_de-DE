# <a name="location-resource-type"></a>Typ des Speicherorts Ressource

Standortinformationen eines Ereignisses darstellt.


## <a name="properties"></a>Eigenschaften
| Eigenschaft  | Typ   | Beschreibung                                                     |
|:----------|:-------|:----------------------------------------------------------------|
| address | [physikalische Adresse](physicalAddress.md) |Die Straße des Speicherorts. |
| Koordinaten | [outlookGeoCoordinates](outlookGeoCoordinates.md) |Die geografischen Koordinaten, Erhöhung und deren Grad der Genauigkeit für einen physischen Standort. |
| displayName  | String | Der Name der Standort zugeordnet.                       |
| locationEmailAddress | String | Optionale e-Mail-Adresse des Speicherorts.              |
| locationUri | String | Darstellung des Speicherorts für URI ist optional.|


## <a name="json-representation"></a>JSON-Darstellung

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.location"
}-->
```json
{
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "coordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},  
  "displayName": "string",
  "locationEmailAddress": "string",
  "locationUri": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "location resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->