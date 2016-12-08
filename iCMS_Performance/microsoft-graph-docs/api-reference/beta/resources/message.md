# <a name="message-resource-type"></a>Nachricht Ressourcentyp

Eine Nachricht in einem Postfachordner.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "extensions"
  ],
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
  "conversationIndex": "binary",
  "createdDateTime": "String (timestamp)",
  "flag": {"@odata.type": "microsoft.graph.followupFlag"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
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
  "UnsubscribeData": "string",
  "UnsubscribeEnabled": true,
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
|conversationIndex|Binary|Der Index der e-Mail-Unterhaltung gehört.|
|createdDateTime|DateTimeOffset|Datum und Uhrzeit der Erstellung die Nachricht.|
|Kennzeichnung|[followUpFlag](followupflag.md)|Das Flagwert, der den Status, Anfangstermin, Fälligkeitsdatum oder Fertigstellungstermin für die Nachricht angibt.|
|from|[Empfänger](recipient.md)|Der Postfachbesitzer und der Absender der Nachricht.|
|hasAttachments|Boolean|Gibt an, ob die Nachricht Anlagen enthält.|
|id|String|Eindeutiger Bezeichner für die Nachricht (Beachten Sie, die diesen Wert ändern kann, wenn eine Nachricht verschoben oder geändert wird)|
|Bedeutung|String| Die Priorität der Nachricht: `Low`, `Normal`, `High`.|
|inferenceClassification|String| Die Klassifizierung der Nachricht für Benutzer, basierend auf abgeleiteten Relevanz oder Wichtigkeit oder auf eine explizite Außerkraftsetzung vorliegt. Mögliche Werte sind: `focused`, `other`.|
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isDraft|Boolean|Gibt an, ob die Nachricht ein Entwurf ist. Eine Nachricht ist Entwurf, falls noch nicht erhalten wurden.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|lastModifiedDateTime|DateTimeOffset|Das Datum und Uhrzeit der letzten Änderung die Nachricht.|
|parentFolderId|String|Der eindeutige Bezeichner für die Meldung übergeordneten MailFolder.|
|receivedDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht empfangen wurde.|
|replyTo|[Empfänger](recipient.md) -Auflistung|Die e-Mail-Adressen beim Antworten verwenden.|
|Absender|[Empfänger](recipient.md)|Das Konto, das tatsächlich verwendet wird, um die Nachricht zu generieren.|
|sentDateTime|DateTimeOffset|Das Datum und die Zeit, die die Nachricht gesendet wurde.|
|Betreff|String|Der Betreff der Nachricht.|
|toRecipients|[Empfänger](recipient.md) -Auflistung|So: Empfänger der Nachricht.|
|uniqueBody|[itemBody](itembody.md)|Der Teil des Textkörpers der Nachricht, die für die aktuelle Nachricht eindeutig ist.|
|UnsubscribeData|String|Gültige Einträge analysiert aus der Liste abmelden Kopfzeile.  Dies ist die Daten für die Mail-Befehl in der Liste abmelden Kopfzeile, wenn UnsubscribeEnabled-Eigenschaft auf true festgelegt ist.|
|UnsubscribeEnabled|Boolean|Gibt an, ob die Nachricht für kündigen aktiviert ist.  Seine ValueTrue Wenn die Liste sich abzumelden Kopfzeile Rfc 2369 entspricht.|
|webLink|String|Die URL zum Öffnen der Nachricht in Outlook Web App.<br><br>Sie können ein Argument Ispopout anfügen, an das Ende der URL zu ändern, wie die Nachricht angezeigt wird. Wenn Ispopout nicht vorhanden ist oder wenn es auf 1 festgelegt ist, wird die Nachricht in einem Popout-Fenster angezeigt. Wenn Ispopout auf 0 festgelegt ist, wird im Browser in der Outlook Web App-Bereich prüfen die Nachricht angezeigt.<br><br>Die Nachricht wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit dem Browser nicht bereits angemeldet sind.<br><br>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|

**Entfernen von Skript aus die Body-Eigenschaft**

Der Nachrichtentext kann HTML oder Text sein. Wenn der Textkörper HTML, in der Standardeinstellung ist, würde vor potenziell unsicheren HTML-Code (beispielsweise JavaScript) eingebettet in die Body-Eigenschaft entfernt werden, bevor eine REST-Antwort der Textkörperinhalt zurückgegeben wird.
Wenn den gesamten ursprünglichen HTML-Code Content erhalten möchten, gehören Sie den folgenden Header der HTTP-Anforderung:
```
Prefer: outlook.allow-unsafe-html
```

**Festlegen der From und der Absender Eigenschaften**

Wenn eine Nachricht aus, in den meisten Fällen From besteht wird und Absender Eigenschaften der gleichen angemeldeten Benutzers, darstellen es sei denn, entweder wird aktualisiert, wie in den folgenden Szenarien beschrieben:

- Die Eigenschaft **aus** kann geändert werden, wenn der Exchange-Administrator **SendAs** -Rechte des Postfachs einige andere Benutzer zugewiesen hat. Der Administrator kann dies, indem Sie in der Azure-Verwaltungsportal **Postfachberechtigungen** des Postfachbesitzers auswählen oder mithilfe der Exchange-Verwaltungskonsole oder ein Windows PowerShell-Add-ADPermission-Cmdlet ausführen. Anschließend können Sie programmgesteuert die Eigenschaft **aus** auf eine dieser Benutzer festlegen, die für dieses Postfach **SendAs** berechtigt.
- **Sender** -Eigenschaft kann geändert werden, wenn der Postfachbesitzer eine oder mehrere Benutzer zum Senden von Nachrichten aus dem Postfach können delegiert wurde. Der Postfachbesitzer kann in Outlook delegieren. Wenn Stellvertreter eine Nachricht im Auftrag des Postfachbesitzers sendet, **Sender** -Eigenschaft wird der Stellvertretung Konto festgelegt, und der Postfachbesitzer bleibt die Eigenschaft **aus** . Programmgesteuert können Sie die **Sender** -Eigenschaft für einen Benutzer festlegen, die Delegaten rechts für dieses Postfach erhalten hat, hat.

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung|[FileAttachment](fileattachment.md) und [ItemAttachment](itemattachment.md) Anlagen für die Nachricht.|
|Erweiterungen|[Erweiterungssammlung](extension.md)| Schreibgeschützt. NULL-Werte zulässt.|
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der Mehrfachwert erweiterte Eigenschaften für die Meldung definiert. Schreibgeschützt. NULL-Werte zulässt.|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der einwertig erweiterte Eigenschaften für die Nachricht definiert ist. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Meldung wird angezeigt](../api/message_get.md) | [Nachricht](message.md) |Eigenschaften lesen und Beziehungen des Message-Objekts.|
|[Erstellen der Anlage](../api/message_post_attachments.md) |[Anlage](attachment.md)| Erstellen Sie eine neue Anlage, indem Sie das Veröffentlichen in der Attachments-Auflistung.|
|[Anlagen auflisten](../api/message_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Auflistung des Attachment-Objekt.|
|[Update](../api/message_update.md) | [Nachricht](message.md) |Objekt "Message" zu aktualisieren. |
|[Löschen](../api/message_delete.md) | Keine |Objekt "Message" zu löschen. |
|[Kopie](../api/message_copy.md)|[Nachricht](message.md)|Kopieren einer Nachricht in einen Ordner.|
|[createForward](../api/message_createforward.md)|[Nachricht](message.md)|Erstellen Sie den Entwurf einer Nachricht weiterleiten eingeschlossen einen Kommentar oder aktualisieren Sie die Nachrichteneigenschaften in einem einzigen Aufruf von **CreateForward** . Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReply](../api/message_createreply.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder einer Nachricht Reply eingeschlossen einen Kommentar oder aktualisieren Sie die Nachrichteneigenschaften in einem einzigen Aufruf von **CreateReply** . Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReplyAll](../api/message_createreplyall.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder eine allen Antworten-Nachricht eingeschlossen einen Kommentar oder aktualisieren Sie die Nachrichteneigenschaften, alle in einem **CreateReplyAll** -Aufruf. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[Weiterleiten](../api/message_forward.md)|Keine|Weiterleiten einer Nachricht, einen Kommentar hinzufügen oder ändern aktualisierbaren Eigenschaften alle in **Vorwärts** durch Aufrufen. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Verschieben](../api/message_move.md)|[Nachricht](message.md)|Verschieben der Nachricht in einen Ordner. Dadurch wird eine neue Kopie der Nachricht im Zielordner erstellt.|
|[Antwort](../api/message_reply.md)|Keine|Antwort an den Absender einer Nachricht, einen Kommentar hinzufügen oder ändern aktualisierbaren Eigenschaften alle in eine **Antwort** Anruf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[replyAll](../api/message_replyall.md)|Keine|Antworten Sie an alle Empfänger einer Nachricht durch Angeben eines Kommentars und Ändern von aktualisierbaren Eigenschaften für die Antwort, die alle mithilfe der **ReplyAll** -Methode. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Senden](../api/message_send.md)|Keine|Sendet einen zuvor erstellte Nachricht Entwurf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Melden Sie sich ab](../api/message_unsubscribe.md)|Keine|Senden einer Nachricht mit der Daten und in den ersten Mailto Befehl in der Liste abmelden Kopfzeile angegebenen Adresse.|
|[Erstellen von openTypeExtension](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine open Typ Daten Erweiterung und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von openTypeExtension](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|
|[Erstellen Sie erweiterter einwertig-Eigenschaft](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[Nachricht](message.md)  |Erstellen Sie eine oder mehrere einwertig erweiterte Eigenschaften in einer neuen oder vorhandenen Nachricht.   |
|[Meldung mit erweiterten Eigenschaft einwertig](../api/singlevaluelegacyextendedproperty_get.md)  | [Nachricht](message.md) | Abrufen von Nachrichten mit einer erweiterten Eigenschaft mithilfe von einwertig `$expand` oder `$filter`. |
|[Erweiterte Eigenschaft Mehrfachwert erstellen](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [Nachricht](message.md) | Erstellen Sie mindestens einen erweiterte mehrwertige Eigenschaften in einem neuen oder vorhandenen Nachricht.  |
|[Meldung mit erweiterten Mehrfachwert-Eigenschaft](../api/multivaluelegacyextendedproperty_get.md)  | [Nachricht](message.md) | Eine Meldung, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`. |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->