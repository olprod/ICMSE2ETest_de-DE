# <a name="delete-permission"></a>Delete permission

Delete a permission. Only permissions that are not inherited can be deleted. The **inheritedFrom** property must be null. Applications can only delete permissions they have created.


## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.ReadWrite

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
DELETE /me/drive/root/permissions/<id>
DELETE /me/drive/items/<id>/permissions/<id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Required.                                                                                                                                                                         |
| if-match      | string | If this request header is included and the eTag (or cTag) provided does not match the current tag on the item, a `412 Precondition Failed` response is returned and the item will not be deleted. |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns `204, No Content` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

<!-- {
  "blockType": "request",
  "name": "delete_permission"
}-->
```http
DELETE /me/drive/root/permissions/<id>
```

##### <a name="response"></a>Antwort

Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

<!-- {
  "blockType": "response",
  "truncated": false
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Delete permission"
}-->
