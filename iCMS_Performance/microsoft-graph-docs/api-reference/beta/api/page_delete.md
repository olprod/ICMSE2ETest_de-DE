# <a name="delete-page"></a>Seite löschen

Löschen einer OneNote-Seite.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /me/notes/pages/<id>
DELETE /users/<id | userPrincipalName>/notes/pages/<id>
DELETE /groups/<id>/notes/pages/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |


## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `204 No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_page"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/notes/pages/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->