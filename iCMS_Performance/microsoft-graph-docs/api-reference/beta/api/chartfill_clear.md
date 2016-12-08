# <a name="chartfill-clear"></a>ChartFill: Deaktivieren

Deaktivieren Sie die Füllfarbe des Diagrammelements.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/worksheets(<id|name>)/charts(<name>)/format/fill/clear
POST /workbook/worksheets(<id|name>)/charts(<name>)/title/format/fill/clear
POST /workbook/worksheets(<id|name>)/charts(<name>)/legend/format/fill/clear

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode. Es werden keine etwas in der Antworttext zurückgegeben.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "chartfill_clear"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/format/fill/clear
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.none"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartFill: clear",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->