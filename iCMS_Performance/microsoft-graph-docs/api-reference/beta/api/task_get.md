# <a name="get-task"></a>Aufgabe abrufen

Rufen Sie die Eigenschaften und Beziehungen des Task-Objekts ab.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.Read.All Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /tasks/<id>

```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Keine

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [Aufgabe](../resources/task.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_task"
}-->
```http
GET https://graph.microsoft.com/beta/tasks/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.task"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 663
ETag: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

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
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get task",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->