# <a name="get-taskboardtaskformat"></a>Get taskBoardTaskFormat

Retrieve the properties and relationships of taskboardtaskformat object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Group.Read.All, Group.ReadWrite.All

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /tasks/<id>/bucketTaskBoardFormat
GET /tasks/<id>/progressTaskBoardFormat
GET /tasks/<id>/assignedToTaskBoardFormat
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
If successful, this method returns a `200 OK` response code and [taskBoardTaskFormat](../resources/taskboardtaskformat.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "get_taskboardtaskformat"
}-->
```http
GET https://graph.microsoft.com/beta/tasks/<id>/bucketTaskBoardFormat
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.taskboardtaskformat"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 80

{
  "type": "type-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get taskBoardTaskFormat",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->