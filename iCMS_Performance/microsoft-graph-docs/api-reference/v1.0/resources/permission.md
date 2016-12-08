# <a name="permission-resource-type"></a>Berechtigung Ressourcentyp

Enthält Informationen über eine Berechtigung für eine [DriveItem](driveitem.md)erteilt.

Eine Reihe von verschiedenen Formularen die Berechtigung haben. Die **Berechtigung** Ressource stellt diese verschiedenen Formularen über Eigenschaften für die **Berechtigung** Ressource dar.

## <a name="methods"></a>Methoden

| Methode                                              | Rückgabetyp                            | Beschreibung                                             |
|:----------------------------------------------------|:---------------------------------------|:--------------------------------------------------------|
| [Listenberechtigungen](../api/item_list_permissions.md) | [Permission](permission.md) -Auflistung | Auflisten der Berechtigungen für ein Element.                        |
| [Berechtigung](../api/permission_get.md)          | [Berechtigung](permission.md)            | Lesen Sie Eigenschaften und Beziehungen der Permission-Objekts. |
| [Fügen Sie hinzu](../api/item_invite.md)                        | [Berechtigung](permission.md)            | Neue Berechtigungen zu einem Element hinzuzufügen.                         |
| [Update](../api/permission_update.md)               | [Berechtigung](permission.md)            | Permission-Objekt zu aktualisieren.                               |
| [Löschen](../api/permission_delete.md)               | Keine                                   | Permission-Objekt zu löschen.                               |


## <a name="properties"></a>Eigenschaften

| Eigenschaft      | Typ                                      | Beschreibung                                                                                                                           |
|:--------------|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| id            | String                                    | Der eindeutige Bezeichner der Berechtigung zwischen alle Berechtigungen für das Element. Schreibgeschützt.                                                 |
| grantedTo     | [identitySet](identityset.md)             | Für Benutzerberechtigungen Typ, die Details der Benutzer und Anwendungen für diese Berechtigung. Schreibgeschützt.                                    |
| Einladung    | [sharingInvitation](sharinginvitation.md) | Details für einen verbundenen freigabeeinladung für diese Berechtigung. Schreibgeschützt.                                                          |
| inheritedFrom | [itemReference](itemreference.md)         | Enthält einen Verweis auf die Vorgänger des aktuellen Berechtigung, wenn es von einem übergeordneten geerbt wird. Schreibgeschützt.                       |
| Link          | [sharingLink](sharinglink.md)             | Enthält den Linkdetails der aktuellen Berechtigung, Berechtigungen ein Link-Typ ist. Schreibgeschützt.                                     |
| Rolle          | Array von Zeichenfolgen                          | Der Typ der Berechtigung, z. B. `read`. Die vollständige Liste der Rollen finden Sie weiter unten. Schreibgeschützt.                                                 |
| shareId       | String                                    | Ein eindeutiges Token für diese Berechtigung. Schreibgeschützt. |


## <a name="roles-enumeration"></a>Rollen-Aufzählung

| Funktion  | Details                                                                        |
|:------|:-------------------------------------------------------------------------------|
| Lesen  | Bietet die Möglichkeit, die Metadaten und den Inhalt des Elements zu lesen.            |
| Schreiben | Die Fähigkeit zum Lesen und Ändern der Metadaten und der Inhalt des Elements enthält. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "link", "grantedTo", "invitation", "inheritedFrom", "shareId" ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.permission"
}-->
```json
{
  "id": "string (identifier)",
  "grantedTo": {"@odata.type": "microsoft.graph.identitySet"},
  "inheritedFrom": {"@odata.type": "microsoft.graph.itemReference"},
  "invitation": {"@odata.type": "microsoft.graph.sharingInvitation"},
  "link": {"@odata.type": "microsoft.graph.sharingLink"},
  "roles": ["string"],
  "shareId": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "permission resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
