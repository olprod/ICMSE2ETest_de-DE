# <a name="update-page"></a>Update-Seite

Aktualisieren des Inhalts einer OneNote-Seite.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/notes/pages/<id>/content
PATCH /users/<id | userPrincipalName>/notes/pages/<id>/content
PATCH /groups/<id>/notes/pages/<id>/content
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Inhaltstyp | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein Array von [PatchContentCommand](../resources/patchcontentcommand.md) -Objekten, die Änderungen auf der Seite darstellen. Weitere Informationen und Beispiele finden Sie unter <a href="https://msdn.microsoft.com/office/office365/howto/onenote-update-page">Update OneNote-Seiten</a>.

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `204 No Content` Antwortcode.  Keine JSON-Daten für eine Anforderung PATCH zurückgegeben.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_page"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/notes/pages/<id>/content
Content-type: application/json
Content-length: 312

[
   {
    'target':'#para-id',
    'action':'insert',
    'position':'before',
    'content':'<img src="image-url-or-part-name" alt="image-alt-text" />'
  }, 
  {
    'target':'#list-id',
    'action':'append',
    'content':'<li>new-page-content</li>'
  }
]
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.page"
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
