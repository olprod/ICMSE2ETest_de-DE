# <a name="privilegedoperationevent-resource-type"></a>PrivilegedOperationEvent Ressourcentyp

Stellt ein Audit-Ereignis, das für die Vorgänge Rolle von privilegierten Identity Management generiert wird, wie ein Administrator privilegierte Rollen verwaltet, ein Benutzer seine Rolle aktiviert und ein Benutzers seiner Rolle deaktiviert.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Liste privilegedOperationEvent](../api/privilegedoperationevent_list.md) | [PrivilegedOperationEvent](privilegedoperationevent.md) -Auflistung. |Rufen Sie die Auflistung von PrivilegedOperationEvent-Objekten.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|zusätzliche Informationen|string|Ausführliche lesbare human Informationen für das Ereignis.|
|creationDateTime|dateTimeOffset|Gibt den Zeitpunkt der Erstellung des Ereignisses.|
|expirationDateTime|dateTimeOffset|Dies wird nur verwendet, wenn die RequestType "Elevate", und es gibt die Ablaufzeit für die Aktivierung der Rolle an.|
|id|string|Der eindeutige Bezeichner für PrivilegedOperationEvent. Schreibgeschützt.|
|referenceKey|string|Während der Aktivierung der Rolle Vorfall-Anforderung Ticket-Nummer. Der Wert wird dargestellt, nur, wenn die Ticket-Nummer bei der Aktivierung der Rolle bereitgestellt wird.|
|referenceSystem|string|Vorfall/Anforderung mitgearbeitet während der Aktivierung Tole bereitgestellt. Nur wenn das System Ticket während der Aktivierung Role bereitgestellt wird, wird der Wert angezeigt.|
|requestType|string|Der Typ der Anforderung Operation. Beispieltypen werden konnte: zuweisen (rollenzuweisung), Elevate (Role-Aktivierung), Zuweisung entfernen (Remove rollenzuweisung) und Unelevate (Rolle Deaktivierung).|
|requestorId|string|Die Benutzer-Id der anfordernden Person, die den Vorgang initiiert.|
|requestorName|string|Der Name der anfordernden Person, die den Vorgang initiiert.|
|roleId|string|Die Id des der Rolle, die den Vorgang zugeordnet ist.|
|roleName|string|Der Name der Rolle.|
|tenantId|string|Die Id des Mandanten (Unternehmen).|
|Benutzer-ID|string|Die Id des Benutzers, der den Vorgang zugeordnet ist.|
|userMail|string|E-Mail des Benutzers.|
|Benutzername|string|Anzeigename des Benutzers.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedOperationEvent"
}-->

```json
{
  "additionalInformation": "string",
  "creationDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "requestType": "string",
  "requestorId": "string",
  "requestorName": "string",
  "roleId": "string",
  "roleName": "string",
  "tenantId": "string",
  "userId": "string",
  "userMail": "string",
  "userName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedOperationEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
