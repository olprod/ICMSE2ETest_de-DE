# <a name="list-attachments"></a>Anlagen auflisten

Abrufen einer Liste der [Attachment](../resources/attachment.md) -Objekte, ein Ereignis zugeordnet ist.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read* 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für ein [Ereignis](../resources/event.md) in die des Benutzers oder einer Gruppe standardmäßig [Kalender](../resources/calendar.md).
```http
GET /me/events/<id>/attachments
GET /users/<id | userPrincipalName>/events/<id>/attachments
GET /groups/<id>/events/<id>/attachments

GET /me/calendar/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendar/events/<id>/attachments
GET /groups/<id>/calendar/events/<id>/attachments
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) des Benutzers Standard [CalendarGroup](../resources/calendargroup.md)zugehörigen.
```http
GET /me/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments

GET /me/calendargroup/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments
```
Anlagen für ein [Ereignis](../resources/event.md) in einem [Kalender](../resources/calendar.md) zu einem Benutzer [CalendarGroup](../resources/calendargroup.md)gehören.
```http
GET /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

Insbesondere können Sie die $ Abfragezeichenfolgen-Parameter, um alle das Ereignis Anlagen Inline mit dem Rest der Ereigniseigenschaften erweitern. Beispiel:

```
GET https://graph.microsoft.com/beta/me/events/<id>?$expand=attachments
```


## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von [Attachment](../resources/attachment.md) -Objekte in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_attachments"
}-->
```http
GET https://graph.microsoft.com/beta/me/events/<id>/attachments
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment",
  "isCollection": true
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
  "description": "List attachments",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->