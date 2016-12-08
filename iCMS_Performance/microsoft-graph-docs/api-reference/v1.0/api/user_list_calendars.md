# <a name="list-calendars"></a>Liste Kalender

Kalender des Benutzers abrufen (`/calendars` Navigationseigenschaft), rufen Sie die Kalender aus der Standardgruppe Kalender oder aus einer bestimmten Kalendergruppe. 
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read; Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->

Kalender des Benutzers.
```http
GET /me/calendars
GET /users/<id | userPrincipalName>/calendars
```

In der Standard- [CalendarGroup](../resources/calendarGroup.md)des Benutzers-Kalender.
```http
GET /me/calendargroups/{calendar_group_id}/calendars
GET /users/<id | userPrincipalName>/calendarGroup/calendars
```

Der Benutzer Kalender in einer bestimmten [CalendarGroup](../resources/calendarGroup.md).
```http
GET /me/calendarGroups/{calendar_group_id}/calendars
GET /users/<id | userPrincipalName>/calendarGroups/{calendar_group_id}/calendars
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Akzeptieren  | Application/json|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von [Calendar](../resources/calendar.md) -Objekten im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_calendars"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/calendars
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.calendar",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 147

{
  "value": [
    {
      "name": "name-value",
      "color": {
      },
      "changeKey": "changeKey-value",
      "id": "id-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List calendars",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->