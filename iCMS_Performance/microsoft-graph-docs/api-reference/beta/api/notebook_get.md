# <a name="get-notebook"></a>Get notebook

Retrieve the properties and relationships of a [notebook](../resources/notebook.md) object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:  
Notes.Read, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, Notes.Read.All, or Notes.ReadWrite.All 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/notebooks/<id>
GET /users/<id | userPrincipalName>/notes/notebooks/<id>
GET /groups/<id>/notes/notebooks/<id>
```
## <a name="optional-query-parameters"></a>Optionale OData-Abfrageparameter
This method supports the `select` and `expand` [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

Valid `expand` values for notebooks are `sections` and `sectionGroups`.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer tokenString`Bearer <token>`Ein gültiges OAuth-Token, das der App basierend auf den Anmeldeinformationen des Benutzers und dem Benutzer bereitgestellt wird, der autorisierten Zugriff hat. Weitere Informationen finden Sie unter . |
| Accept-Methode | string | `application/json` | 

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.
## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and a [notebook](../resources/notebook.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "get_notebook"
}-->
```http
GET https://graph.microsoft.com/beta/me/notes/notebooks/<id>
```
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here is truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.notebook"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 284

{
  "isDefault": true,
  "userRole": {
  },
  "isShared": true,
  "sectionsUrl": "sectionsUrl-value",
  "sectionGroupsUrl": "sectionGroupsUrl-value",
  "links": {
    "oneNoteClientUrl": {
      "href": "href-value"
    },
    "oneNoteWebUrl": {
      "href": "href-value"
    }
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get notebook",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->