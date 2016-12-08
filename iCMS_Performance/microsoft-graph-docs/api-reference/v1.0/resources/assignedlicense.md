# <a name="assignedlicense-resource-type"></a>Ressourcentyp assignedLicense

Stellt eine Lizenz, die einem Benutzer zugewiesen. Die **AssignedLicenses** -Eigenschaft der Entität [Benutzer](user.md) ist eine Auflistung von **AssignedLicense**.

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|disabledPlans|GUID-Auflistung|Eine Auflistung der eindeutige Bezeichner für Pläne, die deaktiviert wurden.|
|skuId|Guid|Der eindeutige Bezeichner für die SKU.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.assignedLicense"
}-->

```json
{
  "disabledPlans": ["guid"],
  "skuId": "guid"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "assignedLicense resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
