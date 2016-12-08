# <a name="get-event"></a>-Ereignis

Rufen Sie die Eigenschaften und Beziehungen des angegebenen [Event](../resources/event.md) -Objekts.

Für alle GET-Vorgänge, die Ereignisse zurückzugeben, verwenden Sie die `Prefer: outlook.timezone` Kopfzeile an die Zeitzone für das Ereignis Start- und Endzeit in der Antwort auftritt. 

Beispielsweise den folgenden `Prefer: outlook.timezone` Header legt die Anfangs- und Endzeiten der Reaktion auf Eastern Standard Time.
```http
Prefer: outlook.timezone="Eastern Standard Time"
```

Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten angepasst werden, auf die Zeitzone, in dem angegebenen `Prefer` Kopfzeile. Finden Sie in dieser [Liste](../resources/datetimetimezone.md) für die Namen der unterstützten Zeitzone. Wenn die `Prefer: outlook.timezone` Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

Sie können die Eigenschaften **OriginalStartTimeZone** und **OriginalEndTimeZone** für die Ressource **Ereignis** verwenden, um zu ermitteln, die Zeitzone verwendet, wenn das Ereignis erstellt wurde.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Calendars.Read*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>
GET /users/<id | userPrincipalName>/events/<id>
GET /groups/<id>/events/<id>

GET /me/calendar/events/<id>
GET /users/<id | userPrincipalName>/calendar/events/<id>
GET /groups/<id>/calendar/events/<id>

GET /me/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>

GET /me/calendargroup/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>

GET /me/calendargroups/<id>/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Bevorzugen: | Outlook.TimeZone | Die Standardzeitzone für Ereignisse in der Antwort. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt [Code und](../resources/event.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_event"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/events/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.event"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 285

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "iCalUId": "iCalUId-value",
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true,
  "start": {
    "dateTime": "datetime-value",
    "timeZone": "timezone-value"
  },
  "end": {
    "dateTime": "datetime-value",
    "timeZone": "timezone-value"
  },        
  "location": {
    "displayName": "displayName-value"
  },
  "organizer": {
    "emailAddress": {
      "address": "address-value",
      "name": "name-value"
    }
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
