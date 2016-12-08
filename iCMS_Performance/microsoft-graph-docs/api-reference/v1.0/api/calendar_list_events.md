# <a name="list-events"></a>List-Ereignisse

Abrufen einer Liste von Ereignissen in einem Kalender.  Die Liste enthält Einzelinstanz Besprechungen und Series-Master.

Wenn expanded-Ereignisinstanzen erhalten möchten, können Sie [die Kalenderansicht erhalten möchten](calendar_list_calendarview.md), oder [Instanzen eines Ereignisses abgerufen](event_list_instances.md).

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Eines Benutzers oder einer Gruppe als [Kalender](../resources/calendar.md).
```http
GET /me/calendar/events
GET /users/<id | userPrincipalName>/calendar/events
GET /groups/<id>/calendar/events
```
Ein Benutzer [Kalender](../resources/calendar.md) in die Standard- [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendars/<id>/events

GET /me/calendarGroup/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendarGroup/calendars/<id>/events
```
Ein Benutzer [Kalender](../resources/calendar.md) in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendarGroups/<id>/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>/events
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Bevorzugen  | Outlook.TimeZone="Eastern Normalzeit". Optional Hiermit können Sie die Zeitzone für die Anfangs- und Endzeiten in der Antwort angeben. Wenn nicht angegeben, wird die Antwort in UTC zurückgegeben. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und Sammlung von [Ereignisobjekten im Antworttext](../resources/event.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_events"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/calendar/events
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.event",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 354

{
  "value": [
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
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List events",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
