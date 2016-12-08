# <a name="update-event"></a>Updateereignis

Aktualisieren der Eigenschaften des Event-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/events/<id>
PATCH /users/<id | userPrincipalName>/events/<id>
PATCH /groups/<id>/events/<id>

PATCH /me/calendar/events/<id>
PATCH /users/<id | userPrincipalName>/calendar/events/<id>
PATCH /groups/<id>/calendar/events/<id>

PATCH /me/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendars/<id>/events/<id>

PATCH /me/calendargroup/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>

PATCH /me/calendargroups/<id>/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Teilnehmer|Teilnehmer|Die Auflistung der Teilnehmer für das Ereignis.|
|body|ItemBody|Der Textkörper der Nachricht mit dem Ereignis verknüpft ist.|
|Kategorien|String|Die Kategorien, die mit dem Ereignis verknüpft ist.|
|Ende|DateTimeTimeZone|Das Datum und die Uhrzeit, die das Ereignis endet.<br/><br/>Standardmäßig ist die Endzeit in UTC. Sie können eine optionale Zeitzone in EndTimeZone angeben, die Endzeit in diese Zeitzone express und einen Uhrzeit-Offset von UTC enthalten. Beachten Sie, dass bei Verwendung von EndTimeZone Sie einen Wert für StartTimeZone sowie angeben müssen.<br/><br/>Dieses Beispiel gibt an, 25 Februar 2015 9:34 pm Pacific Standard Time: "2015-02-25T21:34:00-08:00". |
|Bedeutung|String|Die Bedeutung des Ereignisses: Niedrig = 0 Normal = 1, hoch = 2. Mögliche Werte sind: `Low`, `Normal`, `High`.|
|isAllDay|Boolean|Legen Sie auf true zurück, wenn das Ereignis den ganzen Tag dauert.|
|isReminderOn|Boolean|Legen Sie auf true zurück, wenn eine Warnung an den Benutzer über das Ereignis erinnern festgelegt ist.|
|Speicherort|Location|Der Speicherort des Ereignisses.|
|Serie|PatternedRecurrence|Die Serie Patern für das Ereignis.|
|reminderMinutesBeforeStart|Int32|Die Anzahl der Minuten, bevor das Ereignis Startzeit, die die Erinnerung Warnung auftritt.|
|responseRequested|Boolean|Legen Sie auf true zurück, wenn der Absender eine Antwort erhalten möchte, wenn das Ereignis angenommen oder abgelehnt wird.|
|Vertraulichkeit|String| Mögliche Werte sind: `Normal`, `Personal`, `Private`, `Confidential`.|
|showAs|String|Der Status angezeigt: freien = 0, mit Vorbehalt = 1, beschäftigt = 2, Oof = 3, WorkingElsewhere = 4, unbekannt =-1. Possible values are: `Free`, `Tentative`, `Busy`, `Oof`, `WorkingElsewhere`, `Unknown`.|
|Start|DateTimeTimeZone|Die Anfangszeit des Ereignisses. <br/><br/>Standardmäßig ist die Startzeit in UTC. Sie können eine optionale Zeitzone in StartTimeZone angeben, die Startzeit in dieser Zeitzone express und umfassen einen Uhrzeit-Offset von UTC. Beachten Sie, dass bei Verwendung von StartTimeZone Sie einen Wert für EndTimeZone sowie angeben müssen.<br/><br/>Dieses Beispiel gibt an, 25 Februar 2015 7:34 pm Pacific Standard Time: "2015-02-25T19:34:00-08:00".  |
|Betreff|String|Der Text der Betreffzeile des Ereignisses.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und updated- [Ereignis](../resources/event.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_event"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/events/<id>
Content-type: application/json
Content-length: 285

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "iCalUId": "iCalUId-value",
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.event"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 285

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "iCalUId": "iCalUId-value",
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
