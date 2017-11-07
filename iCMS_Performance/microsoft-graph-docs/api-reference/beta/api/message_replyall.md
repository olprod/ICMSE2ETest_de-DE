# <a name="message-replyall"></a>Meldung: ReplyAll

Antworten Sie an alle Empfänger einer Nachricht durch einen Kommentar angeben und ändern keine aktualisierbaren Eigenschaften für die Antwort, die alle mithilfe der **ReplyAll** -Methode. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ können Sie zunächst [Erstellen Sie eine Entwurf allen Antworten - Nachricht](../api/message_createreplyall.md) zum Einschließen eines Kommentars oder aktualisieren Sie alle Eigenschaften der Nachricht, und die Antwort zu [Senden](../api/message_send.md) .

**Hinweis**

- Sie können angeben, einen Kommentar oder die **Body** -Eigenschaft von der `message` Parameter. Angeben beider gibt einen HTTP-400-Bad Request-Fehler zurück.
- Wenn die **ReplyTo** -Eigenschaft angegeben wird, in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)), sollten Sie senden Sie die Antwort an die Empfänger in der  
**ReplyTo** und **ToRecipients** -Eigenschaften, und nicht die Empfänger in den Eigenschaften **von** und **ToRecipients** . 


## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.Send*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users/me/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/messages/<id>/replyAll
POST /me/mailFolders/<id>/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/replyAll
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
|Nachricht|[Nachricht](../resources/message.md)|Alle schreibbaren Eigenschaften so aktualisieren Sie in der Antwortnachricht.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Das folgende Beispiel enthält einen Kommentar und fügt eine Anlage zu allen Antworten-Nachricht.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "message_replyall"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/replyAll
Content-Type: application/json

{
    "message":{
      "attachments": [ 
        { 
          "@odata.type": "#microsoft.graph.fileAttachment", 
          "name": "guidelines.txt", 
          "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "comment": "Please take a look at the attached guidelines before you decide on the name." 
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
  "description": "message: replyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
