# <a name="get-page"></a>Erste Seite

Rufen Sie die Eigenschaften und die Beziehungen eines [Page](../resources/page.md) -Objekts ab.

**Erste Seiteninhalt**

Sie können der Seite `content` Endpunkt den HTML-Code Inhalt einer Seite abrufen:

```
GET /me/notes/pages/<id>/content[?includeIDs=true]
```

Die `includeIDs=true` Abfrageoption wird verwendet, um [Seiten zu aktualisieren](../api/page_update.md).

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:  
Notes.Read, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite, Notes.Read.All oder Notes.ReadWrite.All
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/pages/<id>
GET /users/<id | userPrincipalName>/notes/pages/<id>
GET /groups/<id>/notes/pages/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die `select` und `expand` [OData-Abfrageparameter](http://graph.microsoft.io/docs/overview/query_parameters) helfen, die Antwort anzupassen.

Erweitert die Standardantwort `parentSection` und wählt im Abschnitts `id`, `name`, und `self` Eigenschaften. Gültige `expand` Werte für Seiten `parentNotebook` und `parentSection`.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Akzeptieren | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und [Page](../resources/page.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
 <!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/me/notes/pages/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
 <!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 312

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
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->