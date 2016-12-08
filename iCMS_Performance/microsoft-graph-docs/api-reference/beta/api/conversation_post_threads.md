# <a name="create-thread"></a>Erstellen von Threads

Erstellen eines neuen Threads in der angegebenen Unterhaltung.

Ein Thread und Post werden erstellt angegeben ist. Verwenden Sie die [Antwort Thread](conversationthread_reply.md) Weitere Beitrag zu diesem Thread. Oder, wenn Sie die Post-ID erhalten möchten, können Sie auch [Antworten](post_reply.md) auf den Beitrag in diesem Thread.

Hinweis: Sie können auch [Starten eine neue Unterhaltung, indem Sie zuerst einen Thread erstellen](group_post_threads.md).

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/conversations/<id>/threads
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ConversationThread](../resources/conversationthread.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [ConversationThread](../resources/conversationthread.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_conversationthread_from_conversation"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/conversations/<id>/threads
Content-type: application/json

{
  "topic": "topic-value",
  "posts": [{
      "body": {
        "contentType": "html",
        "content": "this is body content"
      }
  }]
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ConversationThread](../resources/conversationthread.md) -Objekts.
##### <a name="response"></a>Antwort

Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und die `id` des neuen Threads im Antworttext.
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversationThread"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 346

{
  "id": "thread-id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create thread",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
