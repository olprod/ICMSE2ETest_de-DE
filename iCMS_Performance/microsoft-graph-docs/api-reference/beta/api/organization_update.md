# <a name="update-organization"></a>Organisation aktualisieren

Aktualisieren Sie die Eigenschaften der aktuell authentifizierten Organisation.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /organization

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assignedPlans|AssignedPlan|Die Auflistung der Servicepläne den Mandanten zugeordnet.                            **Notes**: nicht auf NULL festgelegt.            |
|Ort|String|            |
|companyLastDirSyncTime|DateTimeOffset|Datum und die Uhrzeit zuletzt der Mandanten mit der lokalen Verzeichnis synchronisiert.|
|Land|String|            |
|countryLetterCode|String|            |
|deletionTimestamp|DateTimeOffset||
|dirSyncEnabled|Boolean|**true,** Wenn dieses Objekt aus einem lokalen Verzeichnis synchronisiert ist. **false,** Wenn dieses Objekt ursprünglich aus einem lokalen Verzeichnis synchronisiert wurde, aber nicht mehr synchronisiert ist. **null,** Wenn dieses Objekt aus einem lokalen Verzeichnis (Standard) nie synchronisiert wurden.|
|displayName|String|Der Anzeigename für den Mandanten.|
|marketingNotificationEmails|String|                                        **Notes**: nicht auf NULL festgelegt.            |
|objectType|String|Eine Zeichenfolge, die den Objekttyp angibt. Für den Mandanten ist der Wert immer "Company". Geerbt von [DirectoryObject](../resources/directoryobject.md).|
|postalCode|String|            |
|preferredLanguage|String|            |
|provisionedPlans|ProvisionedPlan|                                        **Notes**: nicht auf NULL festgelegt.            |
|provisioningErrors|ProvisioningError|                                        **Notes**: nicht auf NULL festgelegt.            |
|securityComplianceNotificationMails|String||
|securityComplianceNotificationPhones|String||
|Zustand|String|            |
|Straße|String|            |
|technicalNotificationMails|String|                                        **Notes**: nicht auf NULL festgelegt.            |
|telephoneNumber|String|            |
|verifiedDomains|VerifiedDomain|Die Auflistung von Domänen, die diesen Mandanten zugeordnet.                            **Notes**: nicht auf NULL festgelegt.            |

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [Organisation](../resources/organization.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_organization"
}-->
```http
PATCH https://graph.microsoft.com/beta/organization
Content-type: application/json
Content-length: 411

{
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.organization"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 411

{
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update organization",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
