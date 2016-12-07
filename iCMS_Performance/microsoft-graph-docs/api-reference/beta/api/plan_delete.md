# <a name="delete-plan"></a>Delete plan

Delete plan.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Wählen Sie Group.ReadWrite.All.

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /plans/<id>

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| If-Match | string | Value should be set to the ETag of the object |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.


## <a name="response"></a>Antwort
If successful, this method returns `204, No Content` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "delete_plan"
}-->
```http
DELETE https://graph.microsoft.com/beta/plans/<id>
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
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
  "description": "Delete plan",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->