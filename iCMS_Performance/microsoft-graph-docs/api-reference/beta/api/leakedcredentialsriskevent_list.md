# <a name="list-leakedcredentialsriskevents"></a>Liste leakedCredentialsRiskEvents

Abrufen einer Liste von Leakedcredentialsriskevent-Objekten.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *IdentityRiskEvent.Read.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /leakedCredentialsRiskEvents
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|
| Arbeitsmappe-Sitzung-Id  | Arbeitsmappe Sitzung-Id, die bestimmt, ob Änderungen oder nicht beibehalten werden. Optional|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [LeakedCredentialsRiskEvent](../resources/leakedcredentialsriskevent.md) .
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_leakedcredentialsriskevents"
}-->
```http
GET https://graph.microsoft.com/v1.0/leakedCredentialsRiskEvents
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.leakedCredentialsRiskEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 304

{
  "value":
  [
    {
      "closedDateTime": null,
      "createdDateTime": "2016-01-29T00:01:49.126468Z",
      "id": "8c793a18-c86a-b5f9-7d9a-b3d024f33eee-278dc452-4163-dbc6-84eb-a050c37fc931-1a01abd3-b87a-cece-3f4d-c788b055c182",
      "riskEventDateTime": "2016-01-29T00:00:56.2255665Z",
      "riskEventStatus": "active",
      "riskLevel": "high",
      "riskType": "LeakedCredentialsRiskEvent",
      "userDisplayName": "Jon Doe",
      "userId": "278dc452-4163-dbc6-84eb-a050c37fc931",
      "userPrincipalName": "jon@contoso.com"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List leakedCredentialsRiskEvents",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
