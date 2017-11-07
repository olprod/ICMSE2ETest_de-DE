# <a name="list-policies-assigned-to-application-or-service-principal"></a>Zugewiesene Anwendung oder Dienstprinzipal Listenrichtlinien

Abrufen der [Richtlinie](../resources/policy.md) -Objekte, die eine Anwendung oder ein Service principal zugewiesen.

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /applications/<id>/policies
```

> Hinweis: "Id" in der Anforderung ist die Eigenschaft "Id" der Anwendung oder Dienstprinzipal, nicht die Eigenschaft "Appid".

### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortobjekte Code und [Richtlinie](../resources/policy.md) im Antworttext. Wenn Sie nicht erfolgreich ist, ein `4xx` mit bestimmten Details entsprechende Fehlermeldung zurückgegeben.

### <a name="example"></a>Beispiel
Im folgende Beispiel werden die Richtlinien zugewiesen an eine Anwendung abgerufen.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
GET https://graph.microsoft.com/beta/applications/<id>/policies
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 200 OK
Cache-Control: private
Content-Type: application/json

{
    "value":[
        {
            "@odata.type":"#microsoft.graph.policy",
            "id":"id-value",
            "alternativeIdentifier":null,
            "definition":["policy-definition"],
            "displayName":"name-value",
            "isOrganizationDefault":boolean-value,
            "keyCredentials":[key-credentials],
            "type":"type-value"
        }
    ]
}
```
