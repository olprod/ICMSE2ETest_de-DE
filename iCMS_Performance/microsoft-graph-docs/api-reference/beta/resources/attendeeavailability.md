# <a name="attendeeavailability-resource-type"></a>Ressourcentyp attendeeAvailability

Der Typ und der Verfügbarkeit eines Teilnehmers.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.attendeeAvailability"
}-->

```json
{
  "attendee": {"@odata.type": "microsoft.graph.attendeeBase"},
  "availability": "String"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Teilnehmer|[AttendeeBase](attendeebase.md)|Der Typ des Attendee – ob es eine Person oder eine Ressource ist, und ob erforderlich oder optional, wenn sie eine Person handelt.|
|Verfügbarkeit|String| Der Verfügbarkeitsstatus des Teilnehmers. Possible values are: `Free`, `Tentative`, `Busy`, `Oof`, `WorkingElsewhere`, `Unknown`.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "attendeeAvailability resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->