# <a name="create-conversation"></a>Erstellen der Unterhaltung

Erstellen Sie eine neue Unterhaltung durch das Einbeziehen eines Threads und ein Beitrag. 

Verwenden Sie [Antwort Thread](conversationthread_reply.md) oder weitere Beitrag zu dieser Unterhaltung im [Beitrag Antworten](post_reply.md) .
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/conversations
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/json  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der [Conversation](../resources/conversation.md) -Objekt mit einer [ConversationThread](../resources/conversationThread.md) und einer [Buchen](../resources/post.md).


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Unterhaltung](../resources/conversation.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_conversation_from_group"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/conversations
Content-type: application/json

{
  "topic": "New Conversation Topic",
  "threads": [{
    "posts": [{
      "body": {
        "contentType": "html",
        "content": "this is body content"
      },
      "newParticipants": [{
        "emailAddress": {
          "name": "Alex Darrow",
          "address": "alexd@contoso.com"
        }
      }]
    }]
  }]
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversation"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 201

{
  "topic": "topic-value",
  "hasAttachments": true,
  "lastDeliveredDateTime": "datetime-value",
  "uniqueSenders": [
    "uniqueSenders-value"
  ],
  "preview": "preview-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Conversation",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->