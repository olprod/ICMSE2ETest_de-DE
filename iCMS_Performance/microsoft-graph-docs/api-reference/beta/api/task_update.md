# <a name="update-task"></a>Update-task

Aktualisieren Sie die Eigenschaften des Task-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /tasks/<id>

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden|
| If-Match | string | Wert sollte auf den ETag des Objekts festgelegt werden |
| Bevorzugen | string | Wert festgelegt werden sollte, um "zurückgeben = Darstellung" so, dass das aktualisierte Objekt in der Antwort zurückgegeben wird. Dies wird empfohlen, damit der Client den neuen ETag-Wert des aktualisierten Objekts bekommen, ohne eine zusätzliche GET |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|appliedCategories|[appliedCategoriesCollection](../resources/appliedcategoriescollection.md)|Die Kategorien, auf denen die Aufgabe angewendet wurde. Finden Sie unter AppliedCategoriesCollection für mögliche Werte. |
|assignedTo|String|Benutzer-Id, denen die Aufgabe zugewiesen ist.|
|assigneePriority|String|Zum Festlegen der Reihenfolge der relativen Priorität Aufgaben zugewiesen sind, die dem Benutzer in einer Listenansicht verwendet. Betrachten Sie drei Vorgänge in der Reihenfolge der Priorität: `'A'`, `'B'`, `'C'`. So verschieben Sie `'B'` festlegen im oberen Bereich, dessen `assignneePriority` zu kleiner als der von `'A'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|bucketId|String|Bucket-Id, zu der die Aufgabe gehört. Der Bucket muss im Plan sein, die die Aufgabe ist.|
|conversationThreadId|String|Thread-Id der Unterhaltung auf die Aufgabe. Dies ist die Id des Unterhaltung Thread-Objekts in der Gruppe erstellt.|
|dueDateTime|DateTimeOffset|Datum und Uhrzeit, an dem die Aufgabe fällig ist. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|orderHint|String|Verwendet, um die relative Reihenfolge der Aufgaben in einer Listenansicht festzulegen. Betrachten Sie drei Vorgänge in der Reihenfolge der: `'X'`, `'Y'`, `'Z'`. So verschieben Sie `'Y'` festlegen im oberen Bereich, dessen `orderHint` zu kleiner als der von `'X'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|percentComplete|Int32|Prozentsatz der Fertigstellung des Vorgangs. Bei Festlegung auf `100`, gilt die Aufgabe als abgeschlossen.|
|startDateTime|DateTimeOffset|Datum und Uhrzeit, an dem die Aufgabe beginnt. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|title|String|Titel der Aufgabe.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `204 No Content` Antwortcode.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_task"
}-->
```http
PATCH https://graph.microsoft.com/beta/tasks/<id>
Content-type: application/json
Content-length: 663
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "assignedTo": "assignedTo-value",
  "bucketId": "bucketId-value",
  "title": "title-value",
  "orderHint": "orderHint-value",
  "assigneePriority": "assigneePriority-value",
  "percentComplete": 99,
  "startDateTime": "datetime-value",
  "dueDateTime": "datetime-value",
  "previewType": "previewType-value",
  "appliedCategories": {
  },
  "conversationThreadId": "conversationThreadId-value",
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.task"
} -->
```http
HTTP/1.1 204 No Content
```
Wenn Sie das aktualisierte Objekt erhalten möchten, verwenden Sie die `Prefer` Kopfzeile. Finden Sie unter Anforderungsheader oben.
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update task",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->