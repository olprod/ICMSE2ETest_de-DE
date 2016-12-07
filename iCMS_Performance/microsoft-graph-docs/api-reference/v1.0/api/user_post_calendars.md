# <a name="create-calendar"></a>Create Calendar

Use this API to create a new Calendar.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Calendars.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/calendars
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Required.  |
| contentType  | application/json  |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a JSON representation of [Calendar](../resources/calendar.md) object.


## <a name="response"></a>Antwort
If successful, this method returns `201, Created` response code and [Calendar](../resources/calendar.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_calendar_from_user"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/calendars
Content-type: application/json
Content-length: 78

{
  "name": "name-value",
  "color": {
  },
  "changeKey": "changeKey-value"
}
```
In the request body, supply a JSON representation of [Calendar](../resources/calendar.md) object.
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
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
