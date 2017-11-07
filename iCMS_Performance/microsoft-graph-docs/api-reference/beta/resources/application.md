# <a name="application-resource-type"></a>Anwendung Ressourcentyp

Eine Anwendung darstellt. Jede Anwendung, die mit dem Konfigurieren Authentifizierung Azure AD beauftragt muss in einem Verzeichnis registriert werden. Dieser Schritt umfasst das Angeben von Azure AD über die Anwendung, einschließlich der URL, in dem es wurde gefunden, die URL zum Senden von Antworten nach der Authentifizierung, den URI zum Identifizieren der Anwendung und vieles mehr.  Weitere Informationen finden Sie unter [Grundlagen der Registrieren einer Anwendung in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-scenarios/#basics-of-registering-an-application-in-azure-ad). Erbt vom [DirectoryObject](directoryObject.md).


### <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "createdOnBehalfOf",
    "extensionProperties",
    "owners"
  ],
  "@odata.type": "microsoft.graph.application"
}-->

```json
{
  "addIns": [{"@odata.type": "microsoft.graph.addIn"}],
  "appId": "string",
  "appRoles": [{"@odata.type": "microsoft.graph.approle"}],
  "availableToOtherOrganizations": true,
  "displayName": "string",
  "errorUrl": "string",
  "groupMembershipClaims": "string",
  "homepage": "string",
  "id": "string (identifier)",
  "identifierUris": ["string"],
  "keyCredentials": [{"@odata.type": "microsoft.graph.keyCredential"}],
  "knownClientApplications": ["guid"],
  "logoutUrl": "string",
  "mainLogo": "stream",
  "oauth2AllowImplicitFlow": true,
  "oauth2AllowUrlPathMatching": true,
  "oauth2Permissions": [{"@odata.type": "microsoft.graph.oAuth2Permission"}],
  "oauth2RequirePostResponse": true,
  "passwordCredentials": [{"@odata.type": "microsoft.graph.passwordCredential"}],
  "publicClient": true,
  "recordConsentConditions": "string",
  "replyUrls": ["string"],
  "requiredResourceAccess": [{"@odata.type": "microsoft.graph.requiredResourceAccess"}],
  "samlMetadataUrl": "string"
}

```
### <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ |Beschreibung|
|:---------------|:--------|:----------|
|appId|String|Der eindeutige Bezeichner für die Anwendung.|
|appRoles|[AppRole](approle.md) -Auflistung|Die Auflistung der Anwendungsrollen, die eine Anwendung deklarieren kann. Diese Funktionen können Benutzer, Gruppen oder Dienstprinzipale zugewiesen werden. Nicht NULL-Werte zulässt.|
|availableToOtherOrganizations|Boolean| **true,** Wenn die Anwendung mit anderen Mandanten gemeinsam genutzt wird. anderenfalls **false**.|
|displayName|String|Der Anzeigename für die Anwendung.|
|errorUrl|String|                              |
|groupMembershipClaims|String|Eine Bitmaske, die den "Groups" Anspruch ausgestellt in einen Benutzer oder eine OAuth 2.0-Zugriffstoken, die die Anwendung erwartet konfiguriert. Die Bitmaskenwerte sind: 0: None, 1: Sicherheitsgruppen und Azure AD-Rollen, 2: reserviert und 4: reserviert. Festlegen der Bitmaske auf 7 erhalten alle Sicherheitsgruppen, Verteilergruppen und Azure AD-Directory-Rollen, denen der angemeldeten Benutzer Mitglied ist. |
|Homepage|String|Die URL zur Startseite der Anwendung.|
|identifierUris|String-Auflistung|Die URIs, die Identifizieren der Anwendung. Weitere Informationen finden Sie unter [Application Objects und Service Principal-Objekte](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-objects/). Der **any** -Operator ist für Filterausdrücke auf mehrwertige Eigenschaften erforderlich. Nicht NULL-Werte zulässt. |
|keyCredentials|[KeyCredential](keycredential.md) -Auflistung|Die Auflistung der wichtigsten Anmeldeinformationen der Anwendung nicht zugeordnete NULL-Werte zulässt.|
|knownClientApplications|GUID-Auflistung|Clientanwendungen, die für diese Ressource Anwendung gebunden sind. Zustimmung an den bekannten Clientanwendungen führt implizite Zustimmung der Anwendung Ressource über eine kombinierte Zustimmungsdialogfeld (Anzeigen der OAuth-berechtigungsbereiche vom Client und der Ressource erforderlich). Nicht NULL-Werte zulässt.|
|logoutUrl|String|                              |
|mainLogo|Stream|Das Hauptfenster Logo für die Anwendung. Keine Nullwerte zulassen|
|oauth2AllowImplicitFlow|Boolean|Gibt an, ob diese Web Application OAuth2.0 implizite Fluss Token angefordert werden kann. Der Standardwert ist **false**. Nicht NULL-Werte zulässt.|
|oauth2AllowUrlPathMatching|Boolean|Legt fest, ob, als Teil des Tokens Anforderungen OAuth 2.0, Azure AD wird Pfad Abgleich von umleitungs-URI für die Anwendung **ReplyUrls**. Der Standardwert ist **false**. Nicht NULL-Werte zulässt.|
|oauth2Permissions|[oAuth2Permission](oauth2permission.md) -Auflistung|Die Auflistung von OAuth 2.0 berechtigungsbereiche, die im Web-API (Ressource) Anwendung Clientanwendungen verfügbar macht. Diese berechtigungsbereiche können während Zustimmung Clientanwendungen gewährt werden. Nicht NULL-Werte zulässt.|
|oauth2RequirePostResponse|Boolean||
|id|String|Der eindeutige Bezeichner für die Anwendung. Geerbt von [DirectoryObject](directoryobject.md). -Taste. Nicht NULL-Werte zulässt. Schreibgeschützt.|
|passwordCredentials|[PasswordCredential](passwordcredential.md) -Auflistung|Die Auflistung von Anmeldeinformationen, die mit der Anwendung verbunden sind. Nicht NULL-Werte zulässt.|
|publicClient|Boolean|Gibt an, ob diese Anwendung einen öffentlichen Client (beispielsweise eine installierte Anwendung, die auf einem mobilen Gerät ausgeführt wird) ist.  Standard ist **false**.|
|replyUrls|String-Auflistung|Gibt die URLs der Benutzertoken für die Anmeldung an gesendet werden, oder die Umleitung, URIs, dass OAuth 2.0-Autorisierungscodes und Zugriffstoken gesendet werden. Nicht NULL-Werte zulässt.|
|requiredResourceAccess|[RequiredResourceAccess](requiredresourceaccess.md) -Auflistung|Gibt an, Ressourcen, die diese Anwendung benötigt Zugriff auf und den Satz von OAuth berechtigungsbereiche und Anwendungsrollen, die unter jedem dieser Ressourcen benötigt werden. Diese vor Konfiguration erforderlichen Ressourcenzugriff Laufwerke der Zustimmung wünschen. Nicht NULL-Werte zulässt.|
|samlMetadataUrl|String|Die URL, die SAML-Metadaten für die Anwendung.|

