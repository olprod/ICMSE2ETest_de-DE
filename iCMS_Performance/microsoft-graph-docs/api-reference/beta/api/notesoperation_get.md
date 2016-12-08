# <a name="get-notesoperation"></a>Abrufen von notesOperation


Abrufen des Status eines Vorgangs langer OneNote. Dies gilt für Vorgänge, die den **Vorgang-Location-** Header in der Antwort, z. B. zurückgeben `CopyNotebook`, `CopyToNotebook`, `CopyToSectionGroup`, `and CopyToSection`.   

Sie können den Vorgang standortendpunkts bis zum Abrufen der `status` -Eigenschaft gibt `completed` oder `failed`. 

Wenn der Status `completed`, die `resourceLocation` -Eigenschaft enthält den Ressourcenendpunkt-URI. 

Ist der Status `failed`, den Fehler und `@api.diagnostics` Eigenschaften liefert Fehlerinformationen.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:  
Notes.Read, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, Notes.Read.All oder Notes.ReadWrite.All  
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/operations/<id>
GET /users/<id | userPrincipalName>/notes/operations/<id>
GET /groups/<id>/notes/operations/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Keine.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Akzeptieren | string | `application/json` | 

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortobjekt Code und [NotesOperation](../resources/notesoperation.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_notesoperation"
}-->
```http
GET https://graph.microsoft.com/beta/me/notes/operations/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.notesoperation"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "id": "id-value",
  "status": "status-value",
  "createdDateTime": "datetime-value",
  "lastActionDateTime": "datetime-value",
  "resourceLocation": "resourceLocation-value",
  "resourceId": "resourceId-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get notesOperation",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->