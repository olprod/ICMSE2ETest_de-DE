# <a name="group-getmemberobjects"></a>Gruppe: GetMemberObjects
Zurückgeben Sie aller Gruppen und administrative Einheiten, denen die Gruppe ein Mitglied ist. Die Überprüfung ist transitiv. Hinweis: Gruppen können nicht Mitglieder der Directory Rollen sein, damit keine Directory Rollen zurückgegeben werden.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Group.Read.All* oder *Directory.Read.All* oder *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*.
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/getMemberObjects
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|securityEnabledOnly|Boolean|**true,** um anzugeben, dass nur Sicherheitsgruppen, dass die Gruppe ein Mitglied ist zurückgegeben werden soll. **false,** um anzugeben, dass alle Gruppen, denen die Gruppe ein Mitglied ist zurückgegeben werden sollen.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortcode und Zeichenfolge-Auflistung in der Antworttext, das die IDs der Gruppen enthält, das die Gruppe ein Mitglied ist.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "group_getmemberobjects"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/getMemberObjects
Content-type: application/json
Content-length: 33

{
  "securityEnabledOnly": true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "group: getMemberObjects",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
