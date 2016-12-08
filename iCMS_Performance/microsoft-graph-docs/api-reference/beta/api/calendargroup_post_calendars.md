# <a name="create-calendar"></a>Kalender erstellen

Verwenden Sie diese API, um einen neuen Kalender in einer Kalendergruppe zu erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: _Calendars.ReadWrite_
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Ein Benutzer standardmäßig [CalendarGroup](../resources/calendargroup.md).
```http
POST /me/calendarGroup/calendars
POST /users/<id | userPrincipalName>/calendarGroup/calendars
```
Alle [CalendarGroup](../resources/calendargroup.md) eines Benutzers.
```http
POST /me/calendarGroups/<id>/calendars
POST /users/<id | userPrincipalName>/calendarGroups/<id>/calendars
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Calendar](../resources/calendar.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [Calendar](../resources/calendar.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_calendar_from_calendargroup"
}-->
```http
POST https://graph.microsoft.com/beta/me/calendarGroups/<id>/calendars
Content-type: application/json
Content-length: 78

{
  "name": "name-value",
  "color": {
  }
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Calendar](../resources/calendar.md) -Objekt.
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
  "description": "Create Calendar",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
