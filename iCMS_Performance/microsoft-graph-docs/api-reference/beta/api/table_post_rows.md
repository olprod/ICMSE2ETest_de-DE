# <a name="create-tablerow"></a>Create TableRow

Use this API to create a new TableRow.
## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables(<id|name>)/rows
POST /workbook/worksheets(<id|name>)/tables(<id|name>)/rows

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer <code>|


## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a JSON representation of [TableRow](../resources/tablerow.md) object.


## <a name="response"></a>Antwort
If successful, this method returns `201, Created` response code and [TableRow](../resources/tablerow.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_tablerow_from_table"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/tables(<id|name>)/rows
Content-type: application/json
Content-length: 45

{
  "index": 99,
  "values": "values-value"
}
```
In the request body, supply a JSON representation of [TableRow](../resources/tablerow.md) object.
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tableRow"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 45

{
  "index": 99,
  "values": "values-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create TableRow",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->