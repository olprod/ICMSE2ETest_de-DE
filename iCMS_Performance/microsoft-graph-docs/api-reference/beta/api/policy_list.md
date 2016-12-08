# <a name="list-policies"></a>Listenrichtlinien

Rufen Sie [aller Gruppenrichtlinienobjekte in das Verzeichnis ab](../resources/policy.md) .

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /policies
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortobjekte Code und [Richtlinie](../resources/policy.md) im Antworttext. Wenn Sie nicht erfolgreich...

### <a name="example"></a>Beispiel
Im folgende Beispiel werden alle Richtlinien abgerufen.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
GET https://graph.microsoft.com/beta/policies
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "value":[
        {
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
