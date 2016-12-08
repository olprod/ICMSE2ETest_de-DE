# <a name="get-plantaskboard"></a>Abrufen von planTaskBoard

Rufen Sie die Eigenschaften und Beziehungen Plantaskboard-Objekts ab.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.Read.All Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /plans/<id>/bucketTaskBoard
GET /plans/<id>/progressTaskBoard
GET /plans/<id>/assignedToTaskBoard
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Keine

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortobjekt Code und [PlanTaskBoard](../resources/plantaskboard.md) in den Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_plantaskboard"
}-->
```http
GET https://graph.microsoft.com/beta/plans/<id>/bucketTaskBoard
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plantaskboard"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 46

{
  "type": "type-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get planTaskBoard",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->