# <a name="create-attachment"></a>Erstellen der Anlage

Verwenden Sie diese API, um eine [Anlage](../resources/attachment.md) auf ein Ereignis hinzuzufügen. Da es derzeit maximal 4MB für die Gesamtgröße der einzelnen REST-Anforderungen ist, beschränkt dies die Größe der Anlage, die Sie größer als 4 MB hinzufügen können.
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
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [Attachment](../resources/attachment.md) -Objekt aus der Antwort.

## <a name="example-file-attachment"></a>Beispiel (Dateianlage)

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_event"
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

Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Attachment](../resources/attachment.md) -Objekt.

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
  "name": "create_item_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": {}
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
