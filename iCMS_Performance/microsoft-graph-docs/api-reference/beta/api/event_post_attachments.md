# <a name="create-attachment"></a>Anlage erstellen

Verwenden Sie diese API, um eine [Anlage](../resources/attachment.md) auf ein Ereignis hinzufügen. Da es derzeit maximal 4MB für die Gesamtgröße der einzelnen REST-Anforderungen ist, schränkt dies die Größe der Anlage, die Sie unter 4 MB hinzufügen können.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für ein [Ereignis](../resources/event.md) in die des Benutzers oder einer Gruppe standardmäßig [Kalender](../resources/calendar.md).
```http
POST /me/events/<id>/attachments
POST /users/<id | userPrincipalName>/events/<id>/attachments
POST /groups/<id>/events/<id>/attachments

POST /me/calendar/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendar/events/<id>/attachments
POST /groups/<id>/calendar/events/<id>/attachments
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) des Benutzers Standard [CalendarGroup](../resources/calendargroup.md)zugehörigen.
```http
POST /me/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments

POST /me/calendargroup/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) zu einem Benutzer [CalendarGroup](../resources/calendargroup.md)gehören.
```http
POST /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments
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
  "name": "create_file_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/attachments
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
  "name": "create_item_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": {}
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
Hier ist ein Beispiel für eine Anforderung, die eine Anlage Verweis auf ein vorhandenes Ereignis hinzugefügt.
Die Anlage verweist auf einen Ordner auf OneDrive.
<!-- {
  "blockType": "request",
  "name": "create_reference_attachment_from_event"
}-->

```
POST https://graph.microsoft.com/beta/me/events/AAMkAGE1M88AADUv0uAAAG=/attachments
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users/ddfcd489-628b-40d7-b48b-57002df800e5/events/AAMkAGE1M88AADUv0uAAAG%3D/attachments/$entity",
  "@odata.type": "#microsoft.graph.referenceAttachment",
  "id": "AAMkAGE1Mg72tgf7hJp0PCGVCIc0g=",
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
