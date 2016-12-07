# <a name="privilegedrolesummary-resource-type"></a>privilegedRoleSummary resource type

The statistics summary for a particular role.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get privilegedRoleSummary](../api/privilegedrolesummary_get.md) | [privilegedRoleSummary](privilegedrolesummary.md) |Read properties and relationships of privilegedRoleSummary object.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|elevatedCount|Int32|The number of users that have the role assigned and the role is activated.|
|id|string| The unique identifier for the role. Read-only.|
|managedCount|Int32|The number of users that have the role assigned but the role is deactivated.|
|mfaEnabled|boolean|**true** if the role activation requires MFA. **false** if the role activation doesn't require MFA.|
|status|string| Possible values are: `ok`, `bad`. The value depends on the ratio of (managedCount / usersCount). If the ratio is less than a predefined threshold, `ok` is returned. Otherwise, `bad` is returned.|
|usersCount|Int32|The number of users that are assigned with the role.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleSummary"
}-->

```json
{
  "elevatedCount": 1024,
  "id": "string (identifier)",
  "managedCount": 1024,
  "mfaEnabled": true,
  "status": "string",
  "usersCount": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleSummary resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->