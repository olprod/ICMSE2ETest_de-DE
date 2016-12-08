# <a name="list-calendarview"></a>Liste calendarView

Der vorkommen, Ausnahmen und einzelne Instanzen von Ereignissen in einer Kalenderansicht definiert durch ein Zeitbereich, aus dem primären Kalender des Benutzers abrufen `(../me/calendarview)` oder aus einem angegebenen Kalender.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Eines Benutzers oder einer Gruppe als [Kalender](../resources/calendar.md).
```http
GET /me/calendar/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendar/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /groups/<id>/calendar/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

Ein Benutzer [Kalender](../resources/calendar.md) in die Standard- [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}

GET /me/calendarGroup/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendarGroup/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

Ein Benutzer [Kalender](../resources/calendar.md) in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendarGroups/<id>/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

## <a name="query-parameters"></a>Abfrageparameter

Geben Sie in der URL der Anforderung die folgenden erforderlichen Abfrageparameter mit Werten.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|startDateTime|String|Das Startdatum und die Uhrzeit des Zeitraums, dargestellt im ISO 8601-Format dar. Beispielsweise "2015-11-08T19:00:00.0000000".|
|endDateTime|String|Das Enddatum und die Uhrzeit des Zeitraums, dargestellt im ISO 8601-Format dar. Beispielsweise "2015-11-08T20:00:00.0000000".|

Diese Methode unterstützt auch die [Parameter der OData-Abfrage](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
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
  "name": "get_calendarview"
}-->
```http
GET https://graph.microsoft.com/beta/me/calendar/calendarView
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
        "response": "response-value",
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
  "description": "List calendarView",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