### <a name="relationships"></a>Beziehungen
| Beziehung | Typ |Beschreibung|
|:---------------|:--------|:----------|
|createdOnBehalfOf|[directoryObject](directoryobject.md)| Schreibgeschützt.|
|extensionProperties|[ExtensionProperty](extensionproperty.md) -Auflistung|Die Erweiterungseigenschaften mit der Anwendung verbunden sind. Schreibgeschützt. NULL-Werte zulässt.|
|Besitzer|[DirectoryObject](directoryobject.md) -Auflistung|Directory-Objekte, die Besitzer der Anwendung sind. Die Besitzer sind eine Reihe von nicht-Administrator-Benutzer, die berechtigt sind, dieses Objekt zu ändern. Erfordert Version 2013-11-08 oder höher.  Schreibgeschützt. NULL-Werte zulässt.|
|Richtlinie|Auflistung von [Gruppenrichtlinien](policy.md)|Die Richtlinien für diese Anwendung zugewiesen.|

### <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen der Anwendung](../api/application_get.md) | [Anwendung](application.md) |Lesen Sie Eigenschaften und Beziehungen des Application-Objekts.|
|[ExtensionProperty erstellen](../api/application_post_extensionproperties.md) |[extensionProperty](extensionproperty.md)| Erstellen Sie eine neue ExtensionProperty, indem Sie das Veröffentlichen in der ExtensionProperties-Auflistung.|
|[Liste extensionProperties](../api/application_list_extensionproperties.md) |[ExtensionProperty](extensionproperty.md) -Auflistung| Rufen Sie eine Auflistung der ExtensionProperty-Objekts.|
|[Zugewiesen-Listenrichtlinien](../api/policy_list_assigned.md)| Auflistung von [Gruppenrichtlinien](policy.md)| Rufen Sie alle Richtlinien, die auf dieses Objekt zugewiesen.|
|[Ersteller-Besitzer](../api/application_post_owners.md) |[directoryObject](directoryobject.md)| Erstellen Sie einen neuen Besitzer, indem Sie das Veröffentlichen der Besitzer-Auflistung.|
|[Liste Besitzer](../api/application_list_owners.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie einen Besitzer Auflistung-Objekts.|
|[Update](../api/application_update.md) | [Anwendung](application.md) |Application-Objekt zu aktualisieren. |
|[Löschen](../api/application_delete.md) | Keine |Application-Objekt zu löschen. |
|[Stellen Sie wieder her](../api/application_restore.md)|[Anwendung](application.md)|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "application resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
