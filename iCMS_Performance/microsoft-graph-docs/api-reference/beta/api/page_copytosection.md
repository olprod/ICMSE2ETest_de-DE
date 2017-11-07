# <a name="page-copytosection"></a>Seite: CopyToSection
Kopiert eine Seite auf einen bestimmten Abschnitt.

Führen Sie für Copy-Vorgänge ein Muster für die asynchrones aufrufende: Rufen Sie zunächst die Aktion kopieren, und Fragen Sie den Vorgang Endpunkt für das Ergebnis.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All  
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/pages/<id>/copyToSection
POST /users/<id | userPrincipalName>/notes/pages/<id>/copyToSection
POST /groups/<id>/notes/pages/<id>/copyToSection
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
|id|String|Erforderlich. Die Id des im Zielabschnitt.|


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode eine `202 Accepted` Antwortcode und ein `Operation-Location` Kopfzeile. Abfragen der Vorgang standortendpunkts zum [Abrufen des Status des Kopiervorgangs](notesoperation_get.md)an.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "page_copytosection"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/pages/<id>/copyToSection
Content-type: application/json
Content-length: 52

{
  "id": "id-value",
  "groupId": "groupId-value"
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
  "description": "page: copyToSection",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->