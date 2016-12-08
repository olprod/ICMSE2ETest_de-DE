# <a name="list-plans"></a>Liste Pläne

Abrufen einer Liste der [Plan](../resources/plan.md) Objekte im Besitz der Gruppe an. Eine Gruppe kann heute nicht mehr als einen Plan besitzen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 

Groups.ReadWrite.All UND Tasks.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/plans
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
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [Plan](../resources/plan.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_plans"
}-->
```http
GET https://graph.microsoft.com/beta/groups/<id>/plans
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plan",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 153

{
  "value": [
    {
      "createdBy": "createdBy-value",
      "owner": "owner-value",
      "title": "title-value",
      "id": "id-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List plans",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->