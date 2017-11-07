# <a name="get-calendar"></a>Kalender abrufen

Rufen Sie die Eigenschaften und Beziehungen des Calendar-Objekt ab.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Eines Benutzers oder einer Gruppe als [Kalender](../resources/calendar.md).
```http
GET /me/calendar
GET /users/<id | userPrincipalName>/calendar
GET /groups/<id>/calendar
```
Ein Benutzer [Kalender](../resources/calendar.md) in die Standard- [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendars/<id>
GET /users/<id | userPrincipalName>/calendars/<id>

GET /me/calendarGroup/calendars/<id>
GET /users/<id | userPrincipalName>/calendarGroup/calendars/<id>
```
Ein Benutzer [Kalender](../resources/calendar.md) in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
GET /me/calendarGroups/<id>/calendars/<id>
GET /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>
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
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortobjekt Code und [Kalender](../resources/calendar.md) in den Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_calendar"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/calendar
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.calendar"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 98

{
  "name": "name-value",
  "color": {
  },
  "changeKey": "changeKey-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get calendar",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
