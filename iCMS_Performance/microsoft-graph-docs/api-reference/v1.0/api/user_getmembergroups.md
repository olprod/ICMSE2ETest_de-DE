# <a name="user-getmembergroups"></a>Benutzer: GetMemberGroups
Zurückgeben Sie aller Gruppen, denen der Benutzer Mitglied ist. Die Überprüfung ist transitiv, im Gegensatz zu lesen die [Mitglied](../api/user_list_memberof.md) Navigation-Eigenschaft gibt nur die Gruppen, denen der Benutzer ein direktes Mitglied ist.

Diese Funktion unterstützt Office 365 und anderen Arten von Gruppen in Azure Active Directory bereitgestellt werden. Die maximale Anzahl von Gruppen, die jeder Anforderung zurückgeben kann ist 2046. Beachten Sie, dass Office 365 Gruppen Gruppen enthalten kann. Die Mitgliedschaft in einer Office 365-Gruppe ist also immer direkten.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *User.Read; User.ReadWrite; User.Read.All; User.ReadWrite.All; Directory.Read.All; Directory.ReadWrite.All; Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/getMemberGroups
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
|securityEnabledOnly|Boolean|**true** gibt an, dass nur Sicherheitsgruppen, dass der Benutzer Mitglied ist zurückgegeben werden soll. **false,** um anzugeben, dass alle Gruppen, bei denen der Benutzer Mitglied ist zurückgegeben werden sollen. Hinweis: Die Funktion kann nur auf einem bestimmten Benutzer aufgerufen werden, wenn der Parameter auf **true**festgelegt ist.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortcode und zeichenfolgenauflistung im Textkörper Antwort, die die IDs der Gruppen enthält, die der Benutzer Mitglied ist.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "user_getmembergroups"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/getMemberGroups
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
  "description": "user: getMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
