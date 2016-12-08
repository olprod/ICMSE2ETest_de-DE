# <a name="delete-contact"></a>Kontakt löschen

Löschen eines Kontakts an.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
[Wenden Sie sich](../resources/contact.md) von einem Benutzer standardmäßig [ContactFolder](../resources/contactfolder.md).
```http
DELETE /me/contacts/<id>
DELETE /users/<id | userPrincipalName>/contacts/<id>
```
[Wenden Sie sich an](../resources/contact.md) von eines Benutzers oberen Ebene [ContactFolder](../resources/contactfolder.md).
```http
DELETE /me/contactFolders/<id>/contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
[Wenden Sie sich](../resources/contact.md) in einem untergeordneten Ordner von einem [ContactFolder](../resources/mailfolder.md)enthaltenen. Das folgende Beispiel zeigt eine Ebene der Schachtelung, aber ein Kontakt kann befindet sich ein untergeordnetes Element des ein untergeordnetes Element und so weiter.
```http
DELETE /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es werden keine etwas in der Antworttext zurückgegeben.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_contact"
}-->
```http
DELETE https://graph.microsoft.com/v1.0/me/contacts/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "Delete contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
