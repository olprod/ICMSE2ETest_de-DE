# <a name="create-bucket"></a>Create bucket

Use this API to create a new bucket.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Wählen Sie Group.ReadWrite.All.

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /buckets

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Value should be set to "Bearer (access-token)" |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a JSON representation of [bucket](../resources/bucket.md) object.


## <a name="response"></a>Antwort
If successful, this method returns `201, Created` response code and [bucket](../resources/bucket.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_bucket_from_buckets"
}-->
```http
POST https://graph.microsoft.com/beta/buckets
Content-type: application/json
Content-length: 88

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value"
}
```
In the request body, supply a JSON representation of [bucket](../resources/bucket.md) object.
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.bucket"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 108

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create bucket",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->