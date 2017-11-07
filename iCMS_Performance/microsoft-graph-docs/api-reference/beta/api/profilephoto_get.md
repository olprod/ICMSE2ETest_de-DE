# <a name="get-photo"></a>Abrufen von Fotos

Rufen Sie die angegebenen [ProfilePhoto](../resources/profilephoto.md) oder der Metadaten (**ProfilePhoto** Eigenschaften).

GET-Vorgang zunächst sucht nach der angegebenen Foto im Postfach des Benutzers auf Exchange Online, und falls er vorhanden, nicht verfügbar ist sucht dann in Azure Active Directory (AAD).

Zu den unterstützten Größen von HD-Fotos in Exchange Online sind wie folgt: '48 x 48', "64 x 64", '96 x 96', '120 x 120', '240 x 240', ' 360 x 360', '432 x 432', '504 x 504' und ' 648 x 648'. Fotos können eine beliebige Dimension sein, wenn sie in AAD gespeichert sind.

Sie können Abrufen der Metadaten des größten verfügbaren Fotos, oder geben eine Größe, um die Metadaten für dieses Fotogröße zu erhalten.
Wenn die Größe die angeforderten nicht verfügbar ist, erhalten Sie, dass der Benutzer zur Verfügung gestellt und hochgeladen hat immer noch eine geringere Größe.
Angenommen, wenn der Benutzer ein Foto hochlädt 504 x 504 Pixel, und klicken Sie dann alle ist die 648 x 648 Größe der Foto werden jedoch zum Download zur Verfügung.
Wenn die angegebene Größe nicht in das Postfach des Benutzers oder in AAD vorliegt, wird die Größe der "1 x 1" mit dem Rest der Metadaten zurückgegeben.

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

## <a name="http-request-to-get-the-metadata-for-a-specific-photo-size"></a>HTTP-Anforderung zum Abrufen der Metadaten für eine bestimmte Fotogröße
<!-- { "blockType": "ignored" } -->
```http
GET /me/photos/<size>
GET /users/<id | userPrincipalName>/photos/<size>
GET /groups/<id>/photos/<size>
GET /me/contacts/<id>/photos/<size>
GET /users/<id | userPrincipalName>/contacts/<id>/photos/<size>
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photos/<size>
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photos/<size>
```

## <a name="parameters"></a>Parameter

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|size  |String  |Eine Fotogröße. |

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
GET https://graph.microsoft.com/beta/me/photo/$value
Content-Type: image/jpg
```

##### <a name="response-1"></a>Antwort 1
Enthält die binären Daten des angeforderten Fotos. Der HTTP-Antwortcode ist 200.

##### <a name="request-2"></a>Anfordern von 2
Diese Anforderung Ruft das Foto 48 x 48 des angemeldeten Benutzers.

<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/beta/me/photos/48x48/$value
Content-Type: image/jpg
```

##### <a name="response-2"></a>Antwort 2
Enthält die binären Daten des angeforderten 48 x 48 Fotos. Der HTTP-Antwort-Code ist 200.

##### <a name="request-3"></a>Anforderung 3
Diese Anforderung Ruft die Metadaten des benutzerfoto des angemeldeten Benutzers ab.

<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/beta/me/photo
```

##### <a name="response-3"></a>Antwort 3
Die folgenden Antwortdaten zeigt die Foto-Metadaten. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten.

<!-- {
  "blockType": "ignored"
}-->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
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
