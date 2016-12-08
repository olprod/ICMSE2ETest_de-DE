# <a name="update-chart"></a>Aktualisieren des Diagramms

Aktualisieren Sie die Eigenschaften des Chart-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|height|double|Die Höhe in Punkt, der das Chart-Objekt darstellt.|
|left|double|Der Abstand zwischen der linken Seite des Diagramms in Arbeitsblatt Ursprung in Punkt.|
|name|string|Den Namen des ein Chart-Objekt darstellt.|
|top|double|Stellt den Abstand in Punkt vom oberen Rand des Objekts an den Anfang der Zeile 1 (auf einem Arbeitsblatt) oder im oberen Bereich des Diagrammbereichs (in einem Diagramm).|
|width|double|Die Breite in Punkt, der das Chart-Objekt darstellt.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [Chart](../resources/chart.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_chart"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)
Content-type: application/json
Content-length: 52

{
  "id": "id-value",
  "height": 99,
  "left": 99
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chart"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 52

{
  "id": "id-value",
  "height": 99,
  "left": 99
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chart",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->