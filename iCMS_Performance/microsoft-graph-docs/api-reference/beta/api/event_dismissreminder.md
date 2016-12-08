# <a name="event-dismissreminder"></a>Ereignis: DismissReminder

Dissmiss eine Erinnerung, die ausgelöst wurde.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/dismissReminder
POST /users/<id | userPrincipalName>/events/<id>/dismissReminder
POST /groups/<id>/events/<id>/dismissReminder

POST /me/calendar/events/<id>/dismissReminder
POST /users/<id | userPrincipalName>/calendar/events/<id>/dismissReminder
POST /groups/<id>/calendar/events/<id>/dismissReminder

POST /me/calendars/<id>/events/<id>/dismissReminder
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/dismissReminder

POST /me/calendargroup/calendars/<id>/events/<id>/dismissReminder
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/dismissReminder

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/dismissReminder
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/dismissReminder
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "event_dismissreminder"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/dismissReminder
```

##### <a name="response"></a>Antwort
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
  "description": "event: dismissReminder",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
