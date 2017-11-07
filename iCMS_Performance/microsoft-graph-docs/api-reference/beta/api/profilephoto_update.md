# <a name="update-profilephoto"></a>Profilephoto aktualisieren

Aktualisieren Sie das Foto für jeden Benutzer in den Mandanten, einschließlich der angemeldeten Benutzer oder der angegebenen Gruppe oder des Kontakts. Da es derzeit maximal 4MB für die Gesamtgröße der einzelnen REST-Anforderungen ist, beschränkt dies die Größe des Fotos, das größer als 4 MB hinzugefügt werden können.

Nur die Verwendung für diesen Vorgang in der Beta-Version AUSGESCHLOSSEN.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API für ausführen:

-   Profilfotos jedes Benutzers in den Mandanten, einschließlich der angemeldeten Benutzers - User.ReadWrite.All
-   Profilfoto des speziell angemeldeten Benutzers - User.ReadWrite, User.ReadWrite.All
- Profilfoto einer **Gruppe** - *Group.ReadWrite.All*
- Foto von **wenden Sie sich an** - *Contacts.ReadWrite*

## <a name="http-request-to-update-the-photo"></a>HTTP-Anforderung an das Foto aktualisieren
<!-- { "blockType": "ignored" } -->
```http
PUT /me/photo/$value
PUT /users/<id | userPrincipalName>/photo/$value
PUT /groups/<id>/photo/$value
PUT /me/contacts/<id>/photo/$value
PUT /users/<id | userPrincipalName>/contacts/<id>/photo/$value
PUT /me/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
PUT /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Image/Jpeg festgelegt. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Enthalten Sie im Textkörper Anforderung die binären Daten des Fotos im Textkörper Anforderung.

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_profilephoto"
}-->
```http
PUT https://graph.microsoft.com/beta/me/photo/$value
Content-type: image/jpeg

Binary data for the image

```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.profilePhoto"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update profilephoto",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
