# <a name="privilegedroleassignment-makeeligible"></a>PrivilegedRoleAssignment: MakeEligible
Stellen Sie die rollenzuweisung als geeignet. Wenn die rollenzuweisung bereits vor dem Aufruf berechtigt ist, hat keine Auswirkung. Wenn die rollenzuweisung dauerhaft gelöscht wird und der Requestor unterscheidet sich von der Zielbenutzer, die rollenzuweisung wird sind berechtigt, und die Rolle wird für die Zielbenutzer deaktiviert werden. Wenn der Requestor Zielbenutzers und die Rolle Sicherheitsadministrator oder privilegierten Rollen-Administrator ist, wird die Rolle das standardmäßige Ablaufdatum aktiviert werden.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: _Directory.AccessAsUser.All_


Der Requestor muss _privilegierten Rolle_ Administratorrolle haben. 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /privilegedRoleAssignments/<id>/makeEligible
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortobjekt Code und [PrivilegedRoleAssignment](../resources/privilegedroleassignment.md) im Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "privilegedroleassignment_makeeligible"
}-->
```http
POST https://graph.microsoft.com/beta/privilegedRoleAssignments/<id>/makeEligible
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedRoleAssignment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 184

{
  "id": "id-value",
  "userId": "userId-value",
  "roleId": "roleId-value",
  "isElevated": true,
  "expirationDateTime": "datetime-value",
  "resultMessage": "resultMessage-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleAssignment: makeEligible",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->