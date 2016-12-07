# <a name="remove-a-member"></a>Remove a member

Use this API to remove a member (user or group) from an administrative unit.

## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: *Directory.AccessAsUser.All*

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /administrativeUnits/<id>/members/<id>/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Required.|

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns `204, No Content` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Here is an example of the request. In the example below, id1 represents the identifier for the target administrative unit, and id2 represents the unique identifier for the member user or group to be removed from the targetted administrative unit. 

```http
DELETE https://graph.microsoft.com/beta/administrativeUnits/<id1>/members/<id2>/$ref
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
 
```http
HTTP/1.1 204 No Content
```
