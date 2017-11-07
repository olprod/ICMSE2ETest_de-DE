# <a name="approleassignment-resource-type"></a>Ressourcentyp appRoleAssignment

Verwendet zum Aufzeichnen, wenn ein Benutzer oder eine Gruppe zu einer Anwendung zugewiesen wird. In diesem Fall führt die rollenzuweisung Kachel Anwendung angezeigt Einrichten des Benutzers app Zugriff im Bereich. Dieser Entität kann auch zum Erteilen von einer anderen (als Dienst principal modelliert) Anwendungszugriff auf eine Ressource-Anwendung in einer bestimmten Rolle verwendet werden. Sie können erstellen, lesen, aktualisieren und Löschen von rollenzuweisungen.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.approleassignment"
}-->

```json
{
  "creationTimestamp": "String (timestamp)",
  "id": "guid (identifier)",
  "principalDisplayName": "string",
  "principalId": "guid",
  "principalType": "string",
  "resourceDisplayName": "string",
  "resourceId": "guid"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|creationTimestamp|DateTimeOffset|Die Uhrzeit der Erstellung der erteilen. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|id|Guid|Die Rolle-Id, die den Prinzipal zugewiesen wurde.  Diese Rolle muss mit der Ziel-Ressource Anwendung **ResourceId** in seiner **AppRoles** -Eigenschaft deklariert werden. In denen die Ressource keine Berechtigungen nicht deklarieren, muss eine Standard-Id (0 (null) GUID) angegeben werden. -Taste. Nicht NULL-Werte zulässt. |
|principalDisplayName|String|Der Anzeigename des Prinzipals, denen den Zugriff gewährt wurde.|
|principalId|Guid|Der eindeutige Bezeichner (**Id**) für den Prinzipal, den Zugriff gewährt wird. Erforderliche auf erstellen.            |
|principalType|String|Der Typ des Prinzipals.  Dies kann entweder "User", "Group" oder "ServicePrincipal" sein.|
|resourceDisplayName|String|Der Anzeigename der Ressource mit der die Zuordnung hergestellt wurde.|
|resourceId|Guid|Der eindeutige Bezeichner (**Id**) für die Zielressource (Service Principal) für die die Zuordnung erstellt wurde.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von appRoleAssignment](../api/approleassignment_get.md) | [appRoleAssignment](approleassignment.md) |Lesen Sie Eigenschaften und Beziehungen des AppRoleAssignment-Objekts.|
|[Update](../api/approleassignment_update.md) | [appRoleAssignment](approleassignment.md)   |Aktualisieren Sie AppRoleAssignment-Objekts. |
|[Löschen](../api/approleassignment_delete.md) | Keine |Löschen Sie AppRoleAssignment Objekt. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appRoleAssignment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->