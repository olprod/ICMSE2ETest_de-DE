# <a name="conversation-resource-type"></a>Ressourcentyp Unterhaltung

Eine Unterhaltung ist eine Auflistung von [Threads](conversationthread.md)und ein Thread Beiträge zu diesem Thread enthält. Teilen den gleichen Betreff alle Threads und Beiträge in einer Unterhaltung.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Liste Unterhaltungen](../api/group_list_conversations.md) | [Unterhaltung](conversation.md) -Auflistung |Rufen Sie die Liste der Unterhaltungen in dieser Gruppe.|
|[Erstellen](../api/group_post_conversations.md) |[Unterhaltung](conversation.md)| Erstellen Sie eine neue Unterhaltung durch das Einbeziehen eines Threads und ein Beitrag.|
|[Abrufen der Unterhaltung](../api/conversation_get.md) | [Unterhaltung](conversation.md) |Lesen Sie Eigenschaften und Beziehungen zwischen Conversation-Objekt.|
|[Löschen](../api/conversation_delete.md) | Keine |Conversation-Objekt zu löschen. |
|[Liste Unterhaltung threads](../api/conversation_list_threads.md) |[ConversationThread](conversationthread.md) -Auflistung| Rufen Sie alle Threads in einer gruppenunterhaltung.|
|[Erstellen von Unterhaltungsthreads](../api/conversation_post_threads.md) |[ConversationThread](conversationthread.md) -Auflistung| Erstellen Sie einen Thread in der angegebenen Unterhaltung.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|hasAttachments|Boolean|Gibt an, ob eine der Beiträge in dieser Unterhaltung mindestens eine Anlage enthält.|
|id|String|Eindeutiger Bezeichner der Unterhaltungen. Schreibgeschützt.|
|lastDeliveredDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Vorschau|String|Eine kurze Zusammenfassung aus dem Textkörper des aktuellen Beitrags in dieser Converstaion.|
|Thema|String|Das Thema der Unterhaltung. Diese Eigenschaft kann festgelegt werden, wenn die Unterhaltung wird erstellt, aber nicht aktualisiert werden.|
|uniqueSenders|String-Auflistung|Alle Benutzer, die eine Nachricht zu dieser Unterhaltung gesendet.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Threads|[ConversationThread](conversationthread.md) -Auflistung|Eine Auflistung aller Unterhaltung Threads in der Unterhaltung. Eine Navigationseigenschaft. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "threads"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.conversation"
}-->

```json
{
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "topic": "string",
  "uniqueSenders": ["string"]
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "conversation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
