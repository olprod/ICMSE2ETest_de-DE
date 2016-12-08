# <a name="orgcontact-resource-type"></a>Ressourcentyp orgContact



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "directReports",
    "manager",
    "memberOf"
  ],
  "@odata.type": "microsoft.graph.orgcontact"
}-->

```json
{
  "businessPhones": ["string"],
  "city": "string",
  "companyName": "string",
  "country": "string",
  "department": "string",
  "displayName": "string",
  "givenName": "string",
  "id": "string (identifier)",
  "jobTitle": "string",
  "mail": "string",
  "mailNickname": "string",
  "mobilePhone": "string",
  "officeLocation": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "postalCode": "string",
  "proxyAddresses": ["string"],
  "state": "string",
  "streetAddress": "string",
  "surname": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Ort|String||
|Land|String||
|Abteilung|String||
|onPremisesSyncEnabled|Boolean||
|displayName|String||
|Vorname|String||
|jobTitle|String||
|onPremisesLastSyncDateTime|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Mail|String||
|mailNickname|String||
|mobilePhone|String||
|id|String| Schreibgeschützt.|
|officeLocation|String||
|Postleitzahl|String||
|Proxyadressen|Zeichenfolgenauflistung||
|Zustand|String||
|streetAddress|String||
|Nachname|String||
|businessPhones|String||

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|directReports|[DirectoryObject](directoryobject.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|
|Vorgesetzter|[directoryObject](directoryobject.md)| Schreibgeschützt.|
|Mitglied|[DirectoryObject](directoryobject.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von orgContact](../api/orgcontact_get.md) | [orgContact](orgcontact.md) |Lesen Sie Eigenschaften und Beziehungen des OrgContact-Objekts.|
|[DirectReport erstellen](../api/orgcontact_post_directreports.md) |[directoryObject](directoryobject.md)| Erstellen einer neuen DirectReport buchen DirectReports-Auflistung.|
|[Liste directReports](../api/orgcontact_list_directreports.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie eine Auflistung der DirectReport-Objekts.|
|[Erstellen von Mitglied](../api/orgcontact_post_memberof.md) |[directoryObject](directoryobject.md)| Erstellen Sie ein neues Mitglied, indem Sie das Veröffentlichen in der Auflistung Mitglied.|
|[Liste Mitglied](../api/orgcontact_list_memberof.md) |[DirectoryObject](directoryobject.md) -Auflistung| Get-Auflistung ein Mitglied-Objekts.|
|[Update](../api/orgcontact_update.md) | [orgContact](orgcontact.md)    |Update OrgContact-Objekt. |
|[Löschen](../api/orgcontact_delete.md) | Keine |OrgContact-Objekt zu löschen. |
|[checkMemberGroups](../api/orgcontact_checkmembergroups.md)|Zeichenfolgenauflistung||
|[getMemberGroups](../api/orgcontact_getmembergroups.md)|Zeichenfolgenauflistung||
|[getMemberObjects](../api/orgcontact_getmemberobjects.md)|Zeichenfolgenauflistung||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "orgContact resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->