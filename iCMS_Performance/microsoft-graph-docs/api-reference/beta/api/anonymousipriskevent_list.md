# <a name="list-anonymousipriskevents"></a>Liste anonymousIpRiskEvents

Abrufen einer Liste von Anonymousipriskevent-Objekten.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *IdentityRiskEvent.Read.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /anonymousIpRiskEvents
```

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|
| Arbeitsmappe-Sitzung-Id  | Arbeitsmappe Sitzung-Id, die bestimmt, ob Änderungen oder nicht beibehalten werden. Optional|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [AnonymousIpRiskEvent](../resources/anonymousipriskevent.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_anonymousipriskevents"
}-->
```http
GET https://graph.microsoft.com/v1.0/anonymousIpRiskEvents
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.anonymousIpRiskEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 290

{
  "value": [
    {
      "closedDateTime": "2016-01-29T20:03:57.7872426Z",
      "createdDateTime": "2016-01-29T00:01:49.126468Z",
      "id": "2016-01-29T00:00:56.22556656a56d0b2-3c51-7c5e-bc1a-1ccdb3bd9c71",
      "ipAddress": null,
      "location": null,
      "riskEventDateTime": "2016-01-29T00:00:56.2255665Z",
      "riskEventStatus": "remediated",
      "riskLevel": "medium",
      "riskType": "AnonymousIpRiskEvent",
      "userDisplayName": "Jon Doe",
      "userId": "6a56d0b2-3c51-7c5e-bc1a-1ccdb3bd9c71",
      "userPrincipalName": "jon@contoso.com"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List anonymousIpRiskEvents",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
