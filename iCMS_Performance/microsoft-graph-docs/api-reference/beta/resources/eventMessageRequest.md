# <a name="eventmessagerequest-resource-type"></a>Ressourcentyp eventMessageRequest

Eine Nachricht, die eine Besprechungsanfrage darstellt.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "event",
    "extensions",
    "previousLocation",
    "previousStartDateTime",
    "previousEndDateTime"
  ],
  "@odata.type": "microsoft.graph.eventmessagerequest"
}-->

```json
{
  "bccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "changeKey": "string",
  "conversationId": "string",
  "createdDateTime": "String (timestamp)",
  "endDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isOutOfDate": "Boolean",
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "meetingMessageType": "microsoft.graph.meetingMessageType",
  "parentFolderId": "string",
  "previousEndDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "previousLocation": {"@odata.type": "microsoft.graph.location"},
  "previousStartDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "receivedDateTime": "String (timestamp)",
  "recurrence": {"@odata.type": "microsoft.graph.patternedrecurrence"},
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "startDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "type": "string",
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bccRecipients|[Empfänger](recipient.md) -Auflistung|Bcc: Empfänger der Nachricht.|
|body|[itemBody](itembody.md)|Der Textkörper der Nachricht.|
|bodyPreview|String|Die ersten 255 Zeichen des Nachrichtentexts.|
|Kategorien|Zeichenfolgenauflistung|Die Kategorien, die Nachricht zugeordnet.|
|ccRecipients|[Empfänger](recipient.md) -Auflistung|Die Cc: Empfänger der Nachricht.|
|changeKey|String|Die Version der Nachricht.|
|conversationId|String|Die ID der e-Mail-Unterhaltung gehört.|
|createdDateTime|DateTimeOffset|Datum und Uhrzeit der Erstellung die Nachricht.|
|endDateTime|[DateTimeTimeZone](datetimetimezone.md)|Die Endzeit der angeforderten Besprechung.|
|from|[Empfänger](recipient.md)|Der Postfachbesitzer und der Absender der Nachricht.|
|hasAttachments|Boolean|Gibt an, ob die Nachricht Anlagen enthält.|
|id|String|Schreibgeschützt.|
|Bedeutung|String| Die Priorität der Nachricht: `Low`, `Normal`, `High`.|
|inferenceClassification|String| Mögliche Werte sind: `Focused`, `Other`.|
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isDraft|Boolean|Gibt an, ob die Nachricht ein Entwurf ist. Eine Nachricht ist Entwurf, falls noch nicht erhalten wurden.|
|isOutOfDate|Boolean|Gibt an, ob diese Besprechungsanfrage von einer neueren Anforderung veralteten vorgenommen wurden.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|lastModifiedDateTime|DateTimeOffset|Das Datum und Uhrzeit der letzten Änderung die Nachricht.|
|Speicherort|[Speicherort](location.md)|Der Speicherort der angeforderten Besprechung.|
|meetingMessageType|String| Der Typ der ereignismeldung: `None`, `MeetingRequest`, `MeetingCancelled`, `MeetingAccepted`, `MeetingTenativelyAccepted`, `MeetingDeclined`.|
|parentFolderId|String|Der eindeutige Bezeichner für die Meldung übergeordneten MailFolder.|
|previousEndDateTime|[DateTimeTimeZone](datetimetimezone.md)|Die vorherigen Endzeit der angeforderten Besprechung.|
|previousLocation|[Speicherort](location.md)|Die vorherige Position der angeforderten Besprechung.|
|previousStartDateTime|[DateTimeTimeZone](datetimetimezone.md)|Die vorherigen Anfangszeit der angeforderten Besprechung.|
|receivedDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht empfangen wurde.|
|Serie|[PatternedRecurrence](patternedrecurrence.md)|Das Serienmuster der angeforderten Besprechung.|
|replyTo|[Empfänger](recipient.md) -Auflistung|Die e-Mail-Adressen beim Antworten verwenden.|
|Absender|[Empfänger](recipient.md)|Das Konto, das tatsächlich verwendet wird, um die Nachricht zu generieren.|
|sentDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht gesendet wurde.|
|startDateTime|[DateTimeTimeZone](datetimetimezone.md)|Die Anfangszeit der angeforderten Besprechung.|
|Betreff|String|Der Betreff der Nachricht.|
|toRecipients|[Empfänger](recipient.md) -Auflistung|So: Empfänger der Nachricht.|
|Typ|String|Die Art der angeforderten Besprechung: `singleInstance`, `occurence`, `exception`, `seriesMaster`.|
|uniqueBody|[itemBody](itembody.md)|Der Teil des Textkörpers der Nachricht, die für die aktuelle Nachricht eindeutig ist.|
|webLink|String|Die URL zum Öffnen der Nachricht in Outlook Web App.<br><br>Sie können ein Argument Ispopout anfügen, an das Ende der URL zu ändern, wie die Nachricht angezeigt wird. Wenn Ispopout nicht vorhanden ist oder wenn es auf 1 festgelegt ist, wird die Nachricht in einem Popout-Fenster angezeigt. Wenn Ispopout auf 0 festgelegt ist, wird im Browser in der Outlook Web App-Bereich prüfen die Nachricht angezeigt.<br><br>Die Nachricht wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit dem Browser nicht bereits angemeldet sind.<br><br>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|
|Ereignis|[Ereignis](event.md)| Das Ereignis ereignismeldung zugeordnet ist. Die Annahme für Teilnehmer oder raumressourcen ist, dass der Kalenderautomatik festgelegt ist, im Kalender mit ein Ereignis, wenn einer Besprechungsanfrage, dass Ereignisnachrichten eintreffen automatisch aktualisiert wird. Navigationseigenschaft.  Schreibgeschützt.|
|Erweiterungen|[Erweiterungssammlung](extension.md)| Schreibgeschützt. NULL-Werte zulässt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von eventMessage](../api/eventmessage_get.md) | [eventMessage](eventmessage.md) |Lesen Sie Eigenschaften und Beziehungen des EventMessage-Objekts.|
|[Erstellen der Anlage](../api/eventmessage_post_attachments.md) |[Anlage](attachment.md)| Erstellen Sie eine neue Anlage, indem Sie das Veröffentlichen in der Attachments-Auflistung.|
|[Anlagen auflisten](../api/eventmessage_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Auflistung des Attachment-Objekt.|
|[Liste-Erweiterungen](../api/eventmessage_list_extensions.md) |[Erweiterungssammlung](extension.md)| Rufen Sie eine Auflistung der Erweiterung-Objekt.|
|[Update](../api/eventmessage_update.md) | [eventMessage](eventmessage.md)  |Aktualisieren Sie EventMessage-Objekts. |
|[Löschen](../api/eventmessage_delete.md) | Keine |EventMessage-Objekt zu löschen. |
|[Kopie](../api/message_copy.md)|[Nachricht](message.md)||
|[createForward](../api/message_createforward.md)|[Nachricht](message.md)||
|[createReply](../api/message_createreply.md)|[Nachricht](message.md)||
|[createReplyAll](../api/message_createreplyall.md)|[Nachricht](message.md)||
|[Weiterleiten](../api/message_forward.md)|Keine|Leitet eine Nachricht an. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Verschieben](../api/message_move.md)|[Nachricht](message.md)|Verschieben der Nachricht in einem MailFolder.|
|[Antwort](../api/message_reply.md)|Keine|Replys an den Absender einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[replyAll](../api/message_replyall.md)|Keine|Antworten Sie an alle Empfänger einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Senden](../api/message_send.md)|Keine|Sendet einen zuvor erstellte Nachricht Entwurf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "eventMessageRequest resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->