# <a name="connector-resource-type"></a>Connector-Ressourcentyp


<!-- Not supported items
|[Create connectorGroup](../api/connector_post_memberof.md) |[connectorGroup](connectorgroup.md)| Associate a connector with a new connectorGroup by posting to the memberOf collection.|
|[Update](../api/connector_update.md) | [connector](connector.md)   | Connectors are created when they are registed with the tenant. |
|[Delete](../api/connector_delete.md) | None |Delete connector object. |

-->

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get-connector](../api/connector_get.md) | [Connector](connector.md) |Lesen Sie Eigenschaften und Beziehungen des Connector-Objekts.|
|[Liste Mitglied](../api/connector_list_memberof.md) |[ConnectorGroup](connectorgroup.md) -Auflistung| Ruft das ConnectorGroup-Objekt, das den Connector zugeordnet.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|externalIp|String|Externe IP-Adresse als ermittelte vom Dienst für den Connectorcomputer. Nur-Lese-|
|id|String| Die Objekt-Id der Verbindung. <BR>Schreibgeschützt.|
|Computername|String| Der Name des Computers, der der Connector ausgeführt wird. <BR>Nur-Lese-|
|status|string| Gibt den Status der Verbindung. Mögliche Werte sind: `active`, `inactive`. Nur-Lese- |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Mitglied|[ConnectorGroup](connectorgroup.md) -Auflistung| Das ConnectorGroup, dem das Verbinden ein Mitglied ist.<br>Schreibgeschützt. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.connector"
}-->

```json
{
  "externalIp": "String",
  "id": "String (identifier)",
  "machineName": "String",
  "status": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "connector resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
