# <a name="phone-resource-type"></a>Phone Ressourcentyp

Stellt eine Telefonnummer ein.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|number|string|Die Telefonnummer.|
|Typ|String|Der Typ der Telefonnummer. Possible values are: `home`, `business`, `mobile`, `other`, `assistant`, `homeFax`, `businessFax`, `otherFax`, `pager`, `radio`.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.phone"
}-->

```json
{
  "number": "string",
  "type": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "phone resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->