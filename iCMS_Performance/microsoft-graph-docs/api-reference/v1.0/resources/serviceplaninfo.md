# <a name="serviceplaninfo-resource-type"></a>Ressourcentyp servicePlanInfo

Enthält Informationen zu einem Serviceplan eine abonnierten SKU zugeordnet. Die **ServicePlans** -Eigenschaft der [SubscribedSku](subscribedsku.md) Entität ist eine Auflistung von **ServicePlanInfo**.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|servicePlanId|Guid|Der eindeutige Bezeichner des Serviceplans.|
|servicePlanName|String|Der Name des Serviceplans.|
|provisioningStatus|String|Der Bereitstellungsstatus die Dienstplan.|
|appliesTo|String||


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.servicePlanInfo"
}-->

```json
{
  "appliesTo": "string",
  "provisioningStatus": "string",
  "servicePlanId": "guid",
  "servicePlanName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "servicePlanInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
