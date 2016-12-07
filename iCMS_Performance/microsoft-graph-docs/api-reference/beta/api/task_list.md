# <a name="list-tasks"></a>List tasks

Retrieve a list of task* objects.

*Note that filter is required for this method.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Group.Read.All, Group.ReadWrite.All

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /tasks
```
## <a name="required-query-parameters"></a>Required query parameters
|Name|Wert|Beschreibung|
|:---------------|:--------|:-------|
|Filter|Zeichenfolge| Only filtering based on the `createdBy` property is supported. |

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Value should be set to "Bearer (access-token)" |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.
## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and collection of [task](../resources/task.md) objects in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/tasks?$filter=createdBy eq 'me'
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils. 
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 772

{
  "value": [
    {
      "createdBy": "createdBy-value",
      "assignedTo": "assignedTo-value",
      "planId": "planId-value",
      "bucketId": "bucketId-value",
      "title": "title-value",
      "orderHint": "orderHint-value",
      "assigneePriority": "assigneePriority-value",
      "percentComplete": 99,
      "startDateTime": "datetime-value",
      "assignedDateTime": "datetime-value",
      "createdDateTime": "datetime-value",
      "assignedBy": "assignedBy-value",
      "dueDateTime": "datetime-value",
      "hasDescription": true,
      "previewType": "previewType-value",
      "completedDateTime": "datetime-value",
      "appliedCategories": {
      },
      "conversationThreadId": "conversationThreadId-value",
      "id": "id-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List tasks",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
