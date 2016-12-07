# <a name="worksheetprotection-unprotect"></a>WorksheetProtection: unprotect

Unprotect a worksheet
## <a name="prerequisites"></a>Voraussetzungen
The following **scopes** are required to execute this API: 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/worksheets(<id|name>)/protection/unprotect

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer <code>|


## <a name="request-body"></a>Anforderungstextkörper
In the request body, provide a JSON object with the following parameters.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|password|string|Optional. sheet protection password.|

## <a name="response"></a>Antwort
If successful, this method returns `200, OK` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "worksheetprotection_unprotect"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/protection/unprotect
Content-type: application/json
Content-length: 34

{
  "password": "password-value"
}
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils. 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.none"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "WorksheetProtection: unprotect",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->