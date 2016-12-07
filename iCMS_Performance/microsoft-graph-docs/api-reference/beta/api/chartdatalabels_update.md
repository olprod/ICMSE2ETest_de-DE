# <a name="update-chartdatalabels"></a>Update chartdatalabels

Update the properties of chartdatalabels object.
## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/datalabels
```
## <a name="optional-request-headers"></a>Optional request headers
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer <code>|


## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|position|string|DataLabelPosition-Wert, der die Position der Datenbeschriftung darstellt. Die folgenden Werte sind möglich: Keine, Mitte, InsideEnd, InsideBase, OutsideEnd, links, rechts, oben, unten, BestFit, Callout. Schreibzugriff.|
|Separator|string|Zeichenfolge, die das Trennzeichen für die Datenbeschriftungen in einem Diagramm darstellt. Schreibzugriff.|
|showBubbleSize|boolean|Boolescher Wert, der angibt, ob die Größe der Datenbeschriftungs-Sprechblase angezeigt wird. Schreibzugriff.|
|showCategoryName|boolean|Boolescher Wert, der angibt, ob der Kategoriename der Datenbeschriftung angezeigt wird. Schreibzugriff.|
|showLegendKey|boolean|Boolescher Wert, der angibt, ob das Legendensymbol der Datenbeschriftung angezeigt wird. Schreibzugriff.|
|showPercentage|boolean|Boolescher Wert, der angibt, ob der Prozentsatz der Datenbeschriftung angezeigt wird. Schreibzugriff.|
|showSeriesName|boolean|Boolescher Wert, der angibt, ob der Name der Datenbeschriftungsreihe angezeigt wird. Schreibzugriff.|
|showValue|boolean|Boolescher Wert, der angibt, ob der Datenbeschriftungswert angezeigt wird. Schreibzugriff.|

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and updated [ChartDataLabels](../resources/chartdatalabels.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "update_chartdatalabels"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/datalabels
Content-type: application/json
Content-length: 134

{
  "position": "position-value",
  "showValue": true,
  "showSeriesName": true,
  "showCategoryName": true,
  "showLegendKey": true
}
```
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartDataLabels"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 134

{
  "position": "position-value",
  "showValue": true,
  "showSeriesName": true,
  "showCategoryName": true,
  "showLegendKey": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chartdatalabels",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->