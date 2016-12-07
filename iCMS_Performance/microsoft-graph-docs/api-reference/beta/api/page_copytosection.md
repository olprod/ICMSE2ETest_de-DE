# <a name="page-copytosection"></a>page: copyToSection
Copies a page to a specific section.

For Copy operations, you follow an asynchronous calling pattern:  First call the Copy action, and then poll the operation endpoint for the result.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, or Notes.ReadWrite.All  
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/pages/<id>/copyToSection
POST /users/<id | userPrincipalName>/notes/pages/<id>/copyToSection
POST /groups/<id>/notes/pages/<id>/copyToSection
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer tokenString`Bearer <token>`Ein gültiges OAuth-Token, das der App basierend auf den Anmeldeinformationen des Benutzers und dem Benutzer bereitgestellt wird, der autorisierten Zugriff hat. Weitere Informationen finden Sie unter . |
| contentType | string | `application/json` |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, provide a JSON object that contains the parameters that your operation needs.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|groupId|String|The id of the group to copy to. Use only when copying to an Office 365 group.|
|id|String|Required. The id of the destination section.|


## <a name="response"></a>Antwort
If successful, this method returns a `202 Accepted` response code and an `Operation-Location` header. Poll the Operation-Location endpoint to [get the status of the copy operation](notesoperation_get.md).

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "page_copytosection"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/pages/<id>/copyToSection
Content-type: application/json
Content-length: 52

{
  "id": "id-value",
  "groupId": "groupId-value"
}
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.copystatusmodel"
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "page: copyToSection",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->