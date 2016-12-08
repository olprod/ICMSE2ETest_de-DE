# <a name="create-contactfolder"></a>Erstellen von ContactFolder

Erstellen einer neuen ContactFolder als untergeordnetes Element eines angegebenen Ordners an. 

Sie können auch [eine neue ContactFolder unter Standard-Kontaktordner des Benutzers zu erstellen](user_post_contactfolders.md).
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/contactFolders/<id>/childFolders
POST /users/<id | userPrincipalName>/contactFolders/<id>/childFolders
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ContactFolder](../resources/contactfolder.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [ContactFolder](../resources/contactfolder.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_contactfolder_from_contactfolder"
}-->
```http
POST https://graph.microsoft.com/beta/me/contactFolders/<id>/childFolders
Content-type: application/json
Content-length: 84

{
  "displayName": "displayName-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ContactFolder](../resources/contactfolder.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.contactFolder"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 104

{
  "parentFolderId": "parentFolderId-value",
  "displayName": "displayName-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create ContactFolder",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
