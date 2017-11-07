# <a name="update-plandetails"></a>Plandetails aktualisieren

Aktualisieren Sie die Eigenschaften des Plandetails-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /plans/<id>/details

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |
| If-Match | string | Wert sollte auf den ETag des Objekts festgelegt werden |
| Bevorzugen | string | Wert festgelegt werden sollte, um "zurückgeben = Darstellung" so, dass das aktualisierte Objekt in der Antwort zurückgegeben wird. Dies wird empfohlen, damit der Client den neuen ETag-Wert des aktualisierten Objekts bekommen, ohne eine zusätzliche GET |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|category0Description|String|Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann.|
|category1Description|String|Beschreibung der Kategorie (oder Beschriftung), die die Aufgabe zugewiesen werden kann.|
|category2Description|String|Beschreibung der Kategorie (oder Beschriftung), die die Aufgabe zugewiesen werden kann.|
|category3Description|String|Beschreibung der Kategorie (oder Beschriftung), die die Aufgabe zugewiesen werden kann.|
|category4Description|String|Beschreibung der Kategorie (oder Beschriftung), die die Aufgabe zugewiesen werden kann.|
|category5Description|String|Beschreibung der Kategorie (oder Beschriftung), die die Aufgabe zugewiesen werden kann.|
|sharedWith|[userIdCollection](../resources/useridcollection.md)| Liste der Benutzer-Ids, denen mit diesem Plan freigegeben werden. Wenn Sie Office 365 Gruppen nutzen, verwenden Sie die API-Gruppen zum Verwalten der Gruppenmitgliedschaft zum Planen der Gruppe freigeben. Sie können auch vorhandene Mitglieder der Gruppe zu dieser Auflistung hinzufügen, obwohl es nicht erforderlich, damit sie Zugriff auf den Besitz der Gruppe Plan ist.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `204 No Content` Antwortcode.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_plandetails"
}-->
```http
PATCH https://graph.microsoft.com/beta/plans/<id>/details
Content-type: application/json
Content-length: 381
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "sharedWith": {
  },
  "category0Description": "category0Description-value",
  "category1Description": "category1Description-value",
  "category2Description": "category2Description-value",
  "category3Description": "category3Description-value",
  "category4Description": "category4Description-value",
  "category5Description": "category5Description-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plandetails"
} -->
```http
HTTP/1.1 204 No Content
```
Wenn Sie das aktualisierte Objekt erhalten möchten, verwenden Sie die `Prefer` Kopfzeile. Finden Sie unter Anforderungsheader oben.
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update plandetails",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->