# <a name="timeconstraint-resource-type"></a>Ressourcentyp timeConstraint

Der Zeiträume für eine Aktivität der angegebenen Art.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.timeconstraint"
}-->

```json
{
  "activityDomain": "String",
  "timeslots": [{"@odata.type": "microsoft.graph.timeSlot"}]
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|activityDomain|String|Die Art der Aktivität, optional. Mögliche Werte sind: `unknown`, `work`, `personal`. Derzeit [FindMeetingTimes](../api/user_findmeetingtimes.md) immer nimmt an, dass der Wert `work` und gibt Besprechungsvorschläge nur während der Arbeitszeiten der Organisator oder Teilnehmer.|
|Zeitabschnitte an|[Zeitrahmen](timeslot.md) -Auflistung|Ein Array von Zeiträumen.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "timeConstraint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->