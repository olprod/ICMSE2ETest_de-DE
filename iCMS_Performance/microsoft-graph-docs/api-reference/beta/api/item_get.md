# <a name="get-a-driveitem-resource"></a>Get a driveItem resource

Retrieve the metadata for a driveItem in a drive by file system path or unique id.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/<item-id>
GET /me/drive/root:/<item-path>
GET /groups/<group-id>/drive/items/<item-id>
```

## <a name="optional-query-parameters"></a>Optionale OData-Abfrageparameter
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Wert  | Beschreibung                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Required.                                                                                                                                |
| if-none-match | String | If this request header is included and the eTag (or cTag) provided matches the current tag on the file, an `HTTP 304 Not Modified` response is returned. |


## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and [item](../resources/driveitem.md) object in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "get_item"
}-->
```
GET /me/drive/items/{item-id}
```

##### <a name="response"></a>Antwort
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
  "createdBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "createdDateTime": "2016-03-21T20:01:37Z",
  "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
  "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
  "file": {  },
  "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
  "lastModifiedBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "lastModifiedDateTime": "2016-03-21T20:01:37Z",
  "name": "OneDrive Graph API.docx",
  "parentReference": {
      "driveId": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "id": "01NKDM7HN6Y2GOVW7725BZO354PWSELRRZ",
      "path": "/drive/root:"
  },
  "size": 31679,
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/OneDrive%20Graph%20API.docx"
}
```

## <a name="notes"></a>Hinweise

You can use the [`expand`](https://dev.onedrive.com/odata/optional-query-parameters.htm#expanding-collections) query string parameter to include the children of an item in the same call as retrieving the metadata of an item.

## <a name="head-requests"></a>HEAD requests

In most cases, a HEAD request will behave the same way as a GET request. There are a couple differences:

1. HEAD requests will only return the corresponding GET request's headers. This is standard practice for a HEAD response.
2. HEAD requests will not automatically provision a [special folder](../resources/specialfolder.md). Instead, if a special folder is not present, a `404` error will be returned.

In this example, you can see that requesting the root resource of a drive will respond with simply `200 OK`.

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

<!-- {"blockType": "request", "name": "head-root"} -->
```
HEAD /me/drive/root
Accept: application/json
```

## <a name="response"></a>Antwort

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true} -->
```
HTTP/1.1 200 OK
Content-Type: application/json
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Get item"
}-->
