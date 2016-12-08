# <a name="device-resource-type"></a>Ressourcentyp Gerät

Stellt ein Gerät im Verzeichnis registriert. Erbt vom [DirectoryObject](directoryobject.md).

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Get-Gerät](../api/device_get.md) | [Gerät](device.md) |Lesen Sie Eigenschaften und Beziehungen Gerät-Objekts.|
|[RegisteredOwner erstellen](../api/device_post_registeredowners.md) |[directoryObject](directoryobject.md)| Fügen Sie einen Benutzer als neuen Besitzer des Geräts, durch die Veröffentlichung auf die Eigenschaft RegisteredOwners Navigation.|
|[Liste registeredOwners](../api/device_list_registeredowners.md) |[DirectoryObject](directoryobject.md) -Auflistung| Abrufen von Benutzern, die registrierte Besitzer des Geräts in der Navigationseigenschaft RegisteredOwners sind.|
|[Registrierter Benutzer erstellen](../api/device_post_registeredusers.md) |[directoryObject](directoryobject.md)| Fügen Sie einen registrierten Benutzer für das Gerät durch die Veröffentlichung auf die Eigenschaft RegisteredUsers Navigation.|
|[Liste registeredUsers](../api/device_list_registeredusers.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die registrierte Benutzer des Geräts vom RegisteredUsers Navigationseigenschaft.|
|[Update](../api/device_update.md) | [Gerät](device.md)  |Aktualisieren Sie die Eigenschaften des Geräts-Objekts. |
|[Löschen](../api/device_delete.md) | Keine |Das Objekt zu löschen. |



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|accountEnabled|Boolean| **true** Wenn das Konto aktiviert ist. anderenfalls **false**. |
|alternativeSecurityIds|[AlternativeSecurityId](alternativesecurityid.md) -Auflistung| Der **any** -Operator ist für Filterausdrücke auf mehrwertige Eigenschaften erforderlich. Nicht NULL-Werte zulässt.           |
|approximateLastSignInDateTime|DateTimeOffset|            Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Geräte-ID|Guid|            |
|deviceMetadata|String||
|operatingSystem|String|Der Typ des Betriebssystems auf dem Gerät.|
|operatingSystemVersion|String|Die Version des Betriebssystems auf dem Gerät|
|deviceVersion|Int32|            |
|physicalIds|String-Auflistung| Nicht NULL-Werte zulässt.            |
|TrustType-Wert|String||
|onPremisesSyncEnabled|Boolean|**true,** Wenn dieses Objekt aus einem lokalen Verzeichnis synchronisiert ist. **false,** Wenn dieses Objekt ursprünglich aus einem lokalen Verzeichnis synchronisiert wurde, aber nicht mehr synchronisiert ist. **null,** Wenn dieses Objekt aus einem lokalen Verzeichnis (Standard) nie synchronisiert wurden.|
|displayName|String|Der Anzeigename für das Gerät.|
|isCompliant|Boolean|**true** , wenn das Gerät mit Richtlinien für Mobile Geräte Management (MDM) entspricht. anderenfalls **false**.|
|isManaged|Boolean|**true,** Wenn das Gerät von einer app Mobile Device Management (MDM) wie Intune verwaltet wird. anderenfalls **false**.|
|onPremisesLastSyncDateTime|DateTimeOffset|Der letzte Zeitpunkt an dem das Objekt mit dem lokalen Verzeichnis synchronisiert wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|id|String|Der eindeutige Bezeichner für das Gerät. Geerbt von [DirectoryObject](directoryobject.md). Wichtige, nicht NULL-Werte zulässt. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|registeredOwners|[DirectoryObject](directoryobject.md) -Auflistung|Benutzer, die registrierten Besitzer des Geräts sind. Schreibgeschützt. NULL-Werte zulässt.|
|registeredUsers|[DirectoryObject](directoryobject.md) -Auflistung|Benutzer, die registrierte Benutzer des Geräts sind. Schreibgeschützt. NULL-Werte zulässt.|



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "registeredOwners",
    "registeredUsers"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.device"
}-->

```json
{
  "accountEnabled": true,
  "alternativeSecurityIds": [{"@odata.type": "microsoft.graph.alternativeSecurityId"}],
  "approximateLastSignInDateTime": "String (timestamp)",
  "deviceId": "string",
  "deviceMetadata": "string",
  "deviceVersion": 1024,
  "displayName": "string",
  "id": "string (identifier)",
  "isCompliant": true,
  "isManaged": true,
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "operatingSystem": "string",
  "operatingSystemVersion": "string",
  "physicalIds": ["string"],
  "trustType": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "device resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
