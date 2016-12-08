# <a name="delete-connectorgroup"></a>ConnectorGroup löschen

Löschen einer ConnectorGroup.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.ReadWrite.All oder Directory.AccessAsUser.All*

> **Hinweis:** Die Gruppe Connectors darf keine Connectors zugeordnet haben.

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /connectorGroups/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer. Erforderlich|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_connectorgroup"
}-->
```http
DELETE https://graph.microsoft.com/{ver}/connectorGroups/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete connectorGroup",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
