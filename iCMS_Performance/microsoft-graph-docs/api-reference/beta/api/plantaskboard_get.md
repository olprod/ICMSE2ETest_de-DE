# <a name="get-plantaskboard"></a>Get planTaskBoard

Retrieve the properties and relationships of plantaskboard object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Group.Read.All, Group.ReadWrite.All

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /plans/<id>/bucketTaskBoard
GET /plans/<id>/progressTaskBoard
GET /plans/<id>/assignedToTaskBoard
```
## <a name="optional-query-parameters"></a>Optionale OData-Abfrageparameter
Keine

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Value should be set to "Bearer (access-token)" |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.
## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and [planTaskBoard](../resources/plantaskboard.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "get_plantaskboard"
}-->
```http
GET https://graph.microsoft.com/beta/plans/<id>/bucketTaskBoard
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plantaskboard"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 46

{
  "type": "type-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get planTaskBoard",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->