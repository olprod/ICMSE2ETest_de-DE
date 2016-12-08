# <a name="meetingtimecandidatesresult-resource-type"></a>Ressourcentyp meetingTimeCandidatesResult

Eine Auflistung von besprechungsvorschlägen ist vorhanden, oder der Grund dafür, wenn nicht vorhanden ist.

Folgen die möglichen Gründe, dass diese [FindMeetingTimes](../api/user_findmeetingtimes.md) kein Besprechungsvorschläge zurückgibt.

|**EmptySuggestionsHint Wert**|**Aus Gründen der**|
|:-----|:-----|
| attendeesUnavailable | Alle für die Verfügbarkeit der Teilnehmer bekannt ist, aber nicht genügend Teilnehmer die Besprechung erreichen stehen Confidence Schwellenwert, die für jeden Zeitraum 50 % in der Standardeinstellung ist. Dieser Grenzwert basiert auf der Teilnehmer Frei/Gebucht-Status für einer vorgeschlagenen Besprechung Zeitraum an, mit dem eines Teilnehmers kostenlose Status, Anwesenheit, Status unbekannt 50 % und gebucht-Status 0 % Wahrscheinlichkeit 100 % entspricht.|
| attendeesUnavailableOrUnknown | Wurden einige oder alle der Teilnehmer unbekannt Verfügbarkeit, verursacht die Besprechung Confidence unter dem Schwellenwert Set fallen die 50 % in der Standardeinstellung ist. Verfügbarkeit von Teilnehmern kann nicht bekannt werden, wenn der Teilnehmer außerhalb der Organisation ist, oder es ist ein Fehler beim Abrufen der Frei/Gebucht-Informationen.|
| locationsUnavailable | **IsRequired** -Eigenschaft des Parameters [LocationConstraint](locationconstraint.md) als obligatorisch angegeben ist, und noch keine Standorte verfügbar sind unter der Steckplätze berechnete Zeit. |
| organizerUnavailable | Der Parameter **IsOrganizerOptional** ist false und noch der Organisator ist nicht verfügbar während des angeforderten Zeitfensters. |
| unbekannt | Der Grund für die Rückgabe kein Besprechungsvorschläge ist nicht bekannt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.meetingTimeCandidatesResult"
}-->

```json
{
  "emptySuggestionsHint": "String",
  "meetingTimeSlots": [{"@odata.type": "microsoft.graph.meetingTimeCandidate"}]
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|emptySuggestionsHint|String|Einen Grund für die Besprechungsvorschläge nicht zurückgeben. Mögliche Werte sind: `attendeesUnavailable`, `attendeesUnavailableOrUnknown`, `locationsUnavailable`, `organizerUnavailable`, oder `unknown`.|
|meetingTimeSlots|[MeetingTimeCandidate](meetingTimeCandidate.md) -Auflistung|Ein Array von besprechungsvorschlägen.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "meetingTimeCandidatesResult resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->