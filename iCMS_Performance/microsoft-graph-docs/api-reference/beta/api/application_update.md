# <a name="update-application"></a>Aktualisieren der Anwendung

Aktualisieren Sie die Eigenschaften des Application-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /applications/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind verwalten ihre vorherigen Werte oder neu berechnet auf der Grundlage Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|appId|String|Der eindeutige Bezeichner für die Anwendung.|
|appRoles|appRole|Die Auflistung der Anwendungsrollen, die eine Anwendung deklarieren kann. Diese Funktionen können Benutzer, Gruppen oder Dienstprinzipale zugewiesen werden.                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|availableToOtherOrganizations|Boolean|                **true,** Wenn die Anwendung mit anderen Mandanten gemeinsam genutzt wird. anderenfalls **false**.|
|displayName|String|Der Anzeigename für die Anwendung.|
|errorUrl|String|                              |
|groupMembershipClaims|String|Eine Bitmaske, die den "Groups" Anspruch ausgestellt in einen Benutzer oder eine OAuth 2.0-Zugriffstoken, die die Anwendung erwartet konfiguriert. Die Bitmaskenwerte sind: 0: None, 1: Sicherheitsgruppen und Azure AD-Rollen, 2: reserviert und 4: reserviert. Festlegen der Bitmaske auf 7 erhalten alle Sicherheitsgruppen, Verteilergruppen und Azure AD-Directory-Rollen, denen der angemeldeten Benutzer Mitglied ist.                              **Notes**: erfordert Version 1.5.|
|Homepage|String|Die URL der Ressourcenkennzeichnung™ s Homepage.|
|identifierUris|String|Die URIs, die die Anwendung zu bestimmen. Weitere Informationen finden Sie unter [Application Objects und Service Principal-Objekte](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-objects/).                              **Notes:** nicht NULL-Werte zulässt, der **any** -Operator ist erforderlich für Filterausdrücke auf mehrwertige Eigenschaften; Weitere Informationen finden Sie unter [unterstützte Abfragen, Filter, und Paging-Optionen](https://msdn.microsoft.com/library/azure/dn727074.aspx).|
|keyCredentials|keyCredential|Die Auflistung der wichtigsten Anmeldeinformationen der Anwendung zugeordneten **Notes:** keine Nullwerte zulassen|
|knownClientApplications|Guid|Clientanwendungen, die für diese Ressource Anwendung gebunden sind. Zustimmung an den bekannten Clientanwendungen führt implizite Zustimmung der Ressource Anwendung über eine kombinierte Zustimmungsdialogfeld (Anzeigen der OAuth-berechtigungsbereiche vom Client und der Ressource erforderlich).                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|logoutUrl|String|                              |
|mainLogo|Stream|Das Hauptfenster Logo für die Anwendung.                              **Notes:** keine Nullwerte zulassen|
|oauth2AllowImplicitFlow|Boolean|Gibt an, ob dieser Webanwendung OAuth2.0 implizite Flow Token anfordern kann. Der Standardwert ist **false**.                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|oauth2AllowUrlPathMatching|Boolean|Legt fest, ob, als Teil des Tokens Anforderungen OAuth 2.0, Azure AD wird Pfad Abgleich von umleitungs-URI für die Anwendung **ReplyUrls**. Der Standardwert ist **false**.                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|oauth2Permissions|oAuth2Permission|Die Auflistung von OAuth 2.0 berechtigungsbereiche, die im Web-API (Ressource) Anwendung Clientanwendungen verfügbar macht. Diese berechtigungsbereiche können während Zustimmung Clientanwendungen gewährt werden.                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|oauth2RequirePostResponse|Boolean||
|passwordCredentials|passwordCredential|Die Auflistung von Anmeldeinformationen, die mit der Anwendung verbunden sind.                              **Notes:** nicht Nullwerte zulassen|
|publicClient|Boolean|Gibt an, ob diese Anwendung einen öffentlichen Client (beispielsweise eine installierte Anwendung, die auf einem mobilen Gerät ausgeführt wird) ist.  Standard ist **false**.|
|replyUrls|String|Gibt die URLs der Benutzertoken für die Anmeldung an gesendet werden, oder die Umleitung, URIs, dass OAuth 2.0 Autorisierungscodes und Zugriffstoken gesendet werden.                              **Notes:** nicht Nullwerte zulassen|
|requiredResourceAccess|requiredResourceAccess|Gibt die Ressourcen, die diese Anwendung benötigt Zugriff auf und den Satz von OAuth berechtigungsbereiche und Anwendungsrollen, die unter jeder dieser Ressourcen benötigt werden. Diese vor Konfiguration erforderlich Ressourcenzugriff Laufwerke der Zustimmung wünschen.                              **Notes**: erfordert Version 1.5, nicht NULL-Werte zulässt.|
|samlMetadataUrl|String|Die URL, die SAML-Metadaten für die Anwendung.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierten [Application](../resources/application.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_application"
}-->
```http
PATCH https://graph.microsoft.com/beta/applications/<id>
Content-type: application/json
Content-length: 636

{
  "addIns": [
    {
      "id": "id-value",
      "type": "type-value",
      "properties": [
        {
          "key": "key-value",
          "value": "value-value"
        }
      ]
    }
  ],
  "appId": "appId-value",
  "appRoles": [
    {
      "allowedMemberTypes": [
        "allowedMemberTypes-value"
      ],
      "description": "description-value",
      "displayName": "displayName-value",
      "id": "id-value",
      "isEnabled": true,
      "origin": "origin-value",
      "value": "value-value"
    }
  ],
  "availableToOtherOrganizations": true,
  "displayName": "displayName-value",
  "errorUrl": "errorUrl-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.application"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 636

{
  "addIns": [
    {
      "id": "id-value",
      "type": "type-value",
      "properties": [
        {
          "key": "key-value",
          "value": "value-value"
        }
      ]
    }
  ],
  "appId": "appId-value",
  "appRoles": [
    {
      "allowedMemberTypes": [
        "allowedMemberTypes-value"
      ],
      "description": "description-value",
      "displayName": "displayName-value",
      "id": "id-value",
      "isEnabled": true,
      "origin": "origin-value",
      "value": "value-value"
    }
  ],
  "availableToOtherOrganizations": true,
  "displayName": "displayName-value",
  "errorUrl": "errorUrl-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update application",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->