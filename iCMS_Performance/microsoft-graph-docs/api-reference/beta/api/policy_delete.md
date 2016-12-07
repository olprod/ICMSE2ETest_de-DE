# <a name="delete-policy"></a>Delete Policy

Delete a [policy](../resources/policy.md).

### <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Directory.AccessAsUser.All*

### <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

```http
DELETE /policies/<id>
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |

### <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

### <a name="response"></a>Antwort
If successful, this method returns `204, No Content` response code. If unsuccessful...

### <a name="example"></a>Beispiel
The following example deletes a policy.

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

```http
DELETE https://graph.microsoft.com/beta/policies/<id>
```

##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 204 No Content
```
