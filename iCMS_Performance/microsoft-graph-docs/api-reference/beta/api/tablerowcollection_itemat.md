# <a name="tablerowcollection-itemat"></a>TableRowCollection: ItemAt

Ruft eine Zeile basierend auf seine Position in der Auflistung ab.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /workbook/tables(<id|name>)/rows/ItemAt(index=n)
GET /workbook/worksheets(<id|name>)/tables(<id|name>)/rows/ItemAt(index=n)

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Index|number|Der Indexwert des Objekts abgerufen werden sollen. 0 (null) indiziert.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode und [TableRow](../resources/tablerow.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung. 1. Zeile zurückgegeben. 
<!-- {
  "blockType": "request",
  "name": "tablerowcollection_itemat"
}-->
```http
GET https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/tables(<id|name>)/rows/ItemAt(0)
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tableRow"
} -->
```http
HTTP/1.1 200 OK
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
  "description": "TableRowCollection: ItemAt",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
