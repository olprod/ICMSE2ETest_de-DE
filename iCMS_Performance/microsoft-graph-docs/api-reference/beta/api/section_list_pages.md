# <a name="list-pages"></a>Listenseiten

Eine Liste der [Page](../resources/page.md) -Objekte im angegebenen Abschnitt abzurufen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:  
Notes.Read, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, Notes.Read.All oder Notes.ReadWrite.All
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/sections/<id>/pages
GET /users/<id | userPrincipalName>/notes/sections/<id>/pages
GET /groups/<id>/notes/sections/<id>/pages
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

Die Standardabfrage für Seiten gibt die ersten 20 Seiten nach sortiert `lastModifiedTime desc`. Die Standardabfrage mehr als 20 Seiten zurück, das die Antwort enthält eine `@odata.nextLink` , mit denen Sie können zur Seite durch die Ergebnismenge. Die maximale Anzahl von Seiten, die für eine `top` Anforderung ist 100.

Erweitert die Standardantwort `parentSection` und wählt im Abschnitts `id`, `name`, und `self` Eigenschaften. Gültige `expand` Werte für Seiten `parentNotebook` und `parentSection`.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Akzeptieren | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und eine Auflistung von [Page](../resources/page.md) -Objekte in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/me/notes/sections/<id>/pages
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 393

{
  "value": [
    {
      "title": "title-value",
      "createdByAppId": "createdByAppId-value",
      "links": {
        "oneNoteClientUrl": {
          "href": "href-value"
        },
        "oneNoteWebUrl": {
          "href": "href-value"
        }
      },
      "contentUrl": "contentUrl-value",
      "content": "content-value",
      "lastModifiedTime": "datetime-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List pages",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->