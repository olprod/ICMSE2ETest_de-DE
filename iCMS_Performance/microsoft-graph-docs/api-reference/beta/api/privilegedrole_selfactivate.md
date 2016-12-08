# <a name="privilegedrole-selfactivate"></a>PrivilegedRole: SelfActivate
Aktivieren Sie die Rolle, die an den Requestor zugewiesen ist.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: _Directory.AccessAsUser.All_

Der Requestor kann nur aufgerufen ```selfActivate``` für die Rolle, die ihm zugewiesen ist.
 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /privilegedRoles/<id>/selfActivate
```

Beachten Sie, dass ``<id>`` ist die Id der Ziel-Rolle.
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Grund|string|Optional Beschreibung der Grund für diese Rolle Aktivierung.|
|duration|string|Optional Gültige Werte werden konnte ```min``` (minimale Aktivierung Dauer), ```default``` (Standard Aktivierung Dauer für die Rolle), oder einen double-Wert an, wie viele Stunden die Aktivierung ist. Die angegebene Dauer darf nicht länger als die Rolle Aktivierung Dauer aus der Einstellung der Rolle sein. |
|ticketNumber|string|Optional Die Ticket-Nummer, die zum Nachverfolgen von dieser Rolle-Aktivierung verwendet wird.|
|ticketSystem|string|Optional Das System Ticket.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortobjekt Code und [PrivilegedRoleAssignment](../resources/privilegedroleassignment.md) im Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "privilegedrole_selfactivate"
}-->
```http
POST https://graph.microsoft.com/beta/privilegedRoles/<id>/selfActivate
Content-type: application/json
Content-length: 142

{
  "reason": "reason-value",
  "duration": "duration-value",
  "ticketNumber": "ticketNumber-value",
  "ticketSystem": "ticketSystem-value"
}
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
  "description": "privilegedRole: selfActivate",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->