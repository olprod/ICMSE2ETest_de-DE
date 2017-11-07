# <a name="privilegedroleassignment-resource-type"></a>Ressourcentyp privilegedRoleAssignment

Stellt eine privilegierten rollenzuweisung für einen bestimmten Benutzer. 


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Liste PrivilegedRoleAssignment-Auflistung](../api/privilegedroleassignment_list.md) | [PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung|Rufen Sie die Auflistung der PrivilegedRoleAssignment-Objekte.|
|[Abrufen von privilegedRoleAssignment](../api/privilegedroleassignment_get.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Lesen Sie Eigenschaften und Beziehungen des PrivilegedRoleAssignment-Objekts.|
|[Zuordnung erstellen](../api/privilegedroleassignment_post_privilegedroleassignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)| Erstellen Sie eine neue Zuordnung, indem Sie das Veröffentlichen in der Assignments-Auflistung.|
|[Löschen](../api/privilegedroleassignment_delete.md) | Keine |Löschen Sie PrivilegedRoleAssignment Objekt. |
|[makePermanent](../api/privilegedroleassignment_makepermanent.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Stellen Sie die rollenzuweisung als dauerhaft entfernt.|
|[makeEligible](../api/privilegedroleassignment_makeeligible.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|Stellen Sie die rollenzuweisung als geeignet.|
|[Meine](../api/privilegedroleassignment_my.md)|[PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung|Abrufen des aktuellen Benutzers privilegierten rollenzuweisungen.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|expirationDateTime|dateTimeOffset|Die UTC-DateTime, die temporäre privilegierten rollenzuweisung abgelaufen sein wird. Für permanente rollenzuweisung ist der Wert null.|
|id|string| Der eindeutige Bezeichner für die privilegierten rollenzuweisung. Schreibgeschützt. Es ist im Format "UserId_roleId", wobei Benutzer-ID ist die GUID-Zeichenfolge für Azure AD-Benutzer-Id und RoleId ist die GUID für Azure Administrator Role-Id-Zeichenfolge.|
|isElevated|boolean|**true,** Wenn die rollenzuweisung aktiviert ist. **false,** Wenn die rollenzuweisung deaktiviert wird.|
|resultMessage|string|Ergebnisnachricht vom Dienst festgelegt.|
|roleId|string|Rollenbezeichner. Im Zeichenformat GUID.|
|Benutzer-ID|string|Benutzer-ID. Im Zeichenformat GUID.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|roleInfo|[privilegedRole](privilegedrole.md)| Schreibgeschützt. NULL-Werte zulässt. Die zugehörige Rolle-Informationen.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

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