# <a name="delete-event"></a>Delete (Ereignis)

Löschen Sie Ereignis.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: ***Calendars.ReadWrite***
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /me/events/<id>
DELETE /users/<id | userPrincipalName>/events/<id>
DELETE /groups/<id>/events/<id>

DELETE /me/calendar/events/<id>
DELETE /users/<id | userPrincipalName>/calendar/events/<id>
DELETE /groups/<id>/calendar/events/<id>/

DELETE /me/calendars/<id>/events/<id>
DELETE /users/<id | userPrincipalName>/calendars/<id>/events/<id>

DELETE /me/calendargroup/calendars/<id>/events/<id>
DELETE /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>

DELETE /me/calendargroups/<id>/calendars/<id>/events/<id>
DELETE /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_event"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/events/<id>
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
  "description": "Delete event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->