# <a name="update-range"></a>Update-Bereich

Aktualisieren Sie die Eigenschaften des Range-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/names(<name>)/range
PATCH /workbook/worksheets(<id|name>)/range(address=<range-address>)
PATCH /workbook/tables(<id|name>)/columns(<id|name>)/range
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|columnHidden|boolean|Stellt dar, wenn alle Spalten des aktuellen Bereichs ausgeblendet sind.|
|formulas|json|Stellt die Formel in A1-Schreibweise.|
|formulasLocal|json|Die Formel in A1-Schreibweise, in der Sprache und Formatieren von Zahlen Gebietsschema des Benutzers darstellt.  Beispielsweise würde die englische Formel "= SUM (A1, 1,5)" werden "= SUMME(A1; 1,5) "auf Deutsch.|
|formulasR1C1|json|Stellt die Formel in Z1S1-Schreibweise.|
|numberFormat|json|Excel Zahlenformat für die angegebene Zelle darstellt.|
|rowHidden|boolean|Stellt dar, ob alle Zeilen des aktuellen Bereichs ausgeblendet werden.|
|values|json|Die unformatierten Werte des angegebenen Bereichs darstellt. Die zurückgegebenen Daten konnte vom Typ String, Nummer oder ein boolescher Wert sein. Zelle, die Fehler enthalten, gibt die Fehlerzeichenfolge zurück.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierten [Range](../resources/range.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung. Ein Range - Werte, Zahlenformat und Formel aktualisiert. Die `null` Eingabe wird angewiesen, die API auf die Zelle für die bestimmten Eingabe ignorieren. Die Werte, Anzahl Format und Formeln können unabhängig voneinander aktualisiert oder kombiniert werden zusammen in derselben API-Aufruf. 

<!-- {
  "blockType": "request",
  "name": "update_range"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets('sheet1')/range(address='A1:B2')
Content-type: application/json
Content-length: 169

{
"values" : [["Hello", "100"],["1/1/2016", null]],
"formula" : [[null, null], [null, "=B1*2"]],
"numberFormat" : [[null,null], ["m-ddd", null]]
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "Update range",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
