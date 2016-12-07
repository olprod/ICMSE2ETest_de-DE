# <a name="message-replyall"></a>message: replyAll

Reply to all recipients of a message. The message is then saved in the Sent Items folder.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Mail.Send*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users/me/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/messages/<id>/replyAll
POST /me/mailFolders/<id>/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/replyAll
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
|Kommentar|String|A comment to include. Can be an empty string.|

## <a name="response"></a>Antwort
If successful, this method returns `202, Accepted` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "message_replyall"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/replyAll
Content-type: application/json
Content-length: 32

{
  "comment": "comment-value"
}
```


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
  "description": "message: replyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
