# <a name="section-copytonotebook"></a>Abschnitt: CopyToNotebook
Kopiert einen Abschnitt in einem bestimmten-Notizbuch.

Führen Sie für Copy-Vorgänge ein Muster für die asynchrones aufrufende: Rufen Sie zunächst die Aktion kopieren, und Fragen Sie den Vorgang Endpunkt für das Ergebnis.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/sections/<id>/copyToNotebook
POST /users/<id | userPrincipalName>/notes/sections/<id>/copyToNotebook
POST /groups/<id>/notes/sections/<id>/copyToNotebook
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Inhaltstyp | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt, das die Parameter enthält, die der Vorgang.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|groupId|String|Die Id der Gruppe zu kopieren. Verwenden Sie nur, wenn ein Office 365-Gruppe zu kopieren.|
|id|String|Erforderlich. Die Id des Notizbuchs Ziel. |
|renameAs|String|Der Name der Kopie. Der Standardwert ist der Name des vorhandenen Elements. |

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode eine `202 Accepted` Antwortcode und ein `Operation-Location` Kopfzeile. Abfragen der Vorgang standortendpunkts zum [Abrufen des Status des Kopiervorgangs](notesoperation_get.md)an.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "section_copytonotebook"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/sections/<id>/copyToNotebook
Content-type: application/json
Content-length: 84

{
  "id": "id-value",
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
  "description": "section: copyToNotebook",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->