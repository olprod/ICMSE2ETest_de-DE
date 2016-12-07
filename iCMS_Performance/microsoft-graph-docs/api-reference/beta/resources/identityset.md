# <a name="identityset-resource-type"></a>identitySet resource type

The **identitySet** type is a keyed collection of [identity](identity.md) objects. It is used to represent a set of identities associated with various events for an item, such as _created by_ or _last modified by_.

## <a name="properties"></a>Eigenschaften

| Eigenschaft    | Typ                    | Beschreibung                                           |
|:------------|:------------------------|:------------------------------------------------------|
| application | [Identität](identity.md) | An identity resource that represents the application. |
| Gerät      | [Identität](identity.md) | An identity resource that represents the device.      |
| user        | [Identität](identity.md) | An identity resource that represents a user.          |

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "user", "device", "application" ],
  "@odata.type": "microsoft.graph.identitySet"
}-->

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "device": {"@odata.type": "microsoft.graph.identity"},
  "user": {"@odata.type": "microsoft.graph.identity"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "identitySet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
