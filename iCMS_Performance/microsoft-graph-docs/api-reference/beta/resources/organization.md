# <a name="organization-resource-type"></a>Organisation Ressourcentyp

Stellt eine Azure Active Directory-Mandanten. Nur die Lese- und Aktualisierungsvorgänge werden auf Mandanten unterstützt. Erstellen und Delete werden nicht unterstützt. Erbt vom [DirectoryObject](directoryobject.md).

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen der Organisation](../api/organization_get.md) | [Organisation](organization.md) |Lesen Sie Eigenschaften und Beziehungen Organisation-Objekts.|
|[Update](../api/organization_update.md) | [Organisation](organization.md)  |Organisationsobjekt zu aktualisieren. (Nur die Eigenschaften **MarketingNotificationMails** und **TechnicalNotificationMails** können aktualisiert werden.) |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assignedPlans|[AssignedPlan](assignedplan.md) -Auflistung|Die Auflistung der Servicepläne den Mandanten zugeordnet. Nicht NULL-Werte zulässt.            |
|Ort|String|            |
|companyLastDirSyncTime|DateTimeOffset|Datum und die Uhrzeit zuletzt der Mandanten mit der lokalen Verzeichnis synchronisiert. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Land|String|            |
|countryLetterCode|String|            |
|deletionTimestamp|DateTimeOffset|Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|dirSyncEnabled|Boolean|**true,** Wenn dieses Objekt aus einem lokalen Verzeichnis synchronisiert ist. **false,** Wenn dieses Objekt ursprünglich aus einem lokalen Verzeichnis synchronisiert wurde, aber nicht mehr synchronisiert ist. **null,** Wenn dieses Objekt aus einem lokalen Verzeichnis (Standard) nie synchronisiert wurden.|
|displayName|String|Der Anzeigename für den Mandanten.|
|id|String|Der eindeutige Bezeichner für den Mandanten. Geerbt von [DirectoryObject](directoryobject.md). -Taste. Nicht NULL-Werte zulässt. Schreibgeschützt.|
|marketingNotificationEmails|String-Auflistung| Nicht NULL-Werte zulässt.            |
|objectType|String|Eine Zeichenfolge, die den Objekttyp angibt. Für den Mandanten ist der Wert immer "Company". |
|postalCode|String|            |
|preferredLanguage|String|            |
|provisionedPlans|[ProvisionedPlan](provisionedplan.md) -Auflistung| Nicht NULL-Werte zulässt.            |
|provisioningErrors|ProvisioningError-Auflistung| Nicht NULL-Werte zulässt.            |
|securityComplianceNotificationMails|String-Auflistung||
|securityComplianceNotificationPhones|String-Auflistung||
|Zustand|String|            |
|Straße|String|            |
|technicalNotificationMails|String-Auflistung| Nicht NULL-Werte zulässt. |
|telephoneNumber|String|            |
|verifiedDomains|[VerifiedDomain](verifieddomain.md) -Auflistung|Die Auflistung von Domänen, die diesen Mandanten zugeordnet. Nicht NULL-Werte zulässt.            |

## <a name="relationships"></a>Beziehungen
Keine

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.organization"
}-->

```json
{
  "assignedPlans": [{"@odata.type": "microsoft.graph.assignedPlan"}],
  "businessPhones": ["string"],
  "city": "string",
  "country": "string",
  "countryLetterCode": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "marketingNotificationEmails": ["string"],
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "postalCode": "string",
  "preferredLanguage": "string",
  "provisionedPlans": [{"@odata.type": "microsoft.graph.provisionedPlan"}],
  "securityComplianceNotificationMails": ["string"],
  "securityComplianceNotificationPhones": ["string"],
  "state": "string",
  "street": "string",
  "technicalNotificationMails": ["string"],
  "verifiedDomains": [{"@odata.type": "microsoft.graph.verifiedDomain"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "organization resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
