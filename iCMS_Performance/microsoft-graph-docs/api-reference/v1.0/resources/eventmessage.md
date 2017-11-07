# <a name="eventmessage-resource-type"></a>Ressourcentyp eventMessage

Eine Nachricht, die eine Besprechung darstellt anfordern, Besprechung absagen Nachricht, Besprechung Nachricht annehmen, Meeting Nachricht mit Vorbehalt annehmen oder Besprechung Nachricht abgelehnt.

Ein EventMessage befindet sich in der Regel im Ordner Posteingang, wenn es als die Ergebnisse der entweder ein Ereignis Organisator eine Besprechung erstellen oder durch einen Teilnehmer reagieren auf eine Besprechungsanfrage ankommt. Sie wirken sich auf Ereignisnachrichten auf die gleiche Weise, dass Sie auf die Nachricht mit geringfügige Unterschiede in der folgenden Tabelle beschriebenen fungieren.


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von eventMessage](../api/eventmessage_get.md) | [eventMessage](eventmessage.md) |Lesen Sie Eigenschaften und Beziehungen des EventMessage-Objekts.|
|[Anlagen auflisten](../api/message_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Auflistung des Attachment-Objekt.|
|[Update](../api/eventmessage_update.md) | [eventMessage](eventmessage.md)  |Aktualisieren Sie EventMessage-Objekts. |
|[Löschen](../api/message_delete.md) | Keine |EventMessage-Objekt zu löschen. |
|[Kopie](../api/message_copy.md)|[Nachricht](message.md)|Kopieren einer Nachricht in einen Ordner.|
|[createForward](../api/message_createforward.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder die Nachricht weiterleiten. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReply](../api/message_createreply.md)|[Nachricht](message.md)|Erstellen Sie einen Entwurf für die Antwortnachricht. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReplyAll](../api/message_createreplyall.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder allen Antworten-Nachricht. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[Weiterleiten](../api/message_forward.md)|Keine|Weiterleiten einer Nachricht an. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Verschieben](../api/message_move.md)|[Nachricht](message.md)|Verschieben von Nachrichten in einen Ordner. Dadurch wird eine neue Kopie der Nachricht im Zielordner erstellt.|
|[Antwort](../api/message_reply.md)|Keine|Antworten Sie an den Absender einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[replyAll](../api/message_replyall.md)|Keine|Antworten Sie an alle Empfänger einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Senden](../api/message_send.md)|Keine|Sendet einen zuvor erstellte Nachricht Entwurf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine open Typ Daten Erweiterung und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|


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
|from|[Empfänger](recipient.md)|Der Postfachbesitzer und der Absender der Nachricht.|
|hasAttachments|Boolean|Gibt an, ob die Nachricht Anlagen enthält.|
|id|String||
|Bedeutung|String| Die Priorität der Nachricht: `Low`, `Normal`, `High`.|
|internetMessageId |String |Die Nachrichten-ID im Format durch [RFC2822](http://www.ietf.org/rfc/rfc2822.txt)angegeben. |
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isDraft|Boolean|Gibt an, ob die Nachricht ein Entwurf ist. Eine Nachricht ist Entwurf, falls noch nicht erhalten wurden.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|lastModifiedDateTime|DateTimeOffset|Das Datum und Uhrzeit der letzten Änderung die Nachricht.|
|meetingMessageType|String| Der Typ der ereignismeldung: `None`, `MeetingRequest`, `MeetingCancelled`, `MeetingAccepted`, `MeetingTenativelyAccepted`, `MeetingDeclined`.|
|parentFolderId|String|Der eindeutige Bezeichner für die Meldung übergeordneten MailFolder.|
|receivedDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht empfangen wurde.|
|replyTo|[Empfänger](recipient.md) -Auflistung|Die e-Mail-Adressen beim Antworten verwenden.|
|Absender|[Empfänger](recipient.md)|Das Konto, das tatsächlich verwendet wird, um die Nachricht zu generieren.|
|sentDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht gesendet wurde.|
|Betreff|String|Der Betreff der Nachricht.|
|toRecipients|[Empfänger](recipient.md) -Auflistung|So: Empfänger der Nachricht.|
|uniqueBody|[itemBody](itembody.md)|Der Teil des Textkörpers der Nachricht, die für die aktuelle Nachricht eindeutig ist.|
|webLink|String|Die URL zum Öffnen der Nachricht in Outlook Web App.<br><br>Sie können ein Argument Ispopout anfügen, an das Ende der URL zu ändern, wie die Nachricht angezeigt wird. Wenn Ispopout nicht vorhanden ist oder wenn es auf 1 festgelegt ist, wird die Nachricht in einem Popout-Fenster angezeigt. Wenn Ispopout auf 0 festgelegt ist, wird im Browser in der Outlook Web App-Bereich prüfen die Nachricht angezeigt.<br><br>Die Nachricht wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit dem Browser nicht bereits angemeldet sind.<br><br>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|


## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|
|Ereignis|[Ereignis](event.md)| Das Ereignis ereignismeldung zugeordnet ist. Die Annahme für Teilnehmer oder raumressourcen ist, dass der Kalenderautomatik festgelegt ist, im Kalender mit ein Ereignis, wenn einer Besprechungsanfrage, dass Ereignisnachrichten eintreffen automatisch aktualisiert wird. Navigationseigenschaft.  Schreibgeschützt.|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der geöffneten Typ Daten Erweiterungen für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource  

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "event"
  ],
  "@odata.type": "microsoft.graph.eventmessage"
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
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "internetMessageId": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "meetingMessageType": "String",
  "parentFolderId": "string",
  "receivedDateTime": "String (timestamp)",
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "eventMessage resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
