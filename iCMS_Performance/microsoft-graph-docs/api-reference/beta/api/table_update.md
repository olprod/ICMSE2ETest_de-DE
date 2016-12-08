# <a name="update-table"></a>Aktualisieren Sie die Tabelle

Aktualisieren Sie die Eigenschaften des Table-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/tables(<id|name>)
PATCH /workbook/worksheets(<id|name>)/tables(<id|name>)
```
## <a name="optional-request-headers"></a>Optional Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind verwalten ihre vorherigen Werte oder neu berechnet auf der Grundlage Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|name|string|Name der Tabelle.|
|showHeaders|boolean|Gibt an, ob die Kopfzeile angezeigt wird. Dieser Wert kann zum Anzeigen oder entfernen die Kopfzeile festgelegt werden.|
|showTotals|boolean|Gibt an, ob die Ergebniszeile sichtbar ist. Dieser Wert kann ein-oder entfernen die gesamte Zeile festgelegt werden.|
|style|string|Konstanter Wert, der die Tabellenformatvorlage repräsentiert. Mögliche Werte sind: TableStyleLight1 bis TableStyleLight21 TableStyleMedium1 bis TableStyleMedium28 TableStyleStyleDark1 bis TableStyleStyleDark11. Eine benutzerdefinierte benutzerdefinierte Formatvorlage in der Arbeitsmappe vorhanden kann auch angegeben.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierten [Table](../resources/table.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_table"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/tables(<id|name>)
Content-type: application/json
Content-length: 109

{
  "id": 99,
  "name": "name-value",
  "showHeaders": true,
  "showTotals": true,
  "style": "style-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.table"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 109

{
  "id": 99,
  "name": "name-value",
  "showHeaders": true,
  "showTotals": true,
  "style": "style-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update table",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->