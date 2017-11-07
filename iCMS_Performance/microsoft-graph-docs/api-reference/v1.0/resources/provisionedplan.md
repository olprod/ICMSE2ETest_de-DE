# <a name="provisionedplan-resource-type"></a>Ressourcentyp provisionedPlan

Die **ProvisionedPlans** -Eigenschaft der Entität [Benutzer](user.md) und die [Organisation](organization.md) Entität ist eine Auflistung von **ProvisionedPlan**.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|capabilityStatus|String|Beispielsweise aktiviert"."|
|provisioningStatus|String|Beispielsweise "Erfolg".|
|Dienst|String|Der Name des Diensts. beispielsweise "AccessControlS2S"|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.provisionedplan"
}-->

```json
{
  "capabilityStatus": "string",
  "provisioningStatus": "string",
  "service": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "provisionedPlan resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->