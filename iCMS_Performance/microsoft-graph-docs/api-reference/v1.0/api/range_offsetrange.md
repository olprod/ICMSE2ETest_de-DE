# <a name="range-offsetrange"></a>Bereich: OffsetRange

Ruft ein Objekt, das einen Bereich darstellt, der gegenüber dem angegebenen Bereich versetzt ist. Die Dimension der zurückgegebene Bereich entspricht diesem Bereich. Wenn der resultierende Bereich außerhalb des Arbeitsblatts Raster erzwungen wird, wird eine Ausnahme ausgelöst.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/names(<name>)/range/OffsetRange
POST /workbook/worksheets(<id|name>)/range(<address>)/OffsetRange
POST /workbook/tables(<id|name>)/columns(<id|name>)/range/OffsetRange

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|rowOffset|number|Der Anzahl der Zeilen (positiv, negativ oder 0), wird der Bereich versetzt werden soll. Positive Werte Versatz nach unten, und negative Werte nach oben versetzt.|
|columnOffset|number|Die Anzahl der Spalten (positiv, negativ oder 0), wird der Bereich versetzt werden soll. Positive Werte werden rechts versetzt, und negative Werte werden auf der linken Seite versetzt.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortcode und [Range](../resources/range.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "range_offsetrange"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/names(<name>)/range/OffsetRange
Content-type: application/json
Content-length: 49

{
  "rowOffset": {
  },
  "columnOffset": {
  }
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.range"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 169

{
  "address": "address-value",
  "addressLocal": "addressLocal-value",
  "cellCount": 99,
  "columnCount": 99,
  "columnIndex": 99,
  "valueTypes": "valueTypes-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Range: OffsetRange",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->