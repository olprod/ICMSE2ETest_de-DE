# <a name="create-event"></a>Ereignis erstellen

Verwenden Sie diese API, um ein neues Ereignis in die Standardvorlage oder den angegebenen Kalender zu erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Eines Benutzers oder einer Gruppe als [Kalender](../resources/calendar.md).
```http
POST /me/calendar/events
POST /users/<id | userPrincipalName>/calendar/events
POST /groups/<id>/calendar/events
```
Ein Benutzer [Kalender](../resources/calendar.md) in die Standard- [CalendarGroup](../resources/calendargroup.md).
```http
POST /me/calendars/<id>/events
POST /users/<id | userPrincipalName>/calendars/<id>/events

POST /me/calendarGroup/calendars/<id>/events
POST /users/<id | userPrincipalName>/calendarGroup/calendars/<id>/events
```
Ein Benutzer [Kalender](../resources/calendar.md) in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
POST /me/calendarGroups/<id>/calendars/<id>/events
POST /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>/events
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Event](../resources/event.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [Event](../resources/event.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_event_from_calendar"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/calendar/events
Content-type: application/json
Content-length: 285

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Event](../resources/event.md) -Objekts.
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
  "description": "Create Event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
