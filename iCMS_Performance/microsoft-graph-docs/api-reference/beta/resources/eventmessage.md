# <a name="eventmessage-resource-type"></a>Ressourcentyp eventMessage

Eine Nachricht, die eine Besprechung darstellt anfordern, Besprechung absagen Nachricht, Besprechung Nachricht annehmen, Meeting Nachricht mit Vorbehalt annehmen oder Besprechung Nachricht abgelehnt. Insbesondere **EventMessage** [Nachricht](message.md)abgeleitet ist, und [EventMessageRequest](eventMessageRequest.md) **EventMessage** abgeleitet ist und eine Besprechungsanfrage darstellt. **MeetingMessageType** -Eigenschaft Idenfies den Typ der ereignismeldung.

Eine **EventMessage** -Instanz ist in der Regel im Ordner Posteingang gefunden, wo es als Ergebnis der entweder ein Ereignis Organisator eine Besprechung erstellen oder durch einen Teilnehmer reagieren auf eine Besprechungsanfrage eingeht. Sie wirken sich auf Ereignisnachrichten auf die gleiche Weise, die Sie für Nachricht mit Unterschiede bestehen fungieren.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource  

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "event",
    "extensions"
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
  "conversationIndex": "binary",
  "createdDateTime": "String (timestamp)",
  "endDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "flag": {"@odata.type": "microsoft.graph.followupFlag"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "internetMessageId": "String",
  "isAllDay": "Boolean",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isOutOfDate": "Boolean",
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "meetingMessageType": {"@odata.type": "microsoft.graph.meetingMessageType"},
  "parentFolderId": "string",
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
|endDateTime|[DateTimeTimeZone](datetimetimezone.md)|Die Endzeit der angeforderten Besprechung.|
|Kennzeichnung|[followUpFlag](followupflag.md)|Das Flagwert, der den Status, Anfangstermin, Fälligkeitsdatum oder Fertigstellungstermin für die Nachricht angibt.|
|from|[Empfänger](recipient.md)|Der Postfachbesitzer und der Absender der Nachricht.|
|hasAttachments|Boolean|Gibt an, ob die Nachricht Anlagen enthält.|
|id|String||
|Bedeutung|String| Die Priorität der Nachricht: `Low`, `Normal`, `High`.|
|inferenceClassification|String| Mögliche Werte sind: `Focused`, `Other`.|
|internetMessageId |String |Die Nachrichten-ID im Format durch [RFC2822](http://www.ietf.org/rfc/rfc2822.txt)angegeben. |
|isAllDay |Boolean|Gibt an, ob das Ereignis den ganzen Tag dauert. Anpassen dieser Eigenschaft erfordert die **StartDateTime** und **EndDateTime** Eigenschaften des Ereignisses sowie anpassen.|
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isDraft|Boolean|Gibt an, ob die Nachricht ein Entwurf ist. Eine Nachricht ist Entwurf, falls noch nicht erhalten wurden.|
|isOutOfDate|Boolean|Gibt an, ob diese Besprechungsanfrage von einer neueren Anforderung veralteten vorgenommen wurden.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|lastModifiedDateTime|DateTimeOffset|Das Datum und Uhrzeit der letzten Änderung die Nachricht.|
|Speicherort|[Speicherort](location.md)|Der Speicherort der angeforderten Besprechung.|
|meetingMessageType|String| Der Typ der ereignismeldung: `None`, `MeetingRequest`, `MeetingCancelled`, `MeetingAccepted`, `MeetingTenativelyAccepted`, `MeetingDeclined`.|
|parentFolderId|String|Der eindeutige Bezeichner für die Meldung übergeordneten MailFolder.|
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
|UnsubscribeData|String|Gültige Einträge analysiert aus der Liste abmelden Kopfzeile.  Dies ist die Daten für die Mail-Befehl in der Liste abmelden Kopfzeile, wenn UnsubscribeEnabled-Eigenschaft auf true festgelegt ist.|
|UnsubscribeEnabled|Boolean|Gibt an, ob die Nachricht für kündigen aktiviert ist.  Seine ValueTrue Wenn die Liste sich abzumelden Kopfzeile Rfc 2369 entspricht.|
|webLink|String|Die URL zum Öffnen der Nachricht in Outlook Web App.<br><br>Sie können ein Argument Ispopout anfügen, an das Ende der URL zu ändern, wie die Nachricht angezeigt wird. Wenn Ispopout nicht vorhanden ist oder wenn es auf 1 festgelegt ist, wird die Nachricht in einem Popout-Fenster angezeigt. Wenn Ispopout auf 0 festgelegt ist, wird im Browser in der Outlook Web App-Bereich prüfen die Nachricht angezeigt.<br><br>Die Nachricht wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook Web App angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit dem Browser nicht bereits angemeldet sind.<br><br>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|


## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung|Die Auflistung von [FileAttachment](fileattachment.md), [ItemAttachment](itemattachment.md)und [ReferenceAttachment](referenceAttachment.md) Anlagen für die Nachricht. Schreibgeschützt. NULL-Werte zulässt.|
|Ereignis|[Ereignis](event.md)| Das Ereignis ereignismeldung zugeordnet ist. Die Annahme für Teilnehmer oder raumressourcen ist, dass der Kalenderautomatik festgelegt ist, im Kalender mit ein Ereignis, wenn einer Besprechungsanfrage, dass Ereignisnachrichten eintreffen automatisch aktualisiert wird. Navigationseigenschaft.  Schreibgeschützt.|
|Erweiterungen|[Erweiterungssammlung](extension.md)| Die Auflistung der geöffneten Typ Daten Erweiterungen für die EventMessage definiert. Schreibgeschützt. NULL-Werte zulässt.|
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der Mehrfachwert erweiterte Eigenschaften für die EventMessage definiert ist. Schreibgeschützt. NULL-Werte zulässt.|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der einwertig erweiterte Eigenschaften für die EventMessage definiert ist. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von eventMessage](../api/eventmessage_get.md) | [eventMessage](eventmessage.md) |Lesen Sie Eigenschaften und Beziehungen des EventMessage-Objekts.|
|[Erstellen der Anlage](../api/eventmessage_post_attachments.md) |[Anlage](attachment.md)| Erstellen Sie eine neue Anlage, indem Sie das Veröffentlichen in der Attachments-Auflistung.|
|[Anlagen auflisten](../api/eventmessage_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Auflistung des Attachment-Objekt.|
|[Liste-Erweiterungen](../api/eventmessage_list_extensions.md) |[Erweiterungssammlung](extension.md)| Rufen Sie eine Auflistung der Erweiterung-Objekt.|
|[Update](../api/eventmessage_update.md) | [eventMessage](eventmessage.md)  |Aktualisieren Sie EventMessage-Objekts.|
|[Löschen](../api/eventmessage_delete.md) | Keine |EventMessage-Objekt zu löschen.|
|[Kopie](../api/message_copy.md)|[Nachricht](message.md)|Kopieren einer Nachricht in einen Ordner.|
|[createForward](../api/message_createforward.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder die Nachricht weiterleiten. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReply](../api/message_createreply.md)|[Nachricht](message.md)|Erstellen Sie einen Entwurf für die Antwortnachricht. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[createReplyAll](../api/message_createreplyall.md)|[Nachricht](message.md)|Erstellen Sie ein Entwurfs oder allen Antworten-Nachricht. Sie können dann [Aktualisieren](../api/message_update.md) oder [Senden Sie](../api/message_send.md) den Entwurf.|
|[Weiterleiten](../api/message_forward.md)|Keine|Weiterleiten einer Nachricht an. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Verschieben](../api/message_move.md)|[Nachricht](message.md)|Verschieben von Nachrichten in einen Ordner. Dadurch wird eine neue Kopie der Nachricht im Zielordner erstellt.|
|[Antwort](../api/message_reply.md)|Keine|Antworten Sie an den Absender einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[replyAll](../api/message_replyall.md)|Keine|Antworten Sie an alle Empfänger einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Senden](../api/message_send.md)|Keine|Sendet einen zuvor erstellte Nachricht Entwurf. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.|
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) | [openTypeExtension](opentypeextension.md) | Erstellen Sie eine Erweiterung der offenen Typ Daten und Hinzufügen von benutzerdefinierten Eigenschaften in einem neuen oder vorhandenen EventMessage. |
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[openTypeExtension](../resources/opentypeextension.md) | Rufen Sie eine Erweiterung der offenen Typ Daten aus der angegebenen EventMessage. |
|[Erstellen Sie erweiterter einwertig-Eigenschaft](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[eventMessage](eventMessage.md)  |Erstellen Sie eine oder mehrere einwertig erweiterte Eigenschaften in einem neuen oder vorhandenen EventMessage.   |
|[Abrufen von EventMessage mit erweiterten einwertig-Eigenschaft](../api/singlevaluelegacyextendedproperty_get.md)  | [eventMessage](eventMessage.md) | Abrufen von EventMessages, die einen erweiterte Eigenschaft mithilfe von Single-Wert enthalten `$expand` oder `$filter`. |
|[Erweiterte Eigenschaft Mehrfachwert erstellen](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [eventMessage](eventMessage.md) | Erstellen Sie eine oder mehrere erweiterte mehrwertige Eigenschaften in einem neuen oder vorhandenen EventMessage.  |
|[Abrufen von EventMessage mit erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_get.md)  | [eventMessage](eventMessage.md) | Abrufen einer EventMessage, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`. |
|[Melden Sie sich ab](../api/message_unsubscribe.md)|Keine|Senden einer Nachricht mit der Daten und in den ersten Mailto Befehl in der Liste abmelden Kopfzeile angegebenen Adresse.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "eventMessage resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
