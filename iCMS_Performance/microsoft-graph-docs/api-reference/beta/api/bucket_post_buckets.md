# <a name="create-bucket"></a>Erstellen von bucket

Verwenden Sie diese API, um eine neue Bucket erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /buckets

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Bucket](../resources/bucket.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Code und [Bucket](../resources/bucket.md) Antwortobjekt im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_bucket_from_buckets"
}-->
```http
POST https://graph.microsoft.com/beta/buckets
Content-type: application/json
Content-length: 88

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Bucket](../resources/bucket.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.bucket"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 108

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create bucket",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->