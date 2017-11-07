# <a name="update-calendar"></a>Update-Kalender

Aktualisieren Sie die Eigenschaften des Calendar-Objekt.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Eines Benutzers oder einer Gruppe als [Kalender](../resources/calendar.md).
```http
PATCH /me/calendar
PATCH /users/<id | userPrincipalName>/calendar
PATCH /groups/<id>/calendar
```
Ein Benutzer [Kalender](../resources/calendar.md) in die Standard- [CalendarGroup](../resources/calendargroup.md).
```http
PATCH /me/calendars/<id>
PATCH /users/<id | userPrincipalName>/calendars/<id>

PATCH /me/calendarGroup/calendars/<id>
PATCH /users/<id | userPrincipalName>/calendarGroup/calendars/<id>
```
Ein Benutzer [Kalender](../resources/calendar.md) in einer bestimmten [CalendarGroup](../resources/calendargroup.md).
```http
PATCH /me/calendarGroups/<id>/calendars/<id>
PATCH /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|color|String|Gibt die Farbdesigns, um den Kalender von anderen Kalender in einer Benutzeroberfläche zu unterscheiden. Die Eigenschaftswerte werden: Hellblau = 0, LightGreen = 1, LightOrange = 2, LightGray = 3, LightYellow = 4, LightTeal = 5, LightPink = 6, LightBrown = 7 LightRed = 8, MaxColor = 9, Auto =-1|
|name|String|Der Kalendername.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [Kalender](../resources/calendar.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_calendar"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/calendar
Content-type: application/json
Content-length: 48

{
  "name": "name-value",
  "color": {
  }
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "Update calendar",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
