# <a name="event-cancel"></a>event: cancel

This action allows the organizer of a meeting to send a cancellation message and cancel the event. 

The action moves the event to the Deleted Items folder. The organizer can also cancel an occurrence of a recurring meeting by providing the occurrence event ID. An attendee calling this action gets an error (HTTP 400 Bad Request), with the following error message:

"Your request can't be completed. You need to be an organizer to cancel a meeting."

This action differs from [Delete](event_delete.md) in that **Cancel** is available to only the organizer, and lets the organizer send a custom message to the attendees about the cancellation.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Calendars.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/cancel
POST /users/<id | userPrincipalName>/events/<id>/cancel
POST /groups/<id>/events/<id>/cancel

POST /me/calendar/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendar/events/<id>/cancel
POST /groups/<id>/calendar/events/<id>/cancel

POST /me/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/cancel

POST /me/calendargroup/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/cancel

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/cancel
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |
| contentType | string  | Nature of the data in the body of an entity. Required. |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, provide a JSON object with the following parameters.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Kommentar|String|A comment about the cancellation sent to all the attendees. Optional.|

## <a name="response"></a>Antwort
If successful, this method returns `202, Accepted` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "event_cancel"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/cancel
Content-type: application/json

{
  "Comment": "Cancelling for this week due to all hands"
}
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: cancel",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
