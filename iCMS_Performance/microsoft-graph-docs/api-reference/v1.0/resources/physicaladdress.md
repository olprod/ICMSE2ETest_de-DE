# <a name="physicaladdress-resource-type"></a>physikalische Adresse Ressourcentyp

Die Adresse einer Ressource wie einen Kontakt oder eine Ereignis darstellt.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Ort|String|Der Ort.|
|countryOrRegion|String|Land oder Region.|
|postalCode|String|Die Postleitzahl.|
|Zustand|String|Der Zustand.|
|Straße|String|Die Straße.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.physicalAddress"
}-->

```json
{
  "city": "string",
  "countryOrRegion": "string",
  "postalCode": "string",
  "state": "string",
  "street": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "physicalAddress resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
