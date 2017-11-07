# <a name="activate-directoryrole"></a>DirectoryRole aktivieren

Eine Rolle Verzeichnis zu aktivieren. Um eine Rolle Directory lesen oder deren Member aktualisieren möchten, müssen sie zuerst im Mandanten aktiviert werden. Nur die Administratoren im Unternehmen und die impliziten Benutzer Directory Rollen sind standardmäßig aktiviert. Zugriff auf und Zuweisen von Mitgliedern zu einer anderen Verzeichnis Rolle, müssen Sie zuerst mit der entsprechenden Verzeichnis Role-Vorlage ([DirectoryRoleTemplate](../resources/directoryroletemplate.md)) aktivieren.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /directoryRoles

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [DirectoryRole](../resources/directoryrole.md) -Objekts.

In der folgenden Tabelle werden die Eigenschaften gezeigt, die erforderlich sind, wenn Sie eine Rolle Verzeichnis zu aktivieren.

|Erforderliche parameter | Typ | Beschreibung|
|:---------|:---------|:---------|
|roleTemplateId | string | Die ID des der [DirectoryRoleTemplate](../resources/directoryroletemplate.md) , die die Rolle basiert. Dies ist die einzige Eigenschaft, die in der Anforderung angegeben werden kann.|


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [DirectoryRole](../resources/directoryrole.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_directoryrole_from_directoryroles"
}-->
```http
POST https://graph.microsoft.com/beta/directoryRoles
Content-type: application/json
Content-length: 153

{
  "description": "description-value",
  "displayName": "displayName-value",
  "roleTemplateId": "roleTemplateId-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [DirectoryRole](../resources/directoryrole.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directoryRole"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 175

{
  "description": "description-value",
  "displayName": "displayName-value",
  "roleTemplateId": "roleTemplateId-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create directoryRole",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
