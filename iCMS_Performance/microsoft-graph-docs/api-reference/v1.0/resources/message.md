# <a name="message-resource-type"></a>Nachricht Ressourcentyp

Eine Nachricht in einer MailFolder.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Meldung wird angezeigt](../api/message_get.md) | [Nachricht](message.md) |Eigenschaften lesen und Beziehungen des Message-Objekts.|
|[Anlage erstellen](../api/message_post_attachments.md) |[Anlage](attachment.md)| Erstellen Sie eine neue Anlage, indem Sie das Veröffentlichen in der Attachments-Auflistung.|
|[Anlagen auflisten](../api/message_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Ruft alle Anlagen in einer Nachricht ab.|
|[Update](../api/message_update.md) | [Nachricht](message.md) |Objekt "Message" zu aktualisieren.|
|[Löschen](../api/message_delete.md) | Keine |Objekt "Message" gelöscht. |
|[Kopie](../api/message_copy.md)|[Nachricht](message.md)|Kopieren einer Nachricht in einem Ordner.|
|[createForward](../api/message_createforward.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder die Nachricht weiterleiten. Dann können [Aktualisieren](../api/message_update.md) oder den Entwurf [Senden](../api/message_send.md) .|
|[createReply](../api/message_createreply.md)|[Nachricht](message.md)|Erstellen Sie einen Entwurf für die Antwortnachricht. Dann können [Aktualisieren](../api/message_update.md) oder den Entwurf [Senden](../api/message_send.md) .|
|[createReplyAll](../api/message_createreplyall.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder allen Antworten-Nachricht. Dann können [Aktualisieren](../api/message_update.md) oder den Entwurf [Senden](../api/message_send.md) .|
|[Weiterleiten](../api/message_forward.md)|Keine|Weiterleiten einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Verschieben](../api/message_move.md)|[Nachricht](message.md)|Verschieben der Nachricht in einem Ordner. Dadurch wird eine neue Kopie der Nachricht im Zielordner erstellt.|
|[Antwort](../api/message_reply.md)|Keine|Antworten Sie an den Absender einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[replyAll](../api/message_replyall.md)|Keine|Antworten Sie an alle Empfänger einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Senden](../api/message_send.md)|Keine|Sendet einen zuvor erstellte Nachricht Entwurf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine Erweiterung der offenen Typ Daten und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bccRecipients|[Empfänger](recipient.md) -Auflistung|Bcc: Empfänger der Nachricht.|
|body|[itemBody](itembody.md)|Der Textkörper der Nachricht.|
|bodyPreview|String|Die ersten 255 Zeichen des Nachrichtentexts.|
|Kategorien|String-Auflistung|Die Kategorien, die die Nachricht zugeordnet wird.|
|ccRecipients|[Empfänger](recipient.md) -Auflistung|Die Cc: Empfänger der Nachricht.|
|changeKey|String|Die Version der Nachricht.|
|conversationId|String|Die ID der e-Mail-Unterhaltung gehört.|
|createdDateTime|DateTimeOffset|Datum und Uhrzeit der Erstellung die Nachricht.|
|from|[Empfänger](recipient.md)|Der Postfachbesitzer und der Absender der Nachricht.|
|hasAttachments|Boolean|Gibt an, ob die Nachricht Anlagen enthält.|
|id|String|Eindeutiger Bezeichner für die Nachricht (Beachten Sie, die diesen Wert ändern kann, wenn eine Nachricht verschoben oder geändert wird)|
|Bedeutung|String| Die Wichtigkeit der Nachricht: `Low`, `Normal`, `High`.|
|inferenceClassification | String | Die Klassifizierung der Nachricht für Benutzer, basierend auf abgeleiteten Relevanz oder Wichtigkeit oder auf eine explizite Außerkraftsetzung vorliegt. Mögliche Werte sind: `focused` oder `other`. |
|internetMessageId |String |Die Nachrichten-ID im Format durch [RFC2822](http://www.ietf.org/rfc/rfc2822.txt)angegeben. |
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isDraft|Boolean|Gibt an, ob die Nachricht ein Entwurf ist. Eine Nachricht sind Entwürfe, wenn es noch nicht erhalten wurden.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|lastModifiedDateTime|DateTimeOffset|Datum und Uhrzeit der letzten Änderung die Nachricht.|
|parentFolderId|String|Der eindeutige Bezeichner für die Nachricht übergeordneten MailFolder.|
|receivedDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht empfangen wurde.|
|replyTo|[Empfänger](recipient.md) -Auflistung|Die e-Mail-Adressen beim Antworten verwenden.|
|Absender|[Empfänger](recipient.md)|Das Konto, das tatsächlich verwendet wird, um die Nachricht zu generieren.|
|sentDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht gesendet wurde.|
|Betreff|String|Der Betreff der Nachricht.|
|toRecipients|[Empfänger](recipient.md) -Auflistung|So: Empfänger der Nachricht.|
|uniqueBody|[itemBody](itembody.md)|Der Teil des Textkörpers der Nachricht, die für die aktuelle Nachricht eindeutig ist.|
|webLink|String|Die URL zum Öffnen der Nachricht in Outlook Web App.<br><br>Sie können ein Argument Ispopout fügen Sie am Ende der URL zum Ändern der Anzeige der Nachricht. Wenn Ispopout nicht vorhanden ist oder wenn es auf 1 festgelegt ist, wird die Nachricht in einem Popout-Fenster angezeigt. Wenn Ispopout auf 0 festgelegt ist, wird im Browser in der Outlook Web App-Bereich prüfen die Nachricht angezeigt.<br><br>Die Nachricht wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit den Browser nicht bereits angemeldet sind.<br><br>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|

**Entfernen von Skript aus die Body-Eigenschaft**

Der Nachrichtentext kann HTML oder Text sein. Wenn der Textkörper HTML, in der Standardeinstellung ist, würde vor potenziell unsicheren HTML-Code (beispielsweise JavaScript) in die Body-Eigenschaft eingebettete entfernt werden, bevor der Textkörperinhalt eine REST-Antwort zurückgegeben wird.
Wenn den gesamten ursprünglichen HTML-Code Content erhalten möchten, gehören Sie den folgenden Header der HTTP-Anforderung:
```
Prefer: outlook.allow-unsafe-html
```

**Festlegen der From und der Absender Eigenschaften**

Wenn eine Nachricht aus, in den meisten Fällen From besteht wird und Absender Eigenschaften der gleichen angemeldeten Benutzers, darstellen es sei denn, entweder wird aktualisiert, wie in den folgenden Szenarien beschrieben:

- Die **von** -Eigenschaft kann geändert werden, wenn der Exchange-Administrator **SendAs** -Rechte des Postfachs einige andere Benutzer zugewiesen hat. Der Administrator kann dies, indem Sie in der Azure-Verwaltungsportal **Postfachberechtigungen** des Postfachbesitzers auswählen oder mithilfe der Exchange-Verwaltungskonsole oder ein Windows PowerShell-Add-ADPermission-Cmdlet ausführen. Klicken Sie dann, können Sie programmgesteuert die **von** -Eigenschaft auf einen dieser Benutzer festlegen, die für dieses Postfach **SendAs** berechtigt.
- **Sender** -Eigenschaft kann geändert werden, wenn der Postfachbesitzer mindestens einen Benutzer zum Senden von Nachrichten aus dem Postfach können delegiert wurde. Der Postfachbesitzer kann in Outlook delegieren. Wenn Stellvertreter eine Nachricht im Auftrag der Postfachbesitzer sendet, die **Sender** -Eigenschaft wird der Stellvertretung Konto festgelegt und bleibt die Eigenschaft **aus** des Postfachbesitzers. Programmgesteuert können Sie die **Sender** -Eigenschaft für einen Benutzer festlegen, die Delegaten rechts für dieses Postfach erhalten hat, hat.

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung|[FileAttachment](fileattachment.md) und [ItemAttachment](itemattachment.md) Anlagen für die Nachricht.|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der geöffneten Typ Daten Erweiterungen für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.message"
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
  "inferenceClassification": "String",
  "internetMessageId": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
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
  "description": "message resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
