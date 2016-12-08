# <a name="update-formatprotection"></a>Formatprotection aktualisieren

Aktualisieren Sie die Eigenschaften des Formatprotection-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/names(<name>)/range/format/protection
PATCH /workbook/worksheets(<id|name>)/range(<address>)/format/protection
PATCH /workbook/tables(<id|name>)/columns(<id|name>)/range/format/protection
```
## <a name="optional-request-headers"></a>Optionale Anforderungsheader
| Name       | Beschreibung|
|:-----------|:-----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|formulaHidden|boolean|Gibt an, ob Excel die Formel für die Zellen im Bereich werden ausgeblendet. Ein null-Wert gibt an, dass der gesamte Bereich uniform Formel ausgeblendete Einstellung hat.|
|gesperrt|boolean|Gibt an, ob Excel die Zellen in das Objekt gesperrt. Ein null-Wert gibt an, dass der gesamte Bereich uniform Sperrung nicht.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [FormatProtection](../resources/formatprotection.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_formatprotection"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/names(<name>)/range/format/protection
Content-type: application/json
Content-length: 45

{
  "locked": true,
  "formulaHidden": true
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.formatProtection"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 45

{
  "locked": true,
  "formulaHidden": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update formatprotection",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->