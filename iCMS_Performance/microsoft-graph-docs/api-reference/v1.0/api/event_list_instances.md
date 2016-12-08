# <a name="list-instances"></a>Listeninstanzen

Rufen Sie die Instanzen (vorkommen) eines Ereignisses für einen angegebenen Zeitraum. Wenn das Ereignis gehört zu einer `SeriesMaster` Typ; Dies gibt die Vorkommen und Ausnahmen des Ereignisses in den angegebenen Zeitraum.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /groups/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}

GET /me/calendar/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendar/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /groups/<id>/calendar/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}

GET /me/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}

GET /me/calendargroup/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}

GET /me/calendargroups/<id>/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```
## <a name="query-parameters"></a>Abfrageparameter

Geben Sie in der URL der Anforderung die folgenden erforderlichen Abfrageparameter mit Werten.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|startDateTime|String|Das Startdatum und die Uhrzeit des Zeitraums, dargestellt im ISO 8601-Format dar. Beispielsweise "2015-11-08T19:00:00.0000000".|
|endDateTime|String|Das Enddatum und die Uhrzeit des Zeitraums, dargestellt im ISO 8601-Format dar. Beispielsweise "2015-11-08T20:00:00.0000000".|

Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Bevorzugen | string | <Time zone>. Optional, wird angenommen, UTC If absent.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und Sammlung von [Ereignisobjekten im Antworttext](../resources/event.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_instances"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/events/<id>/instances
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
  "description": "List instances",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
