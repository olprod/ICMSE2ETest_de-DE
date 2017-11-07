# <a name="event-accept"></a>Ereignis: akzeptieren

Akzeptieren Sie das angegebene Ereignis.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/accept
POST /users/<id | userPrincipalName>/events/<id>/accept
POST /groups/<id>/events/<id>/accept

POST /me/calendar/events/<id>/accept
POST /users/<id | userPrincipalName>/calendar/events/<id>/accept
POST /groups/<id>/calendar/events/<id>/accept

POST /me/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/accept

POST /me/calendargroup/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/accept

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/accept
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Kommentar|String|Der Text in der Antwort enthalten. Optional|
|sendResponse|Boolean|`true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "event_accept"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/accept
Content-type: application/json
Content-length: 56

{
  "comment": "comment-value",
  "sendResponse": true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: accept",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
