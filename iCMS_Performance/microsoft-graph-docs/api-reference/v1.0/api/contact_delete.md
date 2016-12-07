# <a name="delete-contact"></a>Delete contact

Delete a contact.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Contacts.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
A [contact](../resources/contact.md) from a user's default [contactFolder](../resources/contactfolder.md).
```http
DELETE /me/contacts/<id>
DELETE /users/<id | userPrincipalName>/contacts/<id>
```
A [contact](../resources/contact.md) from a user's top level [contactFolder](../resources/contactfolder.md).
```http
DELETE /me/contactFolders/<id>/contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
A [contact](../resources/contact.md) contained in a child folder of a [contactFolder](../resources/mailfolder.md). The example below shows one level of nesting, but a contact can be located in a child of a child and so on.
```http
DELETE /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Required.  |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.


## <a name="response"></a>Antwort
If successful, this method returns `204, No Content` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
AnforderungsheaderNachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "delete_contact"
}-->
```http
DELETE https://graph.microsoft.com/v1.0/me/contacts/<id>
```
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
