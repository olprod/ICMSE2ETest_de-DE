# <a name="get-chartfont"></a>ChartFont abrufen

Rufen Sie die Eigenschaften und Beziehungen zwischen Chartfont-Objekt ab.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/format/font
GET /workbook/worksheets(<id|name>)/charts(<name>)/axes/seriesaxis/format/font
GET /workbook/worksheets(<id|name>)/charts(<name>)/axes/categoryaxis/format/font
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und [ChartFont](../resources/chartfont.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_chartfont"
}-->
```http
GET https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/format/font
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartFont"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 134

{
  "bold": true,
  "color": "color-value",
  "italic": true,
  "name": "name-value",
  "size": 99,
  "underline": "underline-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get ChartFont",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->