# <a name="event-resource-type"></a>Ereignistyp-Ressource

Ein Ereignis in einem Kalender.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[List-Ereignisse](../api/user_list_events.md)|[Ereignissammlung](event.md) |Abrufen einer Liste der [Ereignisobjekte im Postfach des Benutzers](../resources/event.md) an. Die Liste enthält Einzelinstanz Besprechungen und Series-Master.|
|[Ereignis erstellen](../api/user_post_events.md) |[Ereignis](event.md)| Erstellen Sie ein neues Ereignis durch die Veröffentlichung auf der Instanzen-Auflistung.|
|[-Ereignis](../api/event_get.md) | [Ereignis](event.md) |Lesen Sie Eigenschaften und Beziehungen des Event-Objekts.|
|[Update](../api/event_update.md) | [Ereignis](event.md) |Event-Objekt zu aktualisieren. |
|[Löschen](../api/event_delete.md) | Keine |Event-Objekt zu löschen. |
|[akzeptieren](../api/event_accept.md)|Keine|Akzeptieren Sie das angegebene Ereignis.|
|[tentativelyAccept](../api/event_tentativelyaccept.md)|Keine|Das angegebene Ereignis mit Vorbehalt annehmen.|
|[Ablehnen](../api/event_decline.md)|Keine|Auf das angegebene Ereignis Einladung ablehnen.|
|[dismissReminder](../api/event_dismissreminder.md)|Keine|Schließen Sie die Erinnerung für das angegebene Ereignis.|
|[snoozeReminder](../api/event_snoozereminder.md)|Keine|Erneut erinnern Sie die Erinnerung für das angegebene Ereignis aus.|
|[Listeninstanzen](../api/event_list_instances.md) |[Ereignissammlung](event.md)| Rufen Sie die Instanzen (vorkommen) eines Ereignisses für einen angegebenen Zeitraum. Wenn das Ereignis gehört zu einer `SeriesMaster` Typ, dies gibt die Vorkommen und Ausnahmen des Ereignisses in den angegebenen Zeitraum.|
|[Anlagen auflisten](../api/event_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Auflistung des Attachment-Objekt.|
|[Erstellen der Anlage](../api/event_post_attachments.md) |[Anlage](attachment.md)| Erstellen Sie eine neue Anlage, indem Sie das Veröffentlichen in der Attachments-Auflistung.|
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine open Typ Daten Erweiterung und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Teilnehmer|[ATTENDEE](attendee.md) -Auflistung|Die Auflistung der Teilnehmer für das Ereignis.|
|body|[itemBody](itembody.md)|Der Textkörper der Nachricht mit dem Ereignis verknüpft ist.|
|bodyPreview|String|Die Vorschau der Nachricht mit dem Ereignis verknüpft ist.|
|Kategorien|Zeichenfolgenauflistung|Die Kategorien, die mit dem Ereignis verknüpft ist.|
|changeKey|String|Identifiziert die Version des Event-Objekts. Jedes Mal, wenn das Ereignis geändert wird, ändert ChangeKey sowie. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen.|
|createdDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Ende|[dateTimeTimeZone](datetimetimezone.md)|Das Datum, Uhrzeit und Zeitzone, die das Ereignis aus.|
|hasAttachments|Boolean|Wenn das Ereignis Anlagen enthält true festgelegt.|
|iCalUId|String|Ein eindeutiger Bezeichner, der von allen Instanzen eines Ereignisses in unterschiedlichen Kalendern freigegeben ist.|
|id|String| Schreibgeschützt.|
|Bedeutung|String|Die Bedeutung des Ereignisses: Niedrig = 0 Normal = 1, hoch = 2. Mögliche Werte sind: `Low`, `Normal`, `High`.|
|isAllDay|Boolean|Legen Sie auf true zurück, wenn das Ereignis den ganzen Tag dauert.|
|isCancelled|Boolean|Auf true festgelegt, wenn das Ereignis abgebrochen wurde.|
|isOrganizer|Boolean|Wenn der Absender der Nachricht der Organisator auch ist true festgelegt.|
|isReminderOn|Boolean|Legen Sie auf true zurück, wenn eine Warnung an den Benutzer über das Ereignis erinnern festgelegt ist.|
|lastModifiedDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Speicherort|[Speicherort](location.md)|Der Speicherort des Ereignisses.|
|Organizer|[Empfänger](recipient.md)|Der Organisator des Ereignisses.|
|originalEndTimeZone|String|Die End-Zeitzone, die festgelegt wurde, wenn das Ereignis erstellt wurde.|
|originalStart|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|originalStartTimeZone|String|Die Start-Zeitzone, die festgelegt wurde, wenn das Ereignis erstellt wurde. |
|Serie|[patternedRecurrence](patternedrecurrence.md)|Die Serie Patern für das Ereignis.|
|reminderMinutesBeforeStart|Int32|Die Anzahl der Minuten, bevor das Ereignis Startzeit, die die Erinnerung Warnung auftritt.|
|responseRequested|Boolean|Legen Sie auf true zurück, wenn der Absender eine Antwort erhalten möchte, wenn das Ereignis angenommen oder abgelehnt wird.|
|responseStatus|[responseStatus](responsestatus.md)|Gibt den Typ der Antwort, die als Antwort auf ein Ereignisnachricht gesendet.|
|Vertraulichkeit|String| Mögliche Werte sind: `Normal`, `Personal`, `Private`, `Confidential`.|
|seriesMasterId|String|Die Kategorien, die das Element zugewiesen.|
|showAs|String|Der Status angezeigt: freien = 0, mit Vorbehalt = 1, beschäftigt = 2, Oof = 3, WorkingElsewhere = 4, Unknown =-1. Possible values are: `Free`, `Tentative`, `Busy`, `Oof`, `WorkingElsewhere`, `Unknown`.|
|Start|[dateTimeTimeZone](datetimetimezone.md)|Das Datum, Uhrzeit und Zeitzone, die das Ereignis beginnt.|
|Betreff|String|Der Text der Betreffzeile des Ereignisses.|
|Typ|String|Den Ereignistyp: SingleInstance = 0, Vorkommen = 1, Ausnahme = 2, SeriesMaster = 3. Mögliche Werte sind: `SingleInstance`, `Occurrence`, `Exception`, `SeriesMaster`.|
|webLink|String|Die URL, die das Ereignis in Outlook Web App zu öffnen.<br/><br/>Das Ereignis wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit dem Browser nicht bereits angemeldet sind.<br/><br/>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung|Die Auflistung von [FileAttachment](fileAttachment.md) und [ItemAttachment](itemAttachment.md) Anlagen für das Ereignis. Navigationseigenschaft. Schreibgeschützt. NULL-Werte zulässt.|
|calendar|[Kalender](calendar.md)|Der Kalender, der das Ereignis enthält. Navigationseigenschaft. Schreibgeschützt.|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der geöffneten Typ Daten Erweiterungen für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|
|Instanzen|[Ereignissammlung](event.md)|Die Instanzen des Ereignisses. Navigationseigenschaft. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "calendar",
    "instances"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.event"
}-->

```json
{
  "attendees": [{"@odata.type": "microsoft.graph.attendee"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "changeKey": "string",
  "createdDateTime": "String (timestamp)",
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "hasAttachments": true,
  "iCalUId": "string",
  "id": "string (identifier)",
  "importance": "String",
  "isAllDay": true,
  "isCancelled": true,
  "isOrganizer": true,
  "isReminderOn": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "organizer": {"@odata.type": "microsoft.graph.recipient"},
  "originalEndTimeZone": "string",
  "originalStart": "String (timestamp)",
  "originalStartTimeZone": "string",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "reminderMinutesBeforeStart": 1024,
  "responseRequested": true,
  "responseStatus": {"@odata.type": "microsoft.graph.responseStatus"},
  "sensitivity": "String",
  "seriesMasterId": "string",
  "showAs": "String",
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "subject": "string",
  "type": "String",
  "webLink": "string",

  "attachments": [ { "@odata.type": "microsoft.graph.attachment" } ],
  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "instances": [ { "@odata.type": "microsoft.graph.event" }]

}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
