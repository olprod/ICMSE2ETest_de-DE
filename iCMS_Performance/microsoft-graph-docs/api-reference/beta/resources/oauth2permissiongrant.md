# <a name="oauth2permissiongrant-resource-type"></a>Ressourcentyp oAuth2PermissionGrant

Stellt die OAuth 2.0 delegiert berechtigungsbereiche erteilt wurden, die zu einer Anwendung (dargestellt durch ein Dienstprinzipal) im Rahmen des Prozesses Zustimmung Benutzer oder Administrator. 


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.oAuth2Permissiongrant"
}-->

```json
{
  "clientId": "string",
  "consentType": "string",
  "expiryTime": "String (timestamp)",
  "id": "string (identifier)",
  "principalId": "string",
  "resourceId": "string",
  "scope": "string",
  "startTime": "String (timestamp)"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|clientId|String||
|consentType|String||
|expiryTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|objectId|String| Schreibgeschützt.|
|principalId|String||
|resourceId|String||
|Bereich|String||
|startTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[OAuth2PermissionGrant abrufen](../api/oauth2permissiongrant_get.md) | [oAuth2PermissionGrant](oauth2permissiongrant.md) |Lesen Sie Eigenschaften und Beziehungen des oAuth2PermissionGrant-Objekts.|
|[Update](../api/oauth2permissiongrant_update.md) | [oAuth2PermissionGrant](oauth2permissiongrant.md)   |OAuth2PermissionGrant-Objekt zu aktualisieren. |
|[Löschen](../api/oauth2permissiongrant_delete.md) | Keine |OAuth2PermissionGrant-Objekt zu löschen. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oAuth2PermissionGrant resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->