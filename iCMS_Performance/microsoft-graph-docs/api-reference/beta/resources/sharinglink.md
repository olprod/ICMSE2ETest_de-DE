# <a name="sharinglink-resource-type"></a>sharingLink resource type

Provides information on a sharing link for an item.


## <a name="properties"></a>Eigenschaften

| Eigenschaft    | Typ                    | Beschreibung                                                                                                                                                                                             |
|:------------|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| application | [Identität](identity.md) | The app the link is associated with.                                                                                                                                                                    |
| Typ        | String                  | The type of the link created.                                                                                                                                                                           |
| Bereich       | String                  | The scope of the link represented by this permission. Value `anonymous` indicates the link is usable by anyone, `organization` indicates the link is only usable for users signed into the same tenant. |
| WebUrl      | String                  | A URL that opens the item in the browser on the OneDrive website.                                                                                                                                       |


## <a name="type-enumeration"></a>Type enumeration

This table defines the possible values for the **type** property:

| Wert   | Funktion    | Beschreibung                                                                     |
|:--------|:--------|:--------------------------------------------------------------------------------|
| `view`  | `read`  | A view-only sharing link, allowing read-only access.                            |
| `edit`  | `write` | An edit sharing link, allowing read-write access.                               |

## <a name="scope-enumeration"></a>Scope enumeration

| Wert          | Beschreibung                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `anonymous`    | The sharing link is available for anyone to use.                                                                            |
| `organization` | The sharing link is available for anyone within the same organization (tenant) to use. Not available for OneDrive Personal. |


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "application", "scope" ],
  "@odata.type": "microsoft.graph.sharingLink"
}-->

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "type": "view | edit",
  "scope": "anonymous | organization",
  "webUrl": "url"
}
```



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharingLink resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
