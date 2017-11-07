# <a name="privilegedrole-resource-type"></a>Ressourcentyp privilegedRole

Stellt eine Azure AD-Administratorrolle z. B.: **globaler Administrator, Abrechnungsadministrator, Dienstadministrator, Benutzer-Administrator, Kennwort-Administrator**usw..


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Objekte in der Liste privilegedRole](../api/privilegedrole_list.md) | [PrivilegedRole](privilegedrole.md) -Auflistung|Ruft die Auflistung der PrivilegedRole.|
|[Abrufen von privilegedRole](../api/privilegedrole_get.md) | [privilegedRole](privilegedrole.md) |Lesen Sie Eigenschaften und Beziehungen PrivilegedRole-Objekts.|
|[Liste Zuordnungen](../api/privilegedrole_list_assignments.md) |[PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung| Rufen Sie die Auflistung ein Assignment-Objekts für diese Rolle.|
|[selfActivate](../api/privilegedrole_selfactivate.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Aktivieren Sie die zugeordnete Rolle.|
|[selfDeactivate](../api/privilegedrole_selfdeactivate.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Deaktivieren Sie die zugeordnete Rolle.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|Der eindeutige Bezeichner für Administratorrolle. Es ist eine GUID-Zeichenfolge und verfügt über denselben Wert wie der Rolle Vorlagen-Id aus dem Azure Active Directory für die gegebene Rolle. Schreibgeschützt.|
|name|string|Rollenname.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Zuordnungen|[PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung| Die Zuordnungen für diese Rolle. Schreibgeschützt. NULL-Werte zulässt.|
|settings|[privilegedRoleSettings](privilegedrolesettings.md)| Die Einstellungen für diese Rolle. Schreibgeschützt. NULL-Werte zulässt.|
|Zusammenfassung|[privilegedRoleSummary](privilegedrolesummary.md)| Der zusammenfassende Informationen für diese Rolle. Schreibgeschützt. NULL-Werte zulässt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRole"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->