# <a name="create-attachment"></a>Create Attachment

Use this API to add an [attachment](../resources/attachment.md) to an event. Since there is currently a limit of 4MB on the total size of each REST request, this limits the size of the attachment you can add to under 4MB.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Calendars.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Attachments for an [event](../resources/event.md) in the user's or group's default [calendar](../resources/calendar.md).
```http
POST /me/events/<id>/attachments
POST /users/<id | userPrincipalName>/events/<id>/attachments
POST /groups/<id>/events/<id>/attachments

POST /me/calendar/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendar/events/<id>/attachments
POST /groups/<id>/calendar/events/<id>/attachments
```
Attachments for an [event](../resources/event.md) in a [calendar](../resources/calendar.md) belonging to the user's default [calendarGroup](../resources/calendargroup.md).
```http
POST /me/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments

POST /me/calendargroup/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments
```
Attachments for an [event](../resources/event.md) in a [calendar](../resources/calendar.md) belonging to a user's [calendarGroup](../resources/calendargroup.md).
```http
POST /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |
| contentType | string  | Nature of the data in the body of an entity. Required. |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a JSON representation of [Attachment](../resources/attachment.md) object.


## <a name="response"></a>Antwort
If successful, this method returns `201, Created` response code and [Attachment](../resources/attachment.md) object in the response body.

## <a name="example-file-attachment"></a>Example (file attachment)

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/attachments
Content-type: application/json
Content-length: 142

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "name": "name-value",
  "contentBytes": "contentBytes-value"
}
```

In the request body, supply a JSON representation of [attachment](../resources/attachment.md) object.

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

## <a name="example-item-attachment"></a>Example (item attachment)

##### <a name="request"></a>Anforderung

Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": {}
}
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
