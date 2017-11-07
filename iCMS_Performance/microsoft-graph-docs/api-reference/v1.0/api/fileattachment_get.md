# <a name="get-fileattachment"></a>Abrufen von fileAttachment

Rufen Sie die Eigenschaften und Beziehungen des Fileattachment-Objekts ab.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

* Wenn Anlagen in Nachrichten zugreifen: *Mail.Read*
* Wenn das Zugreifen auf Anlagen in Ereignisse: *Calendars.Read*
* Wenn auf Anlagen in Ereignisse gruppieren oder Beiträge zugreifen: *Group.Read.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für ein [Ereignis](../resources/event.md) in die des Benutzers oder einer Gruppe standardmäßig [Kalender](../resources/calendar.md).
```http
GET /me/events/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/events/<id>/attachments/<id>
GET /groups/<id>/events/<id>/attachments/<id>

GET /me/calendar/<id>/events/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/calendar/events/<id>/attachments/<id>
GET /groups/<id>/calendar/events/<id>/attachments/<id>
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) des Benutzers Standard [CalendarGroup](../resources/calendargroup.md)zugehörigen.
```http
GET /me/calendars/<id>/events/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments/<id>

GET /me/calendargroup/calendars/<id>/events/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments/<id>
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) zu einem Benutzer [CalendarGroup](../resources/calendargroup.md)gehören.
```http
GET /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) im Postfach des Benutzers.
```http
GET /me/messages/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/messages/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) enthalten, die in einer Top-level- [MailFolder](../resources/mailfolder.md) im Postfach eines Benutzers.
```http
GET /me/mailFolders/<id>/messages/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) in einem untergeordneten Ordner von einem [MailFolder](../resources/mailfolder.md) im Postfach des Benutzers enthalten.  Das folgende Beispiel zeigt eine Ebene von schachteln, aber eine Nachricht kann befinden in ein untergeordnetes Element des ein untergeordnetes Element und so weiter.
```http
GET /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
Anlagen für einen [Posten](../resources/post.md) in einem [Thread](../resources/conversationthread.md) , gehören zu einer [Unterhaltung](../resources/conversation.md) einer Gruppe.
```http
GET /groups/<id>/threads/<id>/posts/<id>/attachments/<id>
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/attachments/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [FileAttachment](../resources/fileattachment.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_fileattachment"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/events/<id>/attachments/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.fileAttachment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
      "contentType": "contentType-value",
      "contentLocation": "contentLocation-value",
      "contentBytes": "contentBytes-value",
      "contentId": "null",
      "lastModifiedDateTime": "datetime-value",
      "id": "id-value",
      "isInline": false,
      "isContactPhoto": false,
      "name": "name-value",
      "size": 99
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get fileAttachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
