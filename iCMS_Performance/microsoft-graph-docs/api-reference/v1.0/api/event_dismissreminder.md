# <a name="event-dismissreminder"></a>event: dismissReminder

Dissmiss a reminder that has been triggered.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Calendars.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
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
| Autorisierung  | string  | Bearer <token>. Required. |

## <a name="request-body"></a>Anforderungstextkörper

## <a name="response"></a>Antwort
If successful, this method returns `200, OK` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "event_dismissreminder"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/dismissReminder
```

##### <a name="response"></a>Antwort
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
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
