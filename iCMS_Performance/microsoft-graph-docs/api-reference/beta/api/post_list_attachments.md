# <a name="list-attachments"></a>Anlagen auflisten

Abrufen einer Liste der [Attachment](../resources/attachment.md) -Objekte, die auf einen Beitrag zugeordnet ist.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

* Group.Read.All
* Group.Readwrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
Anlagen für einen [Posten](../resources/post.md) in einem [Thread](../resources/conversationthread.md) , gehören zu einer [Unterhaltung](../resources/conversation.md) einer Gruppe.
```http
GET /groups/<id>/threads/<id>/posts/<id>/attachments
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/attachments
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

Sie können insbesondere die $ Abfragezeichenfolgen-Parameter, um alle der Post Anlagen Inline mit dem Rest der Post-Eigenschaften zu erweitern. Beispiel:

```
GET https://graph.microsoft.com/beta/groups/<id>/threads/<id>/posts/<id>?$expand=attachments
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von [Attachment](../resources/attachment.md) -Objekte in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_attachments"
}-->
```http
GET https://graph.microsoft.com/beta/groups/<id>/threads/<id>/posts/<id>/attachments
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
      "id": "id-value",
      "contentType": "contentType-value",
      "contentLocation": "contentLocation-value",
      "contentBytes": "contentBytes-value",
      "contentId": "null",
      "lastModifiedDateTime": "datetime-value",
      "isInline": false,
      "name": "name-value",
      "size": 99
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List attachments",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
