# <a name="conversationthread-resource-type"></a>Ressourcentyp conversationThread
Eine ConversationThread ist eine Auflistung von [Blogbeiträgen](post.md).

Im letzten Beitrag Recipients-Auflistung ist die aggregierten Empfänger des gesamten Threads. Ein Thread kann eine wachsende Sammlung von Empfängern verfügen.
Ein neuer Thread wird erstellt, sobald der Thread ein Empfänger aufgehoben wird.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Liste threads](../api/group_list_threads.md) | [ConversationThread](conversationthread.md) -Auflistung |Rufen Sie alle Threads einer Gruppe.|
|[Erstellen von Threads](../api/group_post_threads.md) | [conversationThread](conversationthread.md) |Starten einer neuen Unterhaltung durch einen Thread zuerst zu erstellen. Einer neuen Unterhaltung Unterhaltungsthreads und Post werden in der Gruppe erstellt werden.|
|[Abrufen von conversationThread](../api/conversationthread_get.md) | [conversationThread](conversationthread.md) |Rufen Sie einen bestimmten Thread, der zu einer Gruppe gehört. |
|[Update](../api/conversationthread_update.md) | [conversationThread](conversationthread.md)  |ConversationThread-Objekt zu aktualisieren. |
|[Löschen](../api/conversationthread_delete.md) | Keine |Löschen Sie ConversationThread Objekt. |
|[Antwort](../api/conversationthread_reply.md)|Keine|Antworten Sie auf dieser Thread durch Erstellen einer neuen Post-Entität.|
|[Liste Beiträge](../api/conversationthread_list_posts.md) |[POST](post.md) -Auflistung| Rufen Sie die Beiträge des angegebenen Threads. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| Schreibgeschützt.|
|toRecipients|[Empfänger](recipient.md) -Auflistung|Die an: Empfänger des Threads.|
|ccRecipients|[Empfänger](recipient.md) -Auflistung|Die Cc: Empfänger des Threads.|
|Thema|String|Das Thema der Unterhaltung. Diese Eigenschaft kann festgelegt werden, wenn die Unterhaltung wird erstellt, aber nicht aktualisiert werden.||
|hasAttachments|Boolean|Gibt an, ob eines der Beiträgen in diesem Thread hat mindestens eine Anlage.|
|lastDeliveredDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|uniqueSenders|String-Auflistung|Alle Benutzer, die dieser Thread eine Nachricht an.|
|Vorschau|String|Eine kurze Zusammenfassung aus dem Textkörper des aktuellen Beitrags in dieser Converstaion.|
|isLocked|Boolean|Gibt an, ob der Thread gesperrt ist.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Blogbeiträge|[POST](post.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

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
