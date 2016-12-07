# <a name="list-available-drives"></a>List available drives

Retrieve a list of available drive objects for a user or Office 365 group.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drives
GET /groups/<id>/drives
```
## <a name="optional-query-parameters"></a>Optionale OData-Abfrageparameter
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Required. |


## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and collection of [drive](../resources/drive.md) objects in the response body.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung
Here is an example of the request for the user's drives.

<!-- {
  "blockType": "request",
  "name": "get_drives"
}-->
```http
GET https://graph.microsoft.com/beta/me/drives
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.drive",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 579

{
  "value": [
    {
      "id": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "driveType": "business",    
      "owner": {
          "user": {
              "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
              "displayName": "Ryan Gregg"
          }
      },
      "quota": {
          "deleted": 256938,
          "remaining": 1099447353539,
          "state": "normal",
          "total": 1099511627776
      }
    }
  ]
}
```

## <a name="remarks"></a>Hinweise

Most users will only have a single OneDrive. Office 365 groups may have more than one drive available.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List drives",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/List Drives"
}-->
