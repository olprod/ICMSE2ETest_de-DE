# <a name="directoryrole-resource-type"></a>Ressourcentyp directoryRole

Stellt eine Azure AD-Directory-Rolle. Azure Active Directory Directory Rollen sind auch bekannt als *Administratorrollen*. Weitere Informationen zu Rollen Verzeichnis (Administrator) finden Sie unter [Zuweisen von Administratorrollen in Azure Active Directory](http://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/). Mit der Microsoft Graph können Sie Directory Rollen erteilen sie die Berechtigungen der Zielrolle Benutzer zuweisen. Um eine Rolle Directory lesen oder deren Member aktualisieren möchten, müssen sie zuerst im Mandanten aktiviert werden. Nur die Administratoren im Unternehmen Directory Rolle ist standardmäßig aktiviert. Um andere verfügbare Verzeichnis Rollen aktivieren möchten, senden Sie eine POST-Anforderung mit der ID der [DirectoryRoleTemplate](directoryroletemplate.md) , auf dem die Rolle Directory basiert. Erbt vom [DirectoryObject](directoryobject.md).

Standardmäßig werden Directory Rollen Recherchediensts Mandanten geltende werden.  Verzeichnis Rollen (derzeit nur das *Konto ein Benutzeradministrator* und *Helpdesk Admin*) können jedoch auch [administrative Einheiten](administrativeunit.md)zugewiesen werden.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von directoryRole](../api/directoryrole_get.md) | [directoryRole](directoryrole.md) |Lesen Sie Eigenschaften und Beziehungen DirectoryRole-Objekts.|
|[Mitglied hinzufügen](../api/directoryrole_post_members.md) |[directoryObject](directoryobject.md)| Hinzufügen eines Benutzers zur Rolle Directory durch die Veröffentlichung auf die Navigationseigenschaft Mitglieder.|
|[Mitglieder der Liste](../api/directoryrole_list_members.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Benutzer, die Mitglieder der Rolle Verzeichnis aus der Navigationseigenschaft Mitglieder sind.|
|[Bereichsbasierte Listenadministratoren](../api/directoryrole_list_scopedadministrators.md) |[ScopedRoleMembership](scopedrolemembership.md) -Auflistung| Die Member dieser Directory Rolle, die [administrative Einheiten](administrativeunit.md), über objektauflistung ScopedRoleMembership Bereich haben aufgelistet.|
<!--|[Entfernen von Mitgliedern](../api/directoryrole_delete_members.md) |[directoryObject](directoryobject.md)| Entfernen eines Benutzers aus der Rolle Directory durch das Veröffentlichen der Mitglieder Navigation-Eigenschaft.|-->

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|description|String|Die Beschreibung für die Rolle Verzeichnis. Schreibgeschützt. |
|displayName|String|Der Anzeigename für die Rolle Verzeichnis. Schreibgeschützt. |
|id|String|Der eindeutige Bezeichner für die Rolle Verzeichnis. Geerbt von [DirectoryObject](directoryobject.md). Wichtige, nicht NULL-Werte zulässt, schreibgeschützt.|
|roleTemplateId|String| Die **Id** des der [DirectoryRoleTemplate](directoryroletemplate.md) , die diese Rolle basiert. Die Eigenschaft muss beim Aktivieren von einer Directory Rolle in einem Mandanten mit einer POST-Operation angegeben werden. Nachdem die Rolle Verzeichnis aktiviert ist, ist die Eigenschaft schreibgeschützt. |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Member|[DirectoryObject](directoryobject.md) -Auflistung|Benutzer, die Mitglieder dieser Rolle Directory sind. HTTP-Methoden: GET, POST, LÖSCHEN. Schreibgeschützt. NULL-Werte zulässt.|
|scopedAdministrators|[ScopedRoleMembership](scopedrolemembership.md) -Auflistung| Administratoren dieser Rolle Directory [administrative Einheiten](administrativeunit.md)zugeordnet sind. Schreibgeschützt. NULL-Werte zulässt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "memberOf",
    "members",
    "ownedObjects",
    "owners"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryRole"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "roleTemplateId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
