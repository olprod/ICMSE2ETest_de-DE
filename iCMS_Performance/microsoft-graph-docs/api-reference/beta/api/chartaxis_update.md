# <a name="update-chartaxis"></a>Chartaxis aktualisieren

Aktualisieren Sie die Eigenschaften des Chartaxis-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/seriesaxis
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/categoryaxis
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|majorUnit|object|Stellt das Intervall zwischen zwei Hauptteilstriche dar. Kann auf einen numerischen Wert oder eine leere Zeichenfolge festgelegt werden.  Der zurückgegebene Wert ist immer eine Zahl.|
|maximum|object|Stellt den Maximalwert für die Größenachse.  Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt sein.  Der zurückgegebene Wert ist immer eine Zahl.|
|minimum|object|Stellt den kleinsten Wert für die Größenachse. Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt sein.  Der zurückgegebene Wert ist immer eine Zahl.|
|minorUnit|object|Stellt das Intervall zwischen zwei Hilfsteilstriche dar. "Kann auf einen numerischen Wert oder eine leere Zeichenfolge (für automatische Achsenwerte) festgelegt werden. Der zurückgegebene Wert ist immer eine Zahl.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierten [ChartAxis](../resources/chartaxis.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_chartaxis"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis
Content-type: application/json
Content-length: 64

{
  "majorUnit": {
  },
  "maximum": {
  },
  "minimum": {
  }
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartaxis"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 64

{
  "majorUnit": {
  },
  "maximum": {
  },
  "minimum": {
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chartaxis",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->