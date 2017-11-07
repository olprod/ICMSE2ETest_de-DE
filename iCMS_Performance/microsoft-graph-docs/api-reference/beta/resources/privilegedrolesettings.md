# <a name="privilegedrolesettings-resource-type"></a>Ressourcentyp privilegedRoleSettings

Stellt die Einstellungen für eine privilegierten Rolle.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von privilegedRoleSettings](../api/privilegedrolesettings_get.md) | [privilegedRoleSettings](privilegedrolesettings.md) |Lesen Sie Eigenschaften und Beziehungen des PrivilegedRoleSettings-Objekts.|
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|elevationDuration|duration|Die Dauer, wenn die Rolle aktiviert ist.|
|id|string| Der eindeutige Bezeichner für die rolleneinstellungen. Schreibgeschützt.|
|isMfaOnElevationConfigurable|boolean|**true,** Wenn MfaOnElevation konfigurierbar ist. **false,** Wenn MfaOnElevation nicht konfigurierbar ist.|
|lastGlobalAdmin|boolean|Verwendet nur intern.|
|maxElavationDuration|duration|Maximale Dauer für die aktivierte Rolle.|
|mfaOnElevation|boolean|**true,** Wenn mehrstufiger Authentifizierung DAS erforderlich ist, um die Rolle zu aktivieren. **false,** Wenn mehrstufiger Authentifizierung DAS nicht erforderlich ist, um die Rolle zu aktivieren.|
|minElevationDuration|duration|Minimale Dauer für die aktivierte Rolle.|
|notificationToUserOnElevation|boolean|**true,** Wenn für den Endbenutzer Benachrichtigung senden, wenn die Rolle aktiviert ist. **false,** Wenn keine Benachrichtigung senden, wenn die Rolle aktiviert ist.|
|ticketingInfoOnElevation|boolean|**true,** Wenn Sie die Informationen zur benötigen beim Aktivieren der Rolle. **false,** Wenn die Informationen zur nicht erforderlich bei ist die Rolle zu aktivieren.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleSettings"
}-->

```json
{
  "elevationDuration": "String (timestamp)",
  "id": "string (identifier)",
  "isMfaOnElevationConfigurable": true,
  "lastGlobalAdmin": true,
  "maxElavationDuration": "String (timestamp)",
  "mfaOnElevation": true,
  "minElevationDuration": "String (timestamp)",
  "notificationToUserOnElevation": true,
  "ticketingInfoOnElevation": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleSettings resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->