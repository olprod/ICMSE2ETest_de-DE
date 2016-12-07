# <a name="conversationthread-resource-type"></a>conversationThread resource type
A conversationThread is a collection of [posts](post.md).

The last post's recipients collection is the aggregated recipients of the entire thread. A thread can have a growing collection of recipients. A new thread is created when a recipient is removed from the thread.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[List threads](../api/group_list_threads.md) | [conversationThread](conversationthread.md) collection |Get all the threads of a group.|
|[Create thread](../api/group_post_threads.md) | [conversationThread](conversationthread.md) |Start a new conversation by first creating a thread. A new conversation, conversation thread, and post are created in the group.|
|[Get conversationThread](../api/conversationthread_get.md) | [conversationThread](conversationthread.md) |Get a specific thread that belongs to a group. |
|[Update](../api/conversationthread_update.md) | [conversationThread](conversationthread.md)  |Update conversationThread object. |
|[delete()](../api/conversationthread_delete.md) | Keine |Delete conversationThread object. |
|[reply](../api/conversationthread_reply.md)|Keine|Reply to this thread by creating a new Post entity.|
|[List Posts](../api/conversationthread_list_posts.md) |[post](post.md) collection| Get the posts of the specified thread. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| ReadOnly|
|toRecipients|[recipient](recipient.md) collection|The To: recipients for the thread.|
|ccRecipients|[recipient](recipient.md) collection|The Cc: recipients for the thread.|
|Thema|String|The topic of the conversation. This property can be set when the conversation is created, but it cannot be updated.||
|hasAttachments|Boolean|Indicates whether any of the posts within this thread has at least one attachment.|
|lastDeliveredDateTime|DateTimeOffset|The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`|
|uniqueSenders|String collection|All the users that sent a message to this thread.|
|Vorschau|String|A short summary from the body of the latest post in this converstaion.|
|isLocked|Boolean|Indicates if the thread is locked.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|posts|[post](post.md) collection| Read-only. Nullable.|


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "posts"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.conversationThread"
}-->

```json
{
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "hasAttachments": true,
  "id": "string (identifier)",
  "isLocked": true,
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "topic": "string",
  "uniqueSenders": ["string"]
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "conversationThread resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
