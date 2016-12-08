# <a name="event-snoozereminder"></a>Ereignis: SnoozeReminder

Verschieben Sie eine Erinnerung bis zu einem neuen Zeitpunkt.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/snoozeReminder
POST /users/<id | userPrincipalName>/events/<id>/snoozeReminder
POST /groups/<id>/events/<id>/snoozeReminder

POST /me/calendar/events/<id>/snoozeReminder
POST /users/<id | userPrincipalName>/calendar/events/<id>/snoozeReminder
POST /groups/<id>/calendar/events/<id>/snoozeReminder

POST /me/calendars/<id>/events/<id>/snoozeReminder
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/snoozeReminder

POST /me/calendargroup/calendars/<id>/events/<id>/snoozeReminder
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/snoozeReminder

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/snoozeReminder
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/snoozeReminder
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|newReminderTime|DateTimeTimeZone|Neues Datum und Uhrzeit die Erinnerung ausgelöst.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "event_snoozereminder"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/snoozeReminder
Content-type: application/json
Content-length: 97

{
  "newReminderTime": {
    "dateTime": "dateTime-value",
    "timeZone": "timeZone-value"
  }
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: snoozeReminder",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
