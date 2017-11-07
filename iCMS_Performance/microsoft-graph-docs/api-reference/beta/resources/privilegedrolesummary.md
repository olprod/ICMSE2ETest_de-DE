# <a name="privilegedrolesummary-resource-type"></a>Ressourcentyp privilegedRoleSummary

Die Zusammenfassung für eine bestimmte Rolle Statistiken.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von privilegedRoleSummary](../api/privilegedrolesummary_get.md) | [privilegedRoleSummary](privilegedrolesummary.md) |Lesen Sie Eigenschaften und Beziehungen des PrivilegedRoleSummary-Objekts.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|elevatedCount|Int32|Die Anzahl der Benutzer, die die Rolle zugewiesen haben, ist aktiviert.|
|id|string| Der eindeutige Bezeichner für die Rolle. Schreibgeschützt.|
|managedCount|Int32|Die Anzahl der Benutzer, die die Rolle zugewiesen haben, aber die Rolle ist deaktiviert.|
|mfaEnabled|boolean|**true,** Wenn die Rolle Aktivierung mehrstufiger Authentifizierung DAS erforderlich sind. **false** , wenn die Rolle Aktivierung mehrstufiger Authentifizierung DAS erforderlich ist.|
|status|string| Mögliche Werte sind: `ok`, `bad`. Der Wert hängt das Verhältnis von (ManagedCount / UsersCount). Wenn das Verhältnis einen vordefinierten Schwellenwert unterschreitet `ok` wird zurückgegeben. Andernfalls `bad` wird zurückgegeben.|
|usersCount|Int32|Die Anzahl der Benutzer, die mit der Rolle zugewiesen sind.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleSummary"
}-->

```json
{
  "elevatedCount": 1024,
  "id": "string (identifier)",
  "managedCount": 1024,
  "mfaEnabled": true,
  "status": "string",
  "usersCount": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleSummary resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->