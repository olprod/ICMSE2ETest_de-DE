# <a name="list-policies"></a>List Policies

Retrieve all [policy](../resources/policy.md) objects in the directory.

### <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Directory.AccessAsUser.All*

### <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /policies
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |

### <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

### <a name="response"></a>Antwort
If successful, this method returns `200, OK` response code and [policy](../resources/policy.md) objects in the response body. If unsuccessful...

### <a name="example"></a>Beispiel
The following example retrieves all policies.

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

```http
GET https://graph.microsoft.com/beta/policies
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

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
