# <a name="impossibletravelriskevent-resource-type"></a>Ressourcentyp impossibleTravelRiskEvent

Ein Risikoereignis von [Azure Active Directory-Identität Protection](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection/) , wobei zwei Konto Anmeldungen von Speicherorten für die Benutzer untypischen auftreten, und es ist nicht möglich, zwischen den Standorten in die Dauer zwischen den Anmeldungen Reisen, erkannt. Umfassende Informationen zum Risikoereignisse finden Sie in der [Dokumentation Azure AD-Schutz](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-risk-events-types/).


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von impossibleTravelRiskEvent](../api/impossibletravelriskevent_get.md) | [impossibleTravelRiskEvent](impossibletravelriskevent.md) |Lesen Sie Eigenschaften und Beziehungen des ImpossibleTravelRiskEvent-Objekts.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|closedDateTime|dateTimeOffset| Datum und Uhrzeit, die das Risikoereignis geschlossen wurde|
|createdDateTime|dateTimeOffset| Datum und Uhrzeit der Erstellung des Ereignisses Risiko. Dies ist immer größer als oder gleich dem Datetime des Ereignisses Risiko selbst. Dies ist die entsprechende Eigenschaft eines Filters beim Risikoereignisse Abfragen verwendet.|
|deviceInformation|string| Informationen über das Gerät|
|id|string| Nur-Lese-|
|IP-Adresse|string| IP-Adresse des zweiten Anmeldung|
|isAtypicalLocation|boolean| Wenn eine der Speicherorte untypischen für den Benutzer ist.|
|Speicherort|string| Der Speicherort, der IP-Adresse des zweiten Anmeldung zugeordnet ist|
|previousIPAddress|string| Die IP-Adresse von der ersten Anmeldung|
|previousLocation|string| Den Speicherort der IP-Adresse von der ersten Anmeldung zugeordnet ist|
|previousSigninDateTime|dateTimeOffset| Datum und Uhrzeit der ersten Anmeldung|
|riskEventDateTime|dateTimeOffset| Datum und Uhrzeit des zweiten Anmeldung|
|riskEventStatus|string| Possible values are: `active`, `remediated`, `dismissedAsFixed`, `dismissedAsFalsePositive`, `dismissedAsIgnore`, `loginBlocked`, `closedMfaAuto`, `closedMultipleReasons`.|
|riskLevel|string| Mögliche Werte sind: `low`, `medium`, `high`.|
|riskEventType|string| Der Typ des Risikos|
|userAgent|string| Benutzeragentzeichenfolge des Browsers|
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
  "@odata.type": "microsoft.graph.impossibleTravelRiskEvent"
}-->

```json
{
  "closedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "deviceInformation": "string",
  "id": "string (identifier)",
  "ipAddress": "string",
  "isAtypicalLocation": true,
  "location": "string",
  "previousIPAddress": "string",
  "previousLocation": "string",
  "previousSigninDateTime": "String (timestamp)",
  "riskEventDateTime": "String (timestamp)",
  "riskEventStatus": "string",
  "riskLevel": "string",
  "riskType": "string",
  "userAgent": "string",
  "userDisplayName": "string",
  "userId": "string",
  "userPrincipalName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "impossibleTravelRiskEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->