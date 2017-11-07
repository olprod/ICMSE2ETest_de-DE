# <a name="delete-attachment"></a>Anlage löschen

Löschen Sie eine Anlage aus einer Kalenderereignis, e-Mail-Nachricht oder Post Gruppe.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

* Wenn Anlagen in Nachrichten zugreifen: *Mail.ReadWrite*
* Wenn das Zugreifen auf Anlagen in Ereignisse: *Calendars.ReadWrite*
* Wenn der Zugriff auf Anlagen in der Gruppe Ereignisse oder Beiträge: *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für ein [Ereignis](../resources/event.md) in die des Benutzers oder einer Gruppe standardmäßig [Kalender](../resources/calendar.md).
```http
DELETE /me/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/events/<id>/attachments/<id>
DELETE /groups/<id>/events/<id>/attachments/<id>

DELETE /me/calendar/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendar/events/<id>/attachments/<id>
DELETE /groups/<id>/calendar/events/<id>/attachments/<id>
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) des Benutzers Standard [CalendarGroup](../resources/calendargroup.md)zugehörigen.
```http
DELETE /me/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments/<id>

DELETE /me/calendargroup/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments/<id>
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) zu einem Benutzer [CalendarGroup](../resources/calendargroup.md)gehören.
```http
DELETE /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) im Postfach des Benutzers.
```http
DELETE /me/messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/messages/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) enthalten, die in einer Top-level- [MailFolder](../resources/mailfolder.md) im Postfach eines Benutzers.
```http
DELETE /me/mailFolders/<id>/messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments/<id>
```
Anlagen für eine [Nachricht](../resources/message.md) in einem untergeordneten Ordner von einem [MailFolder](../resources/mailfolder.md) im Postfach des Benutzers enthalten.  Das folgende Beispiel zeigt eine Ebene von schachteln, aber eine Nachricht kann befinden in ein untergeordnetes Element des ein untergeordnetes Element und so weiter.
```http
DELETE /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
Anlagen für einen [Posten](../resources/post.md) in einem [Thread](../resources/conversationthread.md) , gehören zu einer [Unterhaltung](../resources/conversation.md) einer Gruppe.
```http
DELETE /groups/<id>/threads/<id>/posts/<id>/attachments/<id>
DELETE /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/attachments/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_attachment"
}-->
```http
DELETE https://graph.microsoft.com/v1.0/me/events/<id>/attachments/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
