# <a name="update-chartdatalabels"></a>Chartdatalabels aktualisieren

Aktualisieren Sie die Eigenschaften des Chartdatalabels-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/datalabels
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|position|string|DataLabelPosition-Wert, der die Position der Datenbeschriftung darstellt. Possible values are: `None`, `Center`, `InsideEnd`, `InsideBase`, `OutsideEnd`, `Left`, `Right`, `Top`, `Bottom`, `BestFit`, `Callout`.|
|Separator|string|Eine Zeichenfolge, die das Trennzeichen für die datenbeschriftungen in einem Diagramm darstellt.|
|showBubbleSize|boolean|Boolean-Wert, der darstellt, wenn die Daten Blasengröße bezeichnen ist sichtbar oder nicht.|
|showCategoryName|boolean|Boolean-Wert, darstellt, wenn die Daten Kategoriename bezeichnen ist sichtbar oder nicht.|
|showLegendKey|boolean|Boolean-Wert, wenn die Daten, Legendensymbol bezeichnen darstellt ist sichtbar oder nicht.|
|showPercentage|boolean|Boolean-Wert zurück, wenn die Daten Prozentsatz bezeichnen darstellt ist sichtbar oder nicht.|
|showSeriesName|boolean|Boolean-Wert zurück, wenn die Daten Datenreihennamen bezeichnen darstellt ist sichtbar oder nicht.|
|showValue|boolean|Boolean-Wert zurück, wenn die Daten Wert beschriften darstellt ist sichtbar oder nicht.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierten [ChartDataLabels](../resources/chartdatalabels.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
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
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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