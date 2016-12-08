# <a name="serviceprincipal-resource-type"></a>Ressourcentyp servicePrincipal

Stellt eine Instanz einer Anwendung in einem Verzeichnis. Erbt vom [DirectoryObject](directoryobject.md).


### <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "appRoleAssignedTo",
    "appRoleAssignments",
    "createdObjects",
    "createdOnBehalfOf",
    "memberOf",
    "oauth2PermissionGrants",
    "ownedObjects",
    "owners"
  ],
  "@odata.type": "microsoft.graph.serviceprincipal"
}-->

```json
{
  "accountEnabled": true,
  "addIns": [{"@odata.type": "microsoft.graph.addIn"}],
  "appDisplayName": "string",
  "appId": "string",
  "appOwnerOrganizationId": "guid",
  "appRoleAssignmentRequired": true,
  "appRoles": [{"@odata.type": "microsoft.graph.appRole"}],
  "displayName": "string",
  "errorUrl": "string",
  "homepage": "string",
  "id": "string (identifier)",
  "keyCredentials": [{"@odata.type": "microsoft.graph.keyCredential"}],
  "logoutUrl": "string",
  "oauth2Permissions": [{"@odata.type": "microsoft.graph.oAuth2Permission"}],
  "passwordCredentials": [{"@odata.type": "microsoft.graph.passwordCredential"}],
  "preferredTokenSigningKeyThumbprint": "string",
  "publisherName": "string",
  "replyUrls": ["string"],
  "samlMetadataUrl": "string",
  "servicePrincipalNames": ["string"],
  "tags": ["string"]
}

```
### <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ |Beschreibung|
|:---------------|:--------|:----------|
|accountEnabled|Boolean| **true** Wenn das Dienstkonto für den Prinzipal aktiviert ist. anderenfalls **false**.            |
|appDisplayName|String|Der Anzeigename, der von der zugeordneten Anwendung verfügbar gemacht werden.|
|appId|String|Der eindeutige Bezeichner für die zugewiesene Anwendung (die Eigenschaft **AppId** ).|
|appRoleAssignmentRequired|Boolean|Gibt an, ob eine **AppRoleAssignment** für einen Benutzer oder Gruppe erforderlich ist, bevor Azure AD einen Benutzer oder eine Zugriffstoken für die Anwendung ausstellt. Nicht auf NULL festgelegt. |
|appRoles|[AppRole](approle.md) -Auflistung|Die Rollen der Anwendung von der zugeordneten Anwendung verfügbar gemacht werden. Weitere Informationen finden Sie in der [Anwendung](application.md) Entität die Eigenschaftendefinition **AppRoles** . Nicht auf NULL festgelegt. |
|displayName|String|Der Anzeigename für den Dienstprinzipal.|
|errorUrl|String|            |
|Homepage|String|Die URL zur Homepage der zugehörigen Anwendung.|
|keyCredentials|[KeyCredential](keycredential.md) -Auflistung|Die Auflistung von wichtigen Anmeldeinformationen, die dem Prinzipal Dienst zugeordnet sind. Nicht auf NULL festgelegt.            |
|logoutUrl|String|            |
|oauth2Permissions|[oAuth2Permission](oauth2permission.md) -Auflistung|Die OAuth 2.0-Berechtigungen von der zugeordneten Anwendung verfügbar gemacht werden. Weitere Informationen finden Sie in der Definition der **oauth2Permissions** -Eigenschaft in der [Anwendung](application.md) Entität. Nicht auf NULL festgelegt.            |
|id|String|Der eindeutige Bezeichner für den Dienstprinzipal. Geerbt von [DirectoryObject](directoryobject.md). -Taste. Nicht auf NULL festgelegt. Schreibgeschützt.|
|passwordCredentials|[PasswordCredential](passwordcredential.md) -Auflistung|Die Auflistung von Anmeldeinformationen den Dienstprinzipal zugeordnet. Nicht auf NULL festgelegt. |
|preferredTokenSigningKeyThumbprint|String|Für die interne Verwendung reserviert. Schreiben oder verlassen sich andernfalls auf diese Eigenschaft nicht. Kann in zukünftigen Versionen entfernt werden. |
|publisherName|String|Der Anzeigename des Mandanten in dem verbundenen Anwendung angegeben wird.|
|replyUrls|Zeichenfolgenauflistung|Die URLs, dass Benutzertoken, um für die Anmeldung mit der zugeordneten Anwendung oder die Umleitung URIs, dass OAuth 2.0 Autorisierungscodes gesendet werden und Zugriffstoken werden für die zugewiesene Anwendung an. Nicht auf NULL festgelegt. |
|samlMetadataUrl|String| |
|servicePrincipalNames|Zeichenfolgenauflistung|Die URIs, mit denen die zugewiesene Anwendung identifiziert. Weitere Informationen finden Sie unter [Application Objects und Service Principal-Objekte](https://msdn.microsoft.com/en-us/library/azure/dn132633.aspx). **Any** -Operator ist erforderlich für Filterausdrücke auf mehrwertige Eigenschaften.  Nicht auf NULL festgelegt. |
|Tags|Zeichenfolgenauflistung| Nicht auf NULL festgelegt. |

### <a name="relationships"></a>Beziehungen
| Beziehung | Typ |Beschreibung|
|:---------------|:--------|:----------|
|appRoleAssignedTo|[appRoleAssignment](approleassignment.md)|Prinzipale (Benutzer, Gruppen und Dienstprinzipale), die diese Dienstprinzipal zugewiesen sind. Schreibgeschützt.|
|appRoleAssignments|[AppRoleAssignment](approleassignment.md) -Auflistung|Anwendungen, denen der Dienstprinzipal zugewiesen ist. Schreibgeschützt. NULL-Werte zulässt.|
|createdObjects|[DirectoryObject](directoryobject.md) -Auflistung|Verzeichnis Objekte, die von diesem Dienstprinzipal erstellt. Schreibgeschützt. NULL-Werte zulässt.|
|Mitglied|[DirectoryObject](directoryobject.md) -Auflistung|Rollen, denen diese Dienstprinzipal ein Mitglied ist. HTTP-Methoden: GET schreibgeschützt. NULL-Werte zulässt.|
|oauth2PermissionGrants|[oAuth2PermissionGrant](oauth2permissiongrant.md) -Auflistung|Benutzer Identitätswechsel gewährt dieser Dienstprinzipal zugeordnet sind. Schreibgeschützt. NULL-Werte zulässt.|
|ownedObjects|[DirectoryObject](directoryobject.md) -Auflistung|Directory-Objekte, die diese Dienstprinzipal gehören. Schreibgeschützt. NULL-Werte zulässt.|
|Besitzer|[DirectoryObject](directoryobject.md) -Auflistung|Directory-Objekte, die Besitzer des Prinzipals Service sind. Die Besitzer sind eine Reihe von nicht-Administratoren, die berechtigt sind, um dieses Objekt zu ändern. Schreibgeschützt. NULL-Werte zulässt.|
|Richtlinie|Auflistung von [Gruppenrichtlinien](policy.md)|Die Richtlinien, diese Dienstprinzipal zugewiesen sind.|

### <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von servicePrincipal](../api/serviceprincipal_get.md) | [servicePrincipal](serviceprincipal.md) |Lesen Sie Eigenschaften und Beziehungen ServicePrincipal-Objekts.|
|[Erstellen von appRoleAssignment](../api/serviceprincipal_post_approleassignments.md) |[appRoleAssignment](approleassignment.md)| Erstellen Sie eine neue AppRoleAssignment durch die Veröffentlichung auf der AppRoleAssignments-Auflistung.|
|[Liste appRoleAssignments](../api/serviceprincipal_list_approleassignments.md) |[AppRoleAssignment](approleassignment.md) -Auflistung| Rufen Sie eine Auflistung der AppRoleAssignment-Objekts.|
|[Erstellen von createdObject](../api/serviceprincipal_post_createdobjects.md) |[directoryObject](directoryobject.md)| Erstellen Sie eine neue CreatedObject durch die Veröffentlichung auf der CreatedObjects-Auflistung.|
|[Liste createdObjects](../api/serviceprincipal_list_createdobjects.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie eine Auflistung der CreatedObject-Objekts.|
|[Erstellen von Mitglied](../api/serviceprincipal_post_memberof.md) |[directoryObject](directoryobject.md)| Erstellen Sie ein neues Mitglied, indem Sie das Veröffentlichen in der Auflistung Mitglied.|
|[Liste Mitglied](../api/serviceprincipal_list_memberof.md) |[DirectoryObject](directoryobject.md) -Auflistung| Get-Auflistung ein Mitglied-Objekts.|
|[Zugewiesen-Listenrichtlinien](../api/policy_list_assigned.md)| Auflistung von [Gruppenrichtlinien](policy.md)| Rufen Sie alle Richtlinien, die auf dieses Objekt zugewiesen.|
|[OAuth2PermissionGrant erstellen](../api/serviceprincipal_post_oauth2permissiongrants.md) |[oAuth2PermissionGrant](oauth2permissiongrant.md)| Erstellen Sie eine neue oAuth2PermissionGrant durch die Veröffentlichung auf der oauth2PermissionGrants-Auflistung.|
|[Liste oauth2PermissionGrants](../api/serviceprincipal_list_oauth2permissiongrants.md) |[oAuth2PermissionGrant](oauth2permissiongrant.md) -Auflistung| Rufen Sie eine Auflistung der oAuth2PermissionGrant-Objekts.|
|[Erstellen von ownedObject](../api/serviceprincipal_post_ownedobjects.md) |[directoryObject](directoryobject.md)| Erstellen Sie eine neue OwnedObject, indem Sie das Veröffentlichen in der OwnedObjects-Auflistung.|
|[Liste ownedObjects](../api/serviceprincipal_list_ownedobjects.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie eine Auflistung der OwnedObject-Objekts.|
|[Ersteller-Besitzer](../api/serviceprincipal_post_owners.md) |[directoryObject](directoryobject.md)| Erstellen Sie einen neuen Besitzer, indem Sie das Veröffentlichen in der Besitzer-Auflistung.|
|[Liste Besitzer](../api/serviceprincipal_list_owners.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie einen Besitzer Auflistung-Objekts.|
|[Update](../api/serviceprincipal_update.md) | [servicePrincipal](serviceprincipal.md)  |ServicePrincipal-Objekt zu aktualisieren. |
|[Löschen](../api/serviceprincipal_delete.md) | Keine |ServicePrincipal-Objekt zu löschen. |
|[checkMemberGroups](../api/serviceprincipal_checkmembergroups.md)|Zeichenfolgenauflistung||
|[getMemberGroups](../api/serviceprincipal_getmembergroups.md)|Zeichenfolgenauflistung||
|[getMemberObjects](../api/serviceprincipal_getmemberobjects.md)|Zeichenfolgenauflistung||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "servicePrincipal resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
