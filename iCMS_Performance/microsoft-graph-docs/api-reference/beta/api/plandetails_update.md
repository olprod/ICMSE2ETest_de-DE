# <a name="update-plandetails"></a>Update plandetails

Update the properties of plandetails object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:
 
Wählen Sie Group.ReadWrite.All.

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /plans/<id>/details

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Value should be set to "Bearer (access-token)" |
| If-Match | string | Value should be set to the ETag of the object |
| Prefer | string | Value should be set to "return=representation" so that the updated object is returned in the response. This is advised so that the client can get the new ETag value of the updated object without doing an additional GET |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|category0Description|String|Description of the category (or label) that can be applied to the task.|
|category1Description|String|Description of the category (or label) that can be applied to the task.|
|category2Description|String|Description of the category (or label) that can be applied to the task.|
|category3Description|String|Description of the category (or label) that can be applied to the task.|
|category4Description|String|Description of the category (or label) that can be applied to the task.|
|category5Description|String|Description of the category (or label) that can be applied to the task.|
|sharedWith|[userIdCollection](../resources/useridcollection.md)| List of user ids that this plan is shared with. If you are leveraging Office 365 Groups, use the Groups API to manage group membership to share the group's plan. You can also add existing members of the group to this collection though it is not required for them to access the plan owned by the group.|

## <a name="response"></a>Antwort
If successful, this method returns a `204 No Content` response code.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "update_plandetails"
}-->
```http
PATCH https://graph.microsoft.com/beta/plans/<id>/details
Content-type: application/json
Content-length: 381
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "sharedWith": {
  },
  "category0Description": "category0Description-value",
  "category1Description": "category1Description-value",
  "category2Description": "category2Description-value",
  "category3Description": "category3Description-value",
  "category4Description": "category4Description-value",
  "category5Description": "category5Description-value"
}
```
##### <a name="response"></a>Antwort
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plandetails"
} -->
```http
HTTP/1.1 204 No Content
```
To get the updated object, use the `Prefer` header. See Request Headers above.
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update plandetails",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->