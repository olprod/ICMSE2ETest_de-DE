# <a name="connectorgroup-resource-type"></a>Ressourcentyp connectorGroup




## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von connectorGroup](../api/connectorgroup_get.md) | [connectorGroup](connectorgroup.md) |Lesen Sie Eigenschaften und Beziehungen des ConnectorGroup-Objekts.|
|[Anwendung erstellen](../api/connectorgroup_post_applications.md) |[Anwendung](application.md)| Ordnen Sie eine Anwendung mit der Connector-Gruppe durch das Veröffentlichen in der Auflistung Applications.|
|[Liste applications](../api/connectorgroup_list_applications.md) |[Application](application.md) -Auflistung| Ruft die Auflistung der verbundenen Anwendung-Objekts.|
|[Erstellen Sie connector](../api/connectorgroup_post_members.md) |[Connector](connector.md)| Hinzufügen einer Verbindung an den Konnektor Gruppe durch die Veröffentlichung auf die Members-Auflistung.|
|[Mitglieder der Liste](../api/connectorgroup_list_members.md) |[Connector](connector.md) -Auflistung| Rufen Sie einen Connector-Auflistung-Objekts.|
|[Update](../api/connectorgroup_update.md) | [connectorGroup](connectorgroup.md)    |Aktualisieren Sie ConnectorGroup-Objekts. |
|[Löschen](../api/connectorgroup_delete.md) | Keine |Löschen Sie ConnectorGroup Objekt. Sämtliche Verbinder muss entfernen, bevor eine Gruppe Connector gelöscht werden kann. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|connectorGroupType|string| Der Typ des Connectors, die mit der Gruppe verwendet werden. Mögliche Werte sind: `applicationProxy`.|
|id|String| Die Objekt-Id der connectorGroup|
|isDefault|Boolean| Gibt an, ob die ConnectorGroup der Standardgruppe Connector. Nur ein einzelner Connector Gruppe kann die Standard-ConnectorGroup und wird vom System festgelegt.|
|name|String| Der Name der ConnectorGroup zugeordnet.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anwendungen|[Application](application.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|
|Member|[Connector](connector.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.connectorGroup"
}-->

```json
{
  "connectorGroupType": "string",
  "id": "String (identifier)",
  "isDefault": true,
  "name": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "connectorGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
