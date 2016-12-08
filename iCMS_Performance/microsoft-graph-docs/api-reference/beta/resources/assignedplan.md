# <a name="assignedplan-resource-type"></a>Ressourcentyp assignedPlan

Die **AssignedPlans** -Eigenschaft der Entität [Benutzer](user.md) und die [Organisation](organization.md) Entität ist eine Auflistung von **AssignedPlan**.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assignedDateTime|DateTimeOffset|Datum und Uhrzeit, zu der der Plan zugewiesen wurde; Beispiel: 2013-01-02T19:32:30Z. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|capabilityStatus|String|Beispielsweise aktiviert"."|
|Dienst|String|Der Name des Diensts. beispielsweise "Exchange".|
|servicePlanId|Guid|Eine GUID, die Dienstplan identifiziert.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.assignedPlan"
}-->

```json
{
  "assignedDateTime": "String (timestamp)",
  "capabilityStatus": "string",
  "service": "string",
  "servicePlanId": "guid"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "assignedPlan resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
