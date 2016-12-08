# <a name="update-approleassignment"></a>Approleassignment aktualisieren

Aktualisieren Sie die Eigenschaften des Approleassignment-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /users/<id | userPrincipalName>/appRoleAssignments/<id>
PATCH /servicePrincipals/<id>/appRoleAssignedTo
PATCH /groups/<id>/appRoleAssignments/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|creationTimestamp|DateTimeOffset|Die Uhrzeit der Erstellung der erteilen.|
|id|Guid|Die Rolle-Id, die den Prinzipal zugewiesen wurde.  Diese Rolle muss mit der Ziel-Ressource Anwendung **ResourceId** in seiner **AppRoles** -Eigenschaft deklariert werden. In denen die Ressource keine Berechtigungen nicht deklarieren, muss eine Standard-Id (0 (null) GUID) angegeben werden.                            **Notes**: nicht auf NULL festgelegt.            |
|principalDisplayName|String|Der Anzeigename des Prinzipals, denen den Zugriff gewährt wurde.|
|principalId|Guid|Der eindeutige Bezeichner (**ObjectId**) für den Prinzipal, den Zugriff gewährt wird.                            **Notes**: erforderlich.            |
|principalType|String|Der Typ des Prinzipals.  Dies kann entweder "User", "Group" oder "ServicePrincipal" sein.|
|resourceDisplayName|String|Der Anzeigename der Ressource mit der die Zuordnung hergestellt wurde.|
|resourceId|Guid|Der eindeutige Bezeichner (**ObjectId**) für die Zielressource (Service Principal) für die die Zuordnung erstellt wurde.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierten [AppRoleAssignment](../resources/approleassignment.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_approleassignment"
}-->
```http
PATCH https://graph.microsoft.com/beta/appRoleAssignments/<id>
Content-type: application/json
Content-length: 233

{
  "creationTimestamp": "datetime-value",
  "principalDisplayName": "principalDisplayName-value",
  "principalId": "principalId-value",
  "principalType": "principalType-value",
  "resourceDisplayName": "resourceDisplayName-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.approleassignment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 253

{
  "creationTimestamp": "datetime-value",
  "id": "id-value",
  "principalDisplayName": "principalDisplayName-value",
  "principalId": "principalId-value",
  "principalType": "principalType-value",
  "resourceDisplayName": "resourceDisplayName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update approleassignment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->