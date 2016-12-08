# <a name="azure-ad-privileged-identity-management"></a>Identitätsmanagement Azure AD-Berechtigungen

Hier wird die Liste der Methoden, die vom [Privilegierten Identity Management](https://azure.microsoft.com/en-us/documentation/articles/active-directory-privileged-identity-management-configure/) -Dienst bereitgestellt werden.

Der Dienst wird auf der Basis OData erstellt. Verwenden Sie zum Filtern der Ergebnisse der Abfrage, die standard-OData ``$filter`` Ausdrücke in die URIs.

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Liste privilegedOperationEvent](../api/privilegedoperationevent_list.md) | [PrivilegedOperationEvent](privilegedoperationevent.md) -Auflistung |Rufen Sie PrivilegedOperationEvent-Auflistung-Objekts. |
|[Abrufen von privilegedRole](../api/privilegedrole_get.md) |[privilegedRole](privilegedrole.md)| Rufen Sie ein PrivilegedRole-Objekt.|
|[Liste privilegedRole](../api/privilegedrole_list.md) | [PrivilegedRole](privilegedrole.md) -Auflistung |Rufen Sie PrivilegedRole-Auflistung-Objekts. |
|[Liste von rollenzuweisungen](../api/privilegedrole_list_assignments.md) | [PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung |PrivilegedRoleAssignment-Auflistung für die bestimmten Rolle abrufen. Jeder PrivilegedRoleAssignment stellt eine rollenzuweisung an einen Benutzer.|
|[selfActivate](../api/privilegedrole_selfactivate.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Aktivieren Sie die Rolle, die an den Requestor zugewiesen ist.|
|[selfDeactivate](../api/privilegedrole_selfdeactivate.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Deaktivieren Sie die Rolle, die an den Requestor zugewiesen ist.|
|[Erstellen von privilegedRoleAssignment](../api/privilegedroleassignment_post_privilegedroleassignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)| Erstellen Sie eine neue PrivilegedRoleAssignment (rollenzuweisung), indem Sie das Veröffentlichen in der PrivilegedRoleAssignments-Auflistung.|
|[Liste privilegedRoleAssignment](../api/privilegedroleassignment_list.md) | [PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung |Rufen Sie PrivilegedRoleAssignment-Auflistung-Objekts. Die Auflistung enthält alle rollenzuweisungen für die Organisation. Jeder PrivilegedRoleAssignment stellt eine rollenzuweisung an einen Benutzer. |
|[Abrufen von privilegedRoleAssignment](../api/privilegedroleassignment_get.md) | [privilegedRoleAssignment](privilegedroleassignment.md)|Rufen Sie PrivilegedRoleAssignment Objekt mit der Id angegebenen Zuweisung. |
|[PrivilegedRoleAssignment löschen](../api/privilegedroleassignment_delete.md) | Keine. |Löschen Sie PrivilegedRoleAssignment Objekt. |
|[makePermanent](../api/privilegedroleassignment_makepermanent.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Stellen Sie die rollenzuweisung als dauerhaft entfernt. |
|[makeEligible](../api/privilegedroleassignment_makeeligible.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |Stellen Sie die rollenzuweisung als geeignet. |
|[Meine](../api/privilegedroleassignment_my.md) | [PrivilegedRoleAssignment](privilegedroleassignment.md) -Auflistung|Rufen Sie das jeweilige Rolle Zuordnungen. |
|[Abrufen von privilegedRoleSettings](../api/privilegedrolesettings_get.md) | [privilegedRoleSettings](../resources/privilegedrolesettings.md)|Rufen Sie die Eigenschaften des PrivilegedRoleSettings-Objekts ab. |
|[Abrufen von privilegedRoleSummary](../api/privilegedrolesummary_get.md) | [privilegedRoleSummary](../resources/privilegedrolesummary.md)|Rufen Sie das Objekt PrivilegedRoleSummary. |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Service root",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
