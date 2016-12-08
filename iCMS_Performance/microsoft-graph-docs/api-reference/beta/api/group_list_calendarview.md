# <a name="list-calendarview"></a>Liste calendarView

Eine Liste der Ereignisobjekte abzurufen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Group.Read.All* oder *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
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
| Bevorzugen | string | <Time zone>. Optional, wird angenommen, UTC If absent.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [Ereignis](../resources/event.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_calendarview"
}-->
```http
GET https://graph.microsoft.com/beta/groups/<id>/calendarView
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
  "description": "List calendarView",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
