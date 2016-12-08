# <a name="get-photo"></a>Abrufen von Fotos

Rufen Sie die angegebenen [ProfilePhoto](../resources/profilephoto.md) oder der Metadaten (ProfilePhoto Eigenschaften).

Ein GET-Vorgang sucht nach der angegebenen Foto im Postfach des Benutzers auf Exchange Online.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API für ausführen:

*   Profilfotos eines Benutzers in den Mandanten, einschließlich der angemeldeten Benutzers - *User.ReadBasic.All; User.Read.All; User.ReadWrite.All*
*   Profilfoto des speziell angemeldeten Benutzers - *User.Read, User.ReadWrite; User.ReadBasic.All; User.Read.All; User.ReadWrite.All*
* Profilfoto einer **Gruppe** - *Group.Read.All; Group.ReadWrite.All*
* Foto von **wenden Sie sich an** - *Contacts.Read; Contacts.ReadWrite*

## <a name="http-request-to-get-the-photo"></a>HTTP-Anforderung an das Foto erhalten
<!-- { "blockType": "ignored" } -->
```http
GET /me/photo/$value
GET /users/<id | userPrincipalName>/photo/$value
GET /groups/<id>/photo/$value
GET /me/contacts/<id>/photo/$value
GET /users/<id | userPrincipalName>/contacts/<id>/photo/$value
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
```
## <a name="http-request-to-get-the-metadata-of-the-photo"></a>HTTP-Anforderung zum Abrufen der Metadaten des Fotos
<!-- { "blockType": "ignored" } -->
```http
GET /me/photo
GET /users/<id | userPrincipalName>/photo
GET /groups/<id>/photo
GET /me/contacts/<id>/photo
GET /users/<id | userPrincipalName>/contacts/<id>/photo
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photo
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer \<token\>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response-for-getting-the-photo"></a>Antwort zum Abrufen von Fotos
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwort Code und binäre Daten des angeforderten Fotos.  Wenn kein Foto vorhanden ist, gibt der Vorgang `404 Not Found`.
## <a name="response-for-getting-the-metadata-of-the-photo"></a>Antwort zum Abrufen der Metadaten des Fotos
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [ProfilePhoto](../resources/profilePhoto.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1
Diese Anforderung Ruft das Foto für den angemeldeten Benutzer in die größte verfügbare Größe.
<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/photo/$value
```

##### <a name="response-1"></a>Antwort 1
Enthält die binären Daten des angeforderten Fotos. Der HTTP-Antwortcode ist 200.

##### <a name="request-2"></a>Anfordern von 2
Diese Anforderung Ruft die Metadaten des benutzerfoto des angemeldeten Benutzers ab.
<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/photo
```

##### <a name="response-2"></a>Antwort 2

Die folgenden Antwortdaten zeigt die Foto-Metadaten. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten.
<!-- {
  "blockType": "ignored"
}-->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "@odata.mediaEtag": "\"BA09D118\"",
    "id": "240X240",
    "width": 240,
    "height": 240
}
```

Die folgenden Antwortdaten zeigt den Inhalt einer Antwort, wenn ein Foto für den Benutzer bereits hochgeladen wurden noch nicht. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten.

<!-- {
  "blockType": "ignored"
}-->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/gif",
    "@odata.mediaEtag": "",
    "id": "1X1",
    "width": 1,
    "height": 1
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get photo",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
