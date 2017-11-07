# <a name="list-applications-and-service-principals-with-specific-policy-assigned"></a>Liste Anwendungen und Dienstprinzipale mit bestimmten Richtlinie zugewiesen.

Rufen Sie die Objekte [Application](../resources/application.md) und [Dienstprinzipal](../resources/serviceprincipal.md) , mit der angegebenen Richtlinie zugewiesen.

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung
```http
GET /policies/<id>/appliesTo
```

### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwort von Code und [Anwendung](../resources/application.md) und [Service principal](../resources/serviceprincipal.md) -Objekte in der Antworttext. Wenn Sie nicht erfolgreich ist, ein `4xx` mit bestimmten Details entsprechende Fehlermeldung zurückgegeben.

### <a name="example"></a>Beispiel
Im folgende Beispiel werden die dienstanwendungen und Dienstprinzipale mit einer bestimmten Richtlinie zugewiesen abgerufen.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
GET https://graph.microsoft.com/beta/policies/<id>/appliesTo
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value":[
        {
            "@odata.type"="#microsoft.graph.application",
            "appId":"appId-value",
            "displayName":"displayName-value",
            "errorUrl":"errorUrl-value",
            "groupMembershipClaims":"groupMembershipClaims-value",
            "homepage":"homepage-value",
            "id":"id-value",
            "keyCredentials":[key-credentials],
            "logoutUrl":"logoutUrl-value",
            "replyUrls":["replyUrls-value"]
        }
    ]
}
```
