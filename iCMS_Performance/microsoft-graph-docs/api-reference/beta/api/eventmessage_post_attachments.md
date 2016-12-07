# <a name="create-attachment"></a>Create Attachment

Use this API to create a new Attachment.
## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API:  _Mail.ReadWrite_
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/attachments
POST /users/<id|userPrincipalName>/messages/<id>/attachments
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
  "name": "create_file_attachment_from_eventmessage"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/<id>/attachments
Content-type: application/json

{
  "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
  "name": "name-value",
  "contentType": "contentType-value",
  "isInline": false,
  "contentLocation": "contentLocation-value",
  "contentBytes": "contentBytes-value"
}
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP 201 Created
```


## <a name="example-item-attachment"></a>Example (item attachment)

##### <a name="request"></a>Anforderung

<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_eventmessage"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json

{
  "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
  "name": "name-value",
  "item": "message or event entity"
}
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP 201 Created
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
