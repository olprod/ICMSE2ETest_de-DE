# <a name="update-message"></a>Update message

Update the properties of message object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Mail.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id | userPrincipalName>/messages/<id>
PATCH /me/mailFolders/<id>/messages/<id>
PATCH /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |
| contentType | string  | Nature of the data in the body of an entity. Required. |
## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed. Writable/Updatable properties are

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bccRecipients|Recipient|The Bcc recipients for the message. Updatable only if IsDraft = true.|
|Kategorien|String collection|The categories associated with the message.|
|ccRecipients|Recipient collection|The Cc recipients for the message. Updatable only if IsDraft = true.|
|from|Recipient|The mailbox owner and sender of the message. Updatable only if IsDraft = true.|
|Importance|String|The importance of the message. Possible values are: `Low`, `Normal`, `High`.|
|inferenceClassification | String | The classification of the message for the user, based on inferred relevance or importance, or on an explicit override. Possible values are: `focused` or `other`. |
|Eigenschaft internetMessageId |String |The message ID in the format specified by [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Updatable only if IsDraft = true.|
|isRead|Boolean|True/False. Gibt an, ob die Nachricht als "Gelesen" markiert wurde.|
|replyTo|Recipient collection|The email addresses to use when replying. Updatable only if IsDraft = true.|
|sender|Recipient|The account that is actually used to generate the message. Updatable only if IsDraft = true.|
|toRecipients|Recipient collection|The To recipients for the message. Updatable only if IsDraft = true.|
|body|ItemBody|The body of the message. Updatable only if IsDraft = true.|
|isDeliveryReceiptRequested|Boolean|Indicates whether a read receipt is requested for the message.|
|isReadReceiptRequested|Boolean|Indicates whether a read receipt is requested for the message.|
|Betreff|String|The subject of the message. Updatable only if IsDraft = true.|

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and updated [message](../resources/message.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "update_message"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/messages/<id>
Content-type: application/json
Content-length: 248

{
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "inferenceClassification": "other"
}
```
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 248

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value",
  "inferenceClassification": "other"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update message",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
