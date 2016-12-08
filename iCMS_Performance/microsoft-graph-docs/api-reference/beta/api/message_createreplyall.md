# <a name="message-createreplyall"></a>Meldung: CreateReplyAll

Erstellen Sie ein Entwurfs oder eine allen Antworten-Nachricht enthalten einen Kommentar oder aktualisieren alle Nachrichteneigenschaften, alle in einem einzigen Aufruf von **CreateReplyAll** . Dann können [Aktualisieren](../api/message_update.md) oder den Entwurf [Senden](../api/message_send.md) .

**Hinweis**

- Sie können angeben, einen Kommentar oder die **Body** -Eigenschaft von der `message` Parameter. Angeben beider gibt einen HTTP-400-Bad Request-Fehler zurück.
- Wenn die **ReplyTo** -Eigenschaft angegeben wird, in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)), sollten Sie senden Sie die Antwort an die Empfänger in der  
**ReplyTo** und **ToRecipients** -Eigenschaften, und nicht die Empfänger in den Eigenschaften **von** und **ToRecipients** . 


## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/createReplyAll
POST /users/<id | userPrincipalName>/messages/<id>/createReplyAll
POST /me/mailFolders/<id>/messages/<id>/createReplyAll
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/createReplyAll
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
|Nachricht|[Nachricht](../resources/message.md)|Alle schreibbaren Eigenschaften, in die allen Antworten-Nachricht zu aktualisieren.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `201, Created` Antwortobjekt Code und [Nachricht](../resources/message.md) in der Antworttext.

## <a name="example"></a>Beispiel
Das folgende Beispiel erstellt einen Entwurf, um alle Antworten und fügt eine Anlage und Kommentar in ein **CreateReplyAll** Anruf.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "message_createreplyall"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/createReplyAll
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
    "comment": "if the project gets approved, please take a look at the attached guidelines before you decide on the name." 
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/beta/users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/messages('AAMkADA1MTAAAH5JKpAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DP\"",
  "id": "AAMkADA1MTAAAH5JKpAAA=",
  "subject": "RE: Let's start a group",
  "body": {
    "contentType": "HTML",
    "content": "<html>\r\n<body dir=\"ltr\">\r\nif the project gets approved, please take a look at the attached guidelines before you decide on the name.\r\n<b>From:</b> Admin<br>\r\n<b>Sent:</b> Tuesday, March 15, 2016 6:36:32 AM<br>\r\n<b>To:</b> Fanny Downs; Randi Welch<br>\r\n<b>Subject:</b> RE: Let's start a group\r\n<div>Fanny, Randi, would you name the group please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n</body>\r\n</html>"
  },
  "sender": {
    "emailAddress": {
      "name": "Admin",
      "address": "admin@contoso.onmicrosoft.com"
    }
  },
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "name": "Fanny Downs",
        "address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "emailAddress": {
        "name": "Randi Welch",
        "address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: createReplyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
