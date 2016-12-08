# <a name="meetingtimecandidate-resource-type"></a>Ressourcentyp meetingTimeCandidate

Ein besprechungsvorschlag, das Informationen wie die Besprechungszeit, Anwesenheit Wahrscheinlichkeit, individuelle Präsenz und verfügbaren Besprechung Speicherorte enthält.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.meetingTimeCandidate"
}-->

```json
{
  "attendeeAvailability": [{"@odata.type": "microsoft.graph.attendeeAvailability"}],
  "confidence": 1024,
  "locations": [{"@odata.type": "microsoft.graph.location"}],
  "meetingTimeSlot": {"@odata.type": "microsoft.graph.timeSlot"},
  "organizerAvailability": "String",
  "suggestionHint": "String"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|attendeeAvailability|[AttendeeAvailability](attendeeavailability.md) -Auflistung|Ein Array, das den Verfügbarkeitsstatus der einzelnen Teilnehmer für diese besprechungsvorschlag anzeigt.|
|Vertrauen|Double|Prozentsatz, der von allen Teilnehmern, die Teilnahme an der Likelhood darstellt.|
|Speicherorte|[Standort](location.md) -Auflistung|Ein Array, das den Namen und den geografischen Standort der verschiedenen Speicherorte Besprechung für diese besprechungsvorschlag angibt.|
|meetingTimeSlot|[Zeitrahmen](timeslot.md)|Ein Zeitraum für die Besprechung vorgeschlagen.|
|organizerAvailability|String| Verfügbarkeit der Organisator der Besprechung für diese besprechungsvorschlag. Possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`.|
|suggestionHint|String|Grund für die Besprechungszeit vorschlagen.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "meetingTimeCandidate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->