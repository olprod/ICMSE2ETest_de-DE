# <a name="connectorgroup-resource-type"></a>connectorGroup resource type




## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get connectorGroup](../api/connectorgroup_get.md) | [connectorGroup](connectorgroup.md) |Read properties and relationships of connectorGroup object.|
|[Erstellen einer Dienstanwendung](../api/connectorgroup_post_applications.md) |[Application](application.md)| Associate an application with the connector group by posting to the applications collection.|
|[List applications](../api/connectorgroup_list_applications.md) |[application](application.md) collection| Get the associated application object collection.|
|[Create connector](../api/connectorgroup_post_members.md) |[Connector](connector.md)| Add a connector to the connector Group by posting to the members collection.|
|[List members](../api/connectorgroup_list_members.md) |[connector](connector.md) collection| Get a connector object collection.|
|[Update](../api/connectorgroup_update.md) | [connectorGroup](connectorgroup.md)    |Update connectorGroup object. |
|[delete()](../api/connectorgroup_delete.md) | Keine |Delete connectorGroup object. All connectors must be remove before a conector group can be deleted. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|connectorGroupType|string| The type of connectors that will be used with the group. Possible values are: `applicationProxy`.|
|id|String| The object id of the connectorGroup|
|isDefault|Boolean| Indicates if the connectorGroup is the default connector group. Only a single connector Group can be the default connectorGroup and is set by the system.|
|name|String| Der Name der physischen Datei, die mit dem aktuellen Fehler zusammenhängt|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anwendungen|[application](application.md) collection| Read-only. Nullable.|
|Member|[connector](connector.md) collection| Read-only. Nullable.|

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.connectorGroup"
}-->

```json
{
  "connectorGroupType": "string",
  "id": "String (identifier)",
  "isDefault": true,
  "name": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "connectorGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
