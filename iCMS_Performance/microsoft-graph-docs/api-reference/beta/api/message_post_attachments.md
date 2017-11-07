# <a name="create-attachment"></a>Anlage erstellen

Verwenden Sie diese API, um eine Nachricht eine [Anlage](../resources/attachment.md) hinzuzufügen. 

Sie können eine Anlage zu einer vorhandenen Nachricht hinzufügen, indem das Veröffentlichen in der Attachments-Auflistung, oder an eine neue Nachricht werden, die [Vorlage zu erstellen,](../api/user_post_messages.md)oder [erstellt und gesendet, die dynamisch](../api/user_sendmail.md).

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
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [Attachment](../resources/attachment.md) -Objekt aus der Antwort.

## <a name="example-file-attachment"></a>Beispiel (Dateianlage)

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_message"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/<id>/attachments
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
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 162

{
  "lastModifiedDateTime": "datetime-value",
  "name": "name-value",
  "contentType": "contentType-value",
  "size": 99,
  "isInline": true,
  "id": "id-value"
}
```

## <a name="example-item-attachment"></a>Beispiel (Element Attachment)

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_message"
}-->

```
POST https://graph.microsoft.com/beta/me/messages/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": "message or event entity"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 162

{
  "lastModifiedDateTime": "datetime-value",
  "name": "name-value",
  "contentType": "contentType-value",
  "size": 99,
  "isInline": true,
  "id": "id-value"
}
```

## <a name="example-reference-attachment"></a>Beispiel (Referenz Attachment)

##### <a name="request"></a>Anforderung
Hier ist ein Beispiel für eine Anforderung, die eine Anlage Verweis auf eine vorhandene Nachricht hinzugefügt.
Die Anlage verweist auf einen Ordner auf OneDrive.
<!-- {
  "blockType": "request",
  "name": "create_reference_attachment_from_message"
}-->

```
POST https://graph.microsoft.com/beta/me/messages/AAMkAGE1M88AADUv0uFAAA=/attachments
Content-type: application/json
Content-length: 319

{ 
    "@odata.type": "#microsoft.graph.referenceAttachment", 
    "name": "Personal pictures", 
    "sourceUrl": "https://contoso.com/personal/mario_contoso_net/Documents/Pics", 
    "providerType": "oneDriveConsumer", 
    "permission": "Edit", 
    "isFolder": "True" 
} 
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel einer vollständigen Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 201 Created

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users/ddfcd489-628b-40d7-b48b-57002df800e5/messages/AAMkAGE1M88AADUv0uFAAA%3D/attachments/$entity",
  "@odata.type": "#microsoft.graph.referenceAttachment",
  "id": "AAMkAGE1Mg72tgf7hJp0PICVGCc0g=",
  "lastModifiedDateTime": "2016-03-12T06:04:38Z",
  "name": "Personal pictures",
  "contentType": null,
  "size": 382,
  "isInline": false,
  "sourceUrl": "https://contoso.com/personal/mario_contoso_net/Documents/Pics",
  "providerType": "oneDriveConsumer",
  "thumbnailUrl": null,
  "previewUrl": null,
  "permission": "edit",
  "isFolder": true
}
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
