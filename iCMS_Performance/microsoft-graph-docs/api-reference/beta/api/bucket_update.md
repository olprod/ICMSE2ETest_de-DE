# <a name="update-bucket"></a>Bucket aktualisieren

Aktualisieren Sie die Eigenschaften des Bucket-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /buckets/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |
| If-Match | string | Wert sollte auf den ETag des Objekts festgelegt werden |
| Bevorzugen | string | Wert festgelegt werden sollte, um "zurückgeben = Darstellung" so, dass das aktualisierte Objekt in der Antwort zurückgegeben wird. Dies wird empfohlen, damit der Client den neuen ETag-Wert des aktualisierten Objekts bekommen, ohne eine zusätzliche GET |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|name|String|Name des Bucket.|
|orderHint|String|Verwendet, um die relative Reihenfolge der Buckets in der Vorgangsansicht Pinnwand festzulegen. Berücksichtigen Sie drei Buckets in der Reihenfolge der: `'E'`, `'F'`, `'G'`. So tätigen `'F'` der erste Bucket, legen seine `'orderHint'` zu kleiner als der von `'x'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|"PlanID"|String|Plan-Id zu dem Bucket gehört.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `204 No Content` Antwortcode.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_bucket"
}-->
```http
PATCH https://graph.microsoft.com/beta/buckets/<id>
Content-type: application/json
Content-length: 108
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.bucket"
} -->
```http
HTTP/1.1 204 No Content
```
Wenn Sie das aktualisierte Objekt erhalten möchten, verwenden Sie die `Prefer` Kopfzeile. Finden Sie unter Anforderungsheader oben.
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update bucket",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->