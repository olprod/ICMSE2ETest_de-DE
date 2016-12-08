# <a name="update-serviceprincipal"></a>Serviceprincipal aktualisieren

Aktualisieren Sie die Eigenschaften des Serviceprincipal-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen:
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /servicePrincipals/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|accountEnabled|Boolean|                **true,** Wenn der Prinzipal Dienstkontos aktiviert ist. anderenfalls **false**.            |
|appDisplayName|String|Der Anzeigename, der von der zugeordneten Anwendung verfügbar gemacht werden.|
|appId|String|Der eindeutige Bezeichner für die zugewiesene Anwendung (dessen **AppId** -Eigenschaft).|
|appRoleAssignmentRequired|Boolean|Gibt an, ob ein **AppRoleAssignment** für einen Benutzer oder Gruppe erforderlich ist, bevor Azure AD einen Benutzer oder eine Zugriffstoken an die Anwendung ausstellt.                            **Notes**: erfordert Version 1.5 oder neuere, nicht NULL-Werte zulässt.            |
|appRoles|appRole|Die Rollen der Anwendung von der zugeordneten Anwendung verfügbar gemacht werden. Weitere Informationen finden Sie in der Anwendung Entität **Notizen**die Eigenschaftendefinition **AppRoles** : erfordert Version 1.5 oder neuere, nicht NULL-Werte zulässt.            |
|displayName|String|Der Anzeigename für den Dienstprinzipal.|
|errorUrl|String|            |
|Homepage|String|Die URL zur Homepage der zugeordneten Anwendung.|
|keyCredentials|keyCredential|Die Auflistung von wichtigen Anmeldeinformationen, die dem Prinzipal Dienst zugeordnet sind.                            **Notes**: nicht auf NULL festgelegt.            |
|logoutUrl|String|            |
|oauth2Permissions|oAuth2Permission|Die OAuth 2.0-Berechtigungen von der zugeordneten Anwendung verfügbar gemacht werden. Weitere Informationen finden Sie in der Definition der **oauth2Permissions** -Eigenschaft auf die Entität Anwendung.                            **Notes**: erfordert Version 1.5 oder neuere, nicht NULL-Werte zulässt.            |
|passwordCredentials|passwordCredential|Die Auflistung von Anmeldeinformationen zugeordnet den Dienstprinzipal.                            **Notes**: nicht auf NULL festgelegt.            |
|preferredTokenSigningKeyThumbprint|String|Nur zur internen Verwendung reserviert. Schreiben oder verlassen sich andernfalls auf diese Eigenschaft nicht. Kann in zukünftigen Versionen entfernt werden.                            **Notes**: erfordert Version 1.5 oder höher.            |
|publisherName|String|Der Anzeigename des Mandanten in dem verbundenen Anwendung angegeben wird.|
|replyUrls|String|Die URLs, dass Benutzertoken, um für die Anmeldung mit der zugeordneten Anwendung oder die Umleitung URIs, dass OAuth 2.0 Autorisierungscodes gesendet werden und Zugriffstoken werden für die zugewiesene Anwendung an.                            **Notes**: nicht auf NULL festgelegt.            |
|samlMetadataUrl|String|            |
|servicePrincipalNames|String|Die URIs, mit denen die zugewiesene Anwendung identifiziert. Weitere Informationen finden Sie unter [Application Objects und Service Principal-Objekte](https://msdn.microsoft.com/en-us/library/azure/dn132633.aspx).                            **Notes**: nicht Nullwerte zulassen **any** -Operator ist erforderlich für Filterausdrücke auf mehrwertige Eigenschaften; Weitere Informationen finden Sie unter [unterstützte Abfragen, Filter und Optionen Suchseiten](https://msdn.microsoft.com/library/azure/dn727074.aspx).            |
|Tags|String|                                        **Notes**: nicht auf NULL festgelegt.            |

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [ServicePrincipal](../resources/serviceprincipal.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_serviceprincipal"
}-->
```http
PATCH https://graph.microsoft.com/beta/servicePrincipals/<id>
Content-type: application/json
Content-length: 391

{
  "accountEnabled": true,
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
  "appDisplayName": "appDisplayName-value",
  "appId": "appId-value",
  "appOwnerOrganizationId": "appOwnerOrganizationId-value",
  "appRoleAssignmentRequired": true
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.serviceprincipal"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 391

{
  "accountEnabled": true,
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
  "appDisplayName": "appDisplayName-value",
  "appId": "appId-value",
  "appOwnerOrganizationId": "appOwnerOrganizationId-value",
  "appRoleAssignmentRequired": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update serviceprincipal",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
