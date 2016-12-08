# <a name="create-tablecolumn"></a>TableColumn erstellen

Verwenden Sie diese API, um eine neue TableColumn erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables(<id|name>)/columns
POST /workbook/worksheets(<id|name>)/tables(<id|name>)/columns

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der [TableColumn](../resources/tablecolumn.md) -Objekt.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und [TableColumn](../resources/tablecolumn.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_tablecolumn_from_table"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/tables(<id|name>)/columns
Content-type: application/json
Content-length: 81

{
  "id": 99,
  "name": "name-value",
  "index": 99,
  "values": "values-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der [TableColumn](../resources/tablecolumn.md) -Objekt.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tableColumn"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 81

{
  "id": 99,
  "name": "name-value",
  "index": 99,
  "values": "values-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create TableColumn",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->