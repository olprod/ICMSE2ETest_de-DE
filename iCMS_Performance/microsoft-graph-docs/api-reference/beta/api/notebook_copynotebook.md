# <a name="notebook-copynotebook"></a>Notizbuch: CopyNotebook
Kopiert ein Notizbuch in den Notizbücher-Ordner in der Ziel-Bibliothek Dokumente. Der Ordner wird erstellt, wenn er nicht vorhanden ist.

Führen Sie für Copy-Vorgänge ein Muster für die asynchrones aufrufende: Rufen Sie zunächst die Aktion kopieren, und Fragen Sie den Vorgang Endpunkt für das Ergebnis.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/notebooks/<id>/copyNotebook
POST /users/<id | userPrincipalName>/notes/notebooks/<id>/copyNotebook
POST /groups/<id>/notes/notebooks/<id>/copyNotebook
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Inhaltstyp | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt, das die Parameter enthält, die der Vorgang. Es ist kein Problem einem leeren Meldungstext senden, wenn keine benötigt werden.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|groupId|String|Die Id der Gruppe zu kopieren. Verwenden Sie nur, wenn ein Office 365-Gruppe zu kopieren.|
|renameAs|String|Der Name der Kopie. Der Standardwert ist der Name des vorhandenen Elements. |


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode eine `202 Accepted` Antwortcode und ein `Operation-Location` Kopfzeile. Abfragen der Vorgang standortendpunkts zum [Abrufen des Status des Kopiervorgangs](notesoperation_get.md)an.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "notebook_copynotebook"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/notebooks/<id>/copyNotebook
Content-type: application/json
Content-length: 108

{
  "groupId": "groupId-value",
  "renameAs": "renameAs-value"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.copystatusmodel"
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notebook: copyNotebook",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->