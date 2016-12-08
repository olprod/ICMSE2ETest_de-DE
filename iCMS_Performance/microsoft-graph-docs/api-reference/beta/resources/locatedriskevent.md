# <a name="locatedriskevent-resource-type"></a>Ressourcentyp locatedRiskEvent

Ein Risikoereignis von [Azure Active Directory-Identität Protection](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection/) , die auf Standortdaten basiert erkannt. Befindet sich Risikotypen werden unterstützt:
* [Anmeldungen von anonymen IP-Adressen](anonymousipriskevent.md)
* [Anmeldungen von Geräten Malware infiziert](malwareriskevent.md)
* [unmöglich Reisen zu untypischen Speicherorte](impossibletravelriskevent.md)
* [Anmeldungen von verdächtigen IP-Adressen](suspiciousipriskevent.md)
* [Anmeldungen von unbekannten Standorten](unfamiliarlocationriskevent.md) Umfassende Informationen zum Risikoereignisse finden Sie in der [Dokumentation von Azure AD-Schutz](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-risk-events-types/).


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von locatedRiskEvent](../api/locatedriskevent_get.md) | [locatedRiskEvent](locatedriskevent.md) |Schreibgeschützte Eigenschaften und Beziehungen des LocatedRiskEvent-Objekts.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|closedDateTime|dateTimeOffset| Datum und Uhrzeit, die das Risikoereignis geschlossen wurde|
|createdDateTime|dateTimeOffset| Datum und Uhrzeit der Erstellung des Ereignisses Risiko. Dies ist immer größer als oder gleich dem Datetime des Ereignisses Risiko selbst. Dies ist die entsprechende Eigenschaft eines Filters beim Risikoereignisse Abfragen verwendet.|
|id|string| Schreibgeschützt|
|IP-Adresse|string| Die IP-Adresse von der Anmeldung|
|Speicherort|string| Die Position, die IP-Adresse von der Anmeldung zugeordnet ist|
|riskEventDateTime|dateTimeOffset| Datum und Uhrzeit, wann das Risikoereignis aufgetreten ist|
|riskEventStatus|string| Possible values are: `active`, `remediated`, `dismissedAsFixed`, `dismissedAsFalsePositive`, `dismissedAsIgnore`, `loginBlocked`, `closedMfaAuto`, `closedMultipleReasons`.|
|riskLevel|string| Mögliche Werte sind: `low`, `medium`, `high`.|
|riskEventType|string| Der Typ des Risikos|
|userDisplayName|string| Der Name des Benutzers gefährdet|
|Benutzer-ID|string| Die Id des Benutzers gefährdet|
|userPrincipalName|string| Der Benutzerprinzipalname des Benutzers gefährdet|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|impactedUser|[Benutzer](user.md)| Schreibgeschützt. NULL-Werte zulässt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.locatedRiskEvent"
}-->

```json
{
  "closedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "ipAddress": "string",
  "location": "string",
  "riskEventDateTime": "String (timestamp)",
  "riskEventStatus": "string",
  "riskLevel": "string",
  "riskType": "string",
  "userDisplayName": "string",
  "userId": "string",
  "userPrincipalName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "locatedRiskEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->