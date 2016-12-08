# <a name="update-message"></a>Aktualisierungsnachricht

Aktualisieren Sie die Eigenschaften des Message-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id | userPrincipalName>/messages/<id>
PATCH /me/mailFolders/<id>/messages/<id>
PATCH /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |
## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind verwalten ihre vorherigen Werte oder neu berechnet auf der Grundlage Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert haben. Kein Schreibschutz/Updatable Eigenschaften sind

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bccRecipients|Recipient|Die Bcc-Empfänger der Nachricht. Aktualisierbare nur, wenn IsDraft = True.|
|Kategorien|Zeichenfolgenauflistung|Die Kategorien, die Nachricht zugeordnet.|
|ccRecipients|Empfänger-Auflistung|Cc Empfänger der Nachricht. Aktualisierbare nur, wenn IsDraft = True.|
|from|Recipient|Der Postfachbesitzer und der Absender der Nachricht. Aktualisierbare nur, wenn IsDraft = True.|
|Bedeutung|String|Die Wichtigkeit der Nachricht. Mögliche Werte sind: `Low`, `Normal`, `High`.|
|inferenceClassification | String | Die Klassifizierung der Nachricht für Benutzer, basierend auf abgeleiteten Relevanz oder Wichtigkeit oder auf eine explizite Außerkraftsetzung vorliegt. Mögliche Werte sind: `focused` oder `other`. |
|internetMessageId |String |Die Nachrichten-ID im Format durch [RFC2822](http://www.ietf.org/rfc/rfc2822.txt)angegeben. Nur aktualisiert, wenn IsDraft = True.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|replyTo|Empfänger-Auflistung|Die e-Mail-Adressen beim Antworten verwenden. Nur aktualisiert, wenn IsDraft = True.|
|Absender|Recipient|Das Konto, das tatsächlich verwendet wird, um die Nachricht zu generieren. Nur aktualisiert, wenn IsDraft = True.|
|toRecipients|Empfänger-Auflistung|Die für die Nachricht an-Empfänger. Nur aktualisiert, wenn IsDraft = True.|
|body|ItemBody|Der Textkörper der Nachricht. Nur aktualisiert, wenn IsDraft = True.|
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|Betreff|String|Der Betreff der Nachricht. Aktualisierbare nur, wenn IsDraft = True.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [Nachricht](../resources/message.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_message"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/messages/<id>
Content-type: application/json
Content-length: 248

{
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "inferenceClassification": "other"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 248

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value",
  "inferenceClassification": "other"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update message",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
