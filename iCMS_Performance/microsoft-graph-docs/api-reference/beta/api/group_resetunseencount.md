# <a name="group-resetunseencount"></a>group: resetUnseenCount

Reset the unseenCount of all the posts that the current user has not seen since their last visit. Supported for only Office 365 groups.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Group.ReadWrite.All* 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/resetUnseenCount
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Required.  |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="response"></a>Antwort
If successful, this method returns `200, OK` response code. It does not return anything in the response body.

## <a name="example"></a>Beispiel
Here is an example of how to call this API.
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "group_resetunseencount"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/resetUnseenCount
```

##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils. 
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: resetUnseenCount",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
