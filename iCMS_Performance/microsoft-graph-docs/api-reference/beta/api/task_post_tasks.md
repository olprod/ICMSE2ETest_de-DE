# <a name="create-task"></a>Erstellen der Aufgabe

Verwenden Sie diese API, um eine neue Aufgabe erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /tasks

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Task](../resources/task.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwort Code und [Task](../resources/task.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_task_from_tasks"
}-->
```http
POST https://graph.microsoft.com/beta/tasks
Content-type: application/json
Content-length: 192

{
  "assignedTo": "assignedTo-value",
  "planId": "planId-value",
  "bucketId": "bucketId-value",
  "title": "title-value",
  "orderHint": "orderHint-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Task](../resources/task.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.task"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 663

{
  "@odata.etag": "W/\"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn\"",
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
  "description": "Create task",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
