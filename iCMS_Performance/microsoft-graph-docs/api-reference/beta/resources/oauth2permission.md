# <a name="oauth2permission-resource-type"></a>Ressourcentyp oAuth2Permission

Stellt ein OAuth 2.0 delegiert Berechtigungsbereich. Die angegebene OAuth 2.0-Clientanwendungen (über die **RequiredResourceAccess** -Auflistung für das [Application](application.md) -Objekt) delegierte berechtigungsbereiche angefordert werden können beim Aufruf von einer Anwendung für die Ressource. Die **AppRoles** -Eigenschaft der [ServicePrincipal](serviceprincipal.md) Entität und der [Anwendung](application.md) Entität ist eine Auflistung von **oAuth2Permission**.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.oAuth2Permission"
}-->

```json
{
  "adminConsentDescription": "string",
  "adminConsentDisplayName": "string",
  "id": "guid",
  "isEnabled": true,
  "origin": "string",
  "type": "string",
  "userConsentDescription": "string",
  "userConsentDisplayName": "string",
  "value": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|adminConsentDescription|String|Berechtigung Hilfetext, der in der Admin Zustimmung und app-Zuordnung Erfahrungen angezeigt wird.|
|adminConsentDisplayName|String|Der Anzeigename für die Berechtigung, die in der Erfahrungen Admin app und Zustimmung Zuordnung angezeigt wird.|
|id|Guid|Eindeutige Berechtigungen Bereichsbezeichner innerhalb der oauth2Permissions-Auflistung.|
|isEnabled|Boolean|Beim Erstellen oder eine Berechtigung aktualisieren, müssen diese Eigenschaft auf **true** festlegen (die Standardeinstellung ist). Um eine Berechtigung zu löschen, muss diese Eigenschaft zunächst auf **false**festlegen.  Im Gespräch nachfolgende kann an dieser Stelle die Berechtigung entfernt werden.|
|Typ|String|Gibt an, von einem Endbenutzer gibt an, ob diese Berechtigung Bereich zugestimmt kann oder ob sie eine Berechtigung für die gesamte Mandanten ist, die ein Unternehmensadministrator zugestimmt werden muss.  Mögliche Werte sind "User" oder "Admin".|
|userConsentDescription|String|Berechtigung Hilfetext, der in der Zustimmung des Endbenutzers angezeigt wird.|
|userConsentDisplayName|String|Der Anzeigename für die Berechtigung, die in der Zustimmung des Endbenutzers angezeigt wird.|
|value|String|Der Wert des Bereichs geltend, dass die Anwendung für die Ressource in das OAuth 2.0-Zugriffstoken erwarten.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oAuth2Permission resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
