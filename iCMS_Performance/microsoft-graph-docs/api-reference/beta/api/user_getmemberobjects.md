# <a name="user-getmemberobjects"></a>Benutzer: GetMemberObjects
Zurückgeben Sie aller Gruppen, Directory Rollen und administrative Einheiten, denen der Benutzer Mitglied ist. Die Überprüfung ist transitiv.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *User.Read; User.ReadWrite; User.Read.All; User.ReadWrite.All; Directory.Read.All; Directory.ReadWrite.All; Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/getMemberObjects
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/json  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|securityEnabledOnly|Boolean|**true,** um anzugeben, dass nur Sicherheitsgruppen, dass der Benutzer Mitglied ist zurückgegeben werden soll. **false,** um anzugeben, dass alle Gruppen und Directory Rollen, denen der Benutzer Mitglied ist zurückgegeben werden sollen. Hinweis: Die Funktion kann nur auf einem bestimmten Benutzer aufgerufen werden, wenn der Parameter auf **true**festgelegt ist.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortcode und zeichenfolgenauflistung im Textkörper Antwort, die enthält die IDs der Gruppen und Directory Rollen, die der Benutzer Mitglied ist.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "user_getmemberobjects"
}-->
```http
POST https://graph.microsoft.com/beta/me/getMemberObjects
Content-type: application/json
Content-length: 33

{
  "securityEnabledOnly": true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "string",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 39

{
  "value": [
    "string-value"
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: getMemberObjects",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
