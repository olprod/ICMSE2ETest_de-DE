# <a name="driverecipient-resource-type"></a>Ressourcentyp driveRecipient

Die Ressource Empfänger stellt einen einzelnen Empfänger für die Aktion [einladen](../api/item_invite.md) .

## <a name="json-representation"></a>JSON-Darstellung

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.driveRecipient", "optionalProperties": ["alias", "objectId", "email"] } -->
```json
{
  "email": "string",
  "alias": "string",
  "objectId": "string",
}
```

## <a name="properties"></a>Eigenschaften
Die Ressource der Empfänger hat diese Eigenschaften.

| Name der Eigenschaft | Typ   | Beschreibung                                                                                             |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------|
| E-Mail         | String | Die e-Mail-Adresse für den Empfänger, wenn der Empfänger eine zugeordnete e-Mail-Adresse verfügt.                  |
| Alias         | String | Der Alias des Objekts Domäne für eine e-Mail-Adresse ist nicht verfügbar (z. B. Sicherheitsgruppen). |
| objectId      | String | Der eindeutige Bezeichner für den Empfänger im Verzeichnis.                                               |

## <a name="remarks"></a>Hinweise
Wenn Sie [einladen](../api/item_invite.md) zum Hinzufügen von Berechtigungen verwenden, kann die DriveRecipient **e-Mail**, den **Alias**oder **ObjectId**angeben. Nur eine der folgenden Werte ist erforderlich.

<!-- {
  "type": "#page.annotation",
  "description": "Recipients resource defines a single recipient for the sharing invitation and permissions collection.",
  "keywords": "sharing,share,permissions,action.invite,invite,email",
  "section": "documentation"
} -->
