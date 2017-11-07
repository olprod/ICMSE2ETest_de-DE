# <a name="subscribedsku-resource-type"></a>Ressourcentyp subscribedSku

Nur der Lesevorgang wird unter abonnierten SKUs unterstützt. Erstellen, Update und Delete werden nicht unterstützt. Abfrageausdrücke Filter werden nicht unterstützt. Erbt vom [DirectoryObject](directoryobject.md).


## <a name="methods"></a>Methoden
| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[SubscribedSku abrufen](../api/subscribedsku_get.md) | [subscribedSku](subscribedsku.md) |Lesen Sie Eigenschaften und Beziehungen des SubscribedSku-Objekts.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|capabilityStatus|String||
|consumedUnits|Int32||
|id|String| -Taste. Schreibgeschützt.|
|prepaidUnits|[licenseUnitsDetail](licenseunitsdetail.md)||
|servicePlans|[ServicePlanInfo](serviceplaninfo.md) -Auflistung||
|skuId|Guid||
|skuPartNumber|String||
|appliesTo|String||

## <a name="relationships"></a>Beziehungen
Keine

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.subscribedSku"
}-->

```json
{
  "appliesTo": "string",
  "capabilityStatus": "string",
  "consumedUnits": 1024,
  "id": "string (identifier)",
  "prepaidUnits": {"@odata.type": "microsoft.graph.licenseUnitsDetail"},
  "servicePlans": [{"@odata.type": "microsoft.graph.servicePlanInfo"}],
  "skuId": "guid",
  "skuPartNumber": "string"
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "subscribedSku resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
