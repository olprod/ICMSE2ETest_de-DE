# <a name="privilegedroleassignment-resource-type"></a>privilegedRoleAssignment resource type

Represents a privileged role assignment for a particular user. 


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[List privilegedRoleAssignment collection](../api/privilegedroleassignment_list.md) | [privilegedRoleAssignment](privilegedroleassignment.md) collection|Get the collection of privilegedRoleAssignment objects.|
|[Get privilegedRoleAssignment](../api/privilegedroleassignment_get.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Read properties and relationships of privilegedRoleAssignment object.|
|[Create assignment](../api/privilegedroleassignment_post_privilegedroleassignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)| Create a new assignment by posting to the assignments collection.|
|[delete()](../api/privilegedroleassignment_delete.md) | Keine |Delete privilegedRoleAssignment object. |
|[makePermanent](../api/privilegedroleassignment_makepermanent.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Make the role assignment as permanent.|
|[makeEligible](../api/privilegedroleassignment_makeeligible.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Make the role assignment as eligible.|
|[my](../api/privilegedroleassignment_my.md)|[privilegedRoleAssignment](privilegedroleassignment.md) collection|Get the current user's privileged role assignments.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|expirationDateTime|dateTimeOffset|The UTC DateTime when the temporary privileged role assignment will be expired. For permanent role assignment, the value is null.|
|id|string| The unique identifier for the privileged role assignment. Read-only. It is in the format of 'userId_roleId', where userId is the GUID string for Azure AD user id, and roleId is the GUID string for Azure administrator role id.|
|isElevated|boolean|**true** if the role assignment is activated. **false** if the role assignment is deactivated.|
|resultMessage|string|Result message set by the service.|
|roleId|string|Role identifier. In GUID string format.|
|userID|string|User identifier. In GUID string format.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|roleInfo|[privilegedRole](privilegedrole.md)| Read-only. Nullable. The associated role information.|

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleAssignment"
}-->

```json
{
  "expirationDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "isElevated": true,
  "resultMessage": "string",
  "roleId": "string",
  "userId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleAssignment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->