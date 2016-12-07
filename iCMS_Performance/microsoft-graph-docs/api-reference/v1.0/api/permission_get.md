# <a name="get-permission"></a>Get permission

Retrieve the properties and relationships of permission object.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.Read

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/<item-id>/permissions/<id>
GET /me/drive/root:/<item-path>:/permissions/<id>
GET /groups/<group-id>/drive/items/<item-id>/permissions/<id>
```
## <a name="optional-query-parameters"></a>Optionale OData-Abfrageparameter
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.


## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Required. |


## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and [permission](../resources/permission.md) object in the response body.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Here is an example of the request to access a permission on the root folder.

<!-- {
  "blockType": "request",
  "name": "get_permission"
}-->
```http
GET /me/drive/root/permissions/<id>
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 762

{
  "grantedTo": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12"
    }
  },
  "id": "1",
  "roles": [ "write" ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Get permission"
}-->
