# <a name="approle-resource-type"></a>AppRole Ressourcentyp

Stellt eine Anwendungsrolle, die von einer Clientanwendung aus einer anderen Anwendung aufrufen angefordert werden kann oder, die verwendet werden kann, eine Anwendung Benutzern oder Gruppen in einer angegebenen Anwendungsrolle zugewiesen. Die **AppRoles** -Eigenschaft der Entität [ServicePrincipal](serviceprincipal.md) und der [Anwendung](application.md) Entität ist eine Auflistung von **AppRole**.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.approle"
}-->

```json
{
  "allowedMemberTypes": ["string"],
  "description": "string",
  "displayName": "string",
  "id": "guid",
  "isEnabled": true,
  "origin": "string",
  "value": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|allowedMemberTypes|String-Auflistung|Gibt an, ob diese app Rollendefinition zugewiesen werden kann Benutzer und Gruppen mit der Einstellung "User" oder andere Anwendungen (, auf die diese Anwendung in Filterdaemon Service Szenarien zugreifen) mit der Einstellung auf "Application" oder beide aus.|
|description|String|Berechtigung Hilfetext, die in die Zuordnung der Admin-app angezeigt wird und die Erfahrungen stimmen.|
|displayName|String|Der Anzeigename für die Berechtigung, die in der Erfahrungen Admin app und Zustimmung Zuordnung angezeigt wird.|
|id|Guid|Eindeutiger Rollenbezeichner innerhalb der **AppRoles** -Auflistung.|
|isEnabled|Boolean|Beim Erstellen oder Aktualisieren einer Rollendefinition, muss dies auf **true** festgelegt werden (die Standardeinstellung ist). Um eine Rolle zu löschen, muss dieser zunächst auf **false**festgelegt werden.  An dieser Stelle kann diese Rolle im Gespräch nachfolgenden entfernt werden.|
|value|String|Gibt den Wert des Anspruchs Rollen, die die Anwendung erwarten sollte in die Authentifizierung und Zugriffsteuerung Token an.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->