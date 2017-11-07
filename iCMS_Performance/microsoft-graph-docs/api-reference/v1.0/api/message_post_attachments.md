# <a name="create-attachment"></a>Anlage erstellen

Verwenden Sie diese API, um eine Nachricht eine [Anlage](../resources/attachment.md) hinzuzufügen. 

Sie können auf eine vorhandene Nachricht eine Anlage hinzufügen, indem das Veröffentlichen in der Attachments-Auflistung, oder Sie können eine Anlage zu einer Nachricht, die wird [erstellt und gesendet werden, die dynamisch](../api/user_sendmail.md)hinzufügen.

Da es derzeit maximal 4MB für die Gesamtgröße der einzelnen REST-Anforderungen ist, schränkt dies die Größe der Anlage, die Sie unter 4 MB hinzufügen können.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für eine [Nachricht](../resources/message.md) im Postfach des Benutzers.
```http
POST /me/messages/<id>/attachments
POST /users/<id | userPrincipalName>/messages/<id>/attachments
```
Anlagen für eine [Nachricht](../resources/message.md) enthalten, die in einer Top-level- [MailFolder](../resources/mailfolder.md) im Postfach eines Benutzers.
```http
POST /me/mailFolders/<id>/messages/<id>/attachments
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments
```
Anlagen für eine [Nachricht](../resources/message.md) in einem untergeordneten Ordner von einem [MailFolder](../resources/mailfolder.md) im Postfach des Benutzers enthalten.  Das folgende Beispiel zeigt eine Ebene von schachteln, aber eine Nachricht kann befinden in ein untergeordnetes Element des ein untergeordnetes Element und so weiter.
```http
POST /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
POST /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Attachment](../resources/attachment.md) -Objekt.


## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `201, Created` Antwortcode und [Attachment](../resources/attachment.md) -Objekts in der Antworttext.

## <a name="example-file-attachment"></a>Beispiel (Dateianlage)

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_message"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/attachments
Content-type: application/json
Content-length: 142

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "name": "name-value",
  "contentBytes": "contentBytes-value"
}
```

Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Attachment](../resources/attachment.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

## <a name="example-item-attachment"></a>Beispiel (Element Attachment)

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_message"
}-->

```
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": "message or event entity"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
