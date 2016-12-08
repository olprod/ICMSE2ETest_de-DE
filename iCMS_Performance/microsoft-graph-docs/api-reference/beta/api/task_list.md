# <a name="list-tasks"></a>Listenaufgaben

Eine Liste der Aufgabe *-Objekte abzurufen.

* Beachten Sie diesen Filter für diese Methode erforderlich ist.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.Read.All Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /tasks
```
## <a name="required-query-parameters"></a>Erforderliche Abfrageparameter
|Name|Wert|Beschreibung|
|:---------------|:--------|:-------|
|$filter|Zeichenfolge| Nur Filtern basierend auf den `createdBy` Eigenschaft unterstützt wird. |

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von [Task](../resources/task.md) -Objekten im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/tasks?$filter=createdBy eq 'me'
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
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
