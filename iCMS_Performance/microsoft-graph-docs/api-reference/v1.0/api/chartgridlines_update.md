# <a name="update-chartgridlines"></a>Chartgridlines aktualisieren

Aktualisieren Sie die Eigenschaften des Chartgridlines-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/minorgridlines
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/majorgridlines
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/seriesaxis/majorgridlines
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|visible|boolean|Boolescher Wert, wenn die Gitternetzlinien sichtbar sind.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierten [ChartGridlines](../resources/chartgridlines.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_chartgridlines"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis/minorgridlines
Content-type: application/json
Content-length: 21

{
  "visible": true
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartGridLines"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 21

{
  "visible": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chartgridlines",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->