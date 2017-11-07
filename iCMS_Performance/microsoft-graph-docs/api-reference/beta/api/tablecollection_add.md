# <a name="tablecollection-add"></a>TableCollection: Hinzufügen

Erstellen Sie eine neue Tabelle. Die Bereich Quelladresse bestimmt das Arbeitsblatt, unter dem die Tabelle hinzugefügt werden. Falls die Tabelle (z. B., da die Adresse ungültig ist oder die Tabelle mit einer anderen Tabelle überlappen würde) hinzugefügt werden kann, wird ein Fehler ausgelöst.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables/add
POST /workbook/worksheets(<id|name>)/tables/add

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|address|string|Adresse oder den Namen des Range-Objekts, die die Datenquelle darstellt. Wenn die Adresse nicht mit einen Blattnamen enthält, wird das derzeit aktive Blatt verwendet.|
|hasHeaders|boolean|Boolescher Wert, der angibt, ob für die importierten Daten Spaltenüberschriften. Wenn die Datenquelle keinen Header (z. B.. Wenn diese Eigenschaft auf False festgelegt), Excel generiert automatisch Kopfzeile, die die Daten nach unten verschieben, um eine Zeile.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode und [Table](../resources/table.md) -Objekt in der Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "tablecollection_add"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/tables/add
Content-type: application/json
Content-length: 54

{
  "address": "address-value",
  "hasHeaders": true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "TableCollection: add",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->