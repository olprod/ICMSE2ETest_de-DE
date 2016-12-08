# <a name="delete-calendar"></a>Kalender löschen

Löschen eines Kalenders als Standardkalender.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Ein Benutzer [Kalender](../resources/calendar.md) als Standardkalender in der Standardeinstellung [CalendarGroup](../resources/calendargroup.md).
```http
DELETE /me/calendars/<id>
DELETE /users/<id | userPrincipalName>/calendars/<id>

DELETE /me/calendarGroup/calendars/<id>
DELETE /users/<id | userPrincipalName>/calendarGroup/calendars/<id>
```
Ein [Kalender](../resources/calendar.md) als Standardkalender in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
DELETE /me/calendarGroups/<id>/calendars/<id>
DELETE /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name           |  Typ    | Beschreibung|
|:---------------|:---------|:----------|
| Autorisierung  |  string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_calendar"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/calendar
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
  "description": "Delete calendar",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
