# <a name="message-forward"></a>Meldung: weiterleiten

Weiterleiten einer Nachricht, einen Kommentar hinzufügen oder Ändern von aktualisierbaren Eigenschaften  
Rufen Sie alle in einem **Weiterleiten** . Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ können Sie zunächst [den Entwurf Weiterleiten einer Nachricht erstellen](../api/message_createforward.md) zum Einschließen eines Kommentars oder aktualisieren Sie alle Nachrichteneigenschaften, und klicken Sie dann den Entwurf einer Nachricht [Senden](../api/message_send.md) .

**Hinweis**

- Sie können angeben, einen Kommentar oder die **Body** -Eigenschaft von der `message` Parameter. Angeben beider gibt einen HTTP-400-Bad Request-Fehler zurück.
- Geben Sie entweder die `toRecipients` Parameter oder die **ToRecipients** -Eigenschaft des der `message` Parameter. Beide angeben oder keine Angabe gibt einen HTTP 400 Ungültige Anforderung Fehler zurück.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.Send*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/forward
POST /users/<id | userPrincipalName>/messages/<id>/forward
POST /me/mailFolders/<id>/messages/<id>/forward
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/forward
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Kommentar|String|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|toRecipients|[Empfänger](../resources/recipient.md) -Auflistung|Die Liste der Empfänger.|
|Nachricht|[Nachricht](../resources/message.md)|Alle schreibbaren Eigenschaften so aktualisieren Sie in der Antwortnachricht.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die **IsDeliveryReceiptRequested** -Eigenschaft auf True festgelegt, wird ein Kommentar hinzugefügt und leitet die Nachricht weiter.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "message_forward"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/forward
Content-Type: application/json

{
  "message":{  
    "isDeliveryReceiptRequested": true,
    "toRecipients":[
      {
        "emailAddress": {
          "address":"danas@contoso.onmicrosoft.com",
          "name":"Dana Swope"
        }
      }
     ]
  },
  "comment": "Dana, just want to make sure you get this." 
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: forward",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
