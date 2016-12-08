# <a name="event-cancel"></a>Ereignis: Abbrechen

Diese Aktion ermöglicht den Organisator einer Besprechung senden eine Absage und das Ereignis abzubrechen. 

Die Aktion wird das Ereignis in den Ordner Gelöschte Objekte verschoben. Der Organisator kann auch ein Vorkommen einer Besprechungsserie abzubrechen, durch Bereitstellen der Vorkommen-Ereignis-ID Diese Aktion aufrufen Teilnehmerin Ruft einen Fehler (HTTP 400 Ungültige Anforderung), wobei die folgende Fehlermeldung angezeigt:

"Die Anforderung konnte nicht abgeschlossen werden. Sie müssen ein Organisator eine Besprechung abgebrochen werden."

Diese Aktion unterscheidet sich von [Löschen](event_delete.md) , nur den Organisator steht und ermöglicht es den Organisator, senden eine benutzerdefinierte Meldung an die Teilnehmer über den Abbruch **Abbrechen** .

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/cancel
POST /users/<id | userPrincipalName>/events/<id>/cancel
POST /groups/<id>/events/<id>/cancel

POST /me/calendar/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendar/events/<id>/cancel
POST /groups/<id>/calendar/events/<id>/cancel

POST /me/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/cancel

POST /me/calendargroup/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/cancel

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/cancel
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
|Kommentar|String|Einen Kommentar zu den Abbruch an alle Teilnehmer gesendet. Optional|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "event_cancel"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/cancel
Content-type: application/json

{
  "Comment": "Cancelling for this week due to all hands"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: cancel",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
