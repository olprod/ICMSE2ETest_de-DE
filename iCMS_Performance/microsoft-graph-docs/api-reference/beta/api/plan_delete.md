# <a name="delete-plan"></a>Plan löschen

Löschen Sie Plan.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /plans/<id>

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| If-Match | string | Wert sollte auf den ETag des Objekts festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "delete_plan"
}-->
```http
DELETE https://graph.microsoft.com/beta/plans/<id>
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
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
  "description": "Delete plan",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->