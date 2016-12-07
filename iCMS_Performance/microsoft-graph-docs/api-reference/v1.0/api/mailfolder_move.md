# <a name="mailfolder-move"></a>mailFolder: move

Move a mailfolder and its contents to another mailfolder.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Mail.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/mailFolders/<id>/move
POST /users/<id | userPrincipalName>/mailFolders/<id>/move
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Required.  |
| contentType  | application/json. Required.  |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, provide a JSON object with the following parameters.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|destinationId|String|The folder ID, or the *Inbox*, *Drafts*, *SentItems*, or *DeletedItems* well-known folder name.|

## <a name="response"></a>Antwort
If successful, this method returns `200, OK` response code and [MailFolder](../resources/mailfolder.md) object in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "mailfolder_move"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/mailFolders/<id>/move
Content-type: application/json
Content-length: 44

{
  "destinationId": "destinationId-value"
}
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.mailFolder"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 179

{
  "displayName": "displayName-value",
  "parentFolderId": "parentFolderId-value",
  "childFolderCount": 99,
  "unreadItemCount": 99,
  "totalItemCount": 99,
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "mailFolder: move",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
