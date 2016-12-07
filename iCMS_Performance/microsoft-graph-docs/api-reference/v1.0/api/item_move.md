# <a name="move-an-item"></a>Move - Ein Element verschieben.

Update the parent folder for an item by ID or path. To move an item, you update its parentReference property.

You can also move an item into another folder by updating the **parentInfo.id** or **parentInfo.path** property to the ID of the target parent.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.ReadWrite

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

```http
PATCH /me/drive/items/{item-id}
PATCH /me/drive/root:/{item-path}
PATCH /groups/<id>/drive/<item-id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                         |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Required.                                                                                                                                           |
| if-match      | String | If this request header is included and the eTag (or cTag) provided does not match the current eTag on the folder, a `412 Precondition Failed` response is returned. |


## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the new value for the **parentReference** property. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

**Note:** When moving items to the root of a OneDrive you cannot use the `"id:" "root"` syntax. You either need to use the real ID of the root folder, or use `{"path": "/drive/root"}` for the parent reference.

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and updated [item](../resources/driveitem.md) object in the response body.

## <a name="example"></a>Beispiel
This example moves a folder to a new parent path.

<!-- {
  "blockType": "request",
  "name": "update_item"
}-->
```http
PATCH /drive/items/{item-id}
Content-type: application/json

{
    "name": "new-item-name",
    "parentReference" : {"path": "/drive/root:/Documents"}
}
```

## <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "0123456789abc",
    "name": "BFolder",
    "folder": { "childCount": 3 }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Move item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
