# <a name="update-chartfont"></a>Update chartfont

Update the properties of chartfont object.
## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/format/font
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/seriesaxis/format/font
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/categoryaxis/format/font
```
## <a name="optional-request-headers"></a>Optional request headers
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer <code>|


## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|bold|boolean|Stellt den Fett-Status der Schriftart dar.|
|color|string|HTML-Farbcodedarstellung der Textfarbe. #ff0000 stellt beispielsweise Rot dar.|
|Kursiv|boolean|Stellt den Kursiv-Status der Schriftart dar.|
|name|string|Schriftartname (z. B. "Calibri")|
|Schriftgröße|double|Der Schriftgrad (z. B. 11)|
|Unterstreichen|string|Art der auf die Schriftart angewendete Unterstreichung. Die folgenden Werte sind möglich: Keine, einfache.|

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and updated [ChartFont](../resources/chartfont.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "update_chartfont"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/format/font
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
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
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
  "description": "Update chartfont",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->