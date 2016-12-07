# <a name="get-a-member"></a>Get a member

Use this API to get a specific member (user or group) in an administrative unit.

## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: *Directory.Read.All* or *Directory.ReadWrite.All* or *Directory.AccessAsUser.All*.

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

```http
GET /administrativeUnits/<id>/members/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Required.|

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and a [user](../resources/user.md) or [group](../resources/group.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.

```http
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members/<id>
```

##### <a name="response"></a>Antwort
Here is an example of the respone. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "@odata.type":"#microsoft.graph.user",
  "id":"492c5308-59fd-4740-9c83-4b3db07a6d70"
  "accountEnabled":true,
  "businessPhones":[],
  "companyName":null,
  "displayName":"Demo User"
}
```