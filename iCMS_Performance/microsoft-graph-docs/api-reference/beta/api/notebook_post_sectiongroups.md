# <a name="create-sectiongroup"></a>Create sectionGroup

Create a new [section group](../resources/sectiongroup.md) in the specified notebook.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:   
Notes.Create, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, or Notes.ReadWrite.All
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/notebooks/<id>/sectionGroups
POST /users/<id | userPrincipalName>/notes/notebooks/<id>/sectionGroups
POST /groups/<id>/notes/notebooks/<id>/sectionGroups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer tokenString`Bearer <token>`Ein gültiges OAuth-Token, das der App basierend auf den Anmeldeinformationen des Benutzers und dem Benutzer bereitgestellt wird, der autorisierten Zugriff hat. Weitere Informationen finden Sie unter . |
| contentType | string | `application/json` |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a name for the section group.

Within the same hierarchy level, section group names must be unique. The name cannot contain more than 50 characters or contain the following characters:  ?*\/:<>|&#''%~

## <a name="response"></a>Antwort
If successful, this method returns `201 Created` response code and a [sectionGroup](../resources/sectiongroup.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_sectiongroup_from_notebook"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/notebooks/<id>/sectionGroups
Content-type: application/json
Content-length: 30

{
  "name": "Section group name"
}
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here is truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.sectiongroup"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 305

{
  "sectionsUrl": "sectionsUrl-value",
  "sectionGroupsUrl": "sectionGroupsUrl-value",
  "name": "name-value",
  "createdBy": "createdBy-value",
  "createdByIdentity": {
    "user": {
      "id": "id-value",
      "displayName": "displayName-value"
    }
  },
  "lastModifiedBy": "lastModifiedBy-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create SectionGroup",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->