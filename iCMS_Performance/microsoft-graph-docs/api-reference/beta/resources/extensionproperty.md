# <a name="extensionproperty-resource-type"></a>Ressourcentyp extensionProperty

Ermöglicht es einer Anwendung zum Definieren und verwenden eine Reihe von zusätzlichen Eigenschaften, die Directory-Objekte (Benutzer, Gruppen, Mandanten Details, Geräte, Anwendungen und Dienstprinzipale) ohne die Anwendungsbereiche, einen externen Datenspeicher hinzugefügt werden können. Weitere Informationen zu Erweiterungseigenschaften finden Sie unter [Azure AD-Diagramm-API-Directory-Erweiterungen](https://msdn.microsoft.com/en-us/library/azure/dn720459.aspx). Erbt vom [DirectoryObject](directoryobject.md).


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.extensionproperty"
}-->

```json
{
  "appDisplayName": "string",
  "dataType": "string",
  "id": "string (identifier)",
  "isSyncedFromOnPremises": true,
  "name": "string",
  "targetObjects": ["string"]
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|appDisplayName|String|            |
|Datentyp|String|Gibt den Typ des hinzuzufügenden Directory Extension-Eigenschaft.   Typen werden unterstützt: ganze Zahl, LargeInteger, DateTime (muss angegeben werden im ISO 8601 - DateTime in UTC gespeichert ist), Binary, Boolean und Zeichenfolge.|
|isSyncedFromOnPremises|Boolean|Gibt an, ob die Extension-Eigenschaft aus dem auf lokalen Verzeichnis synchronisiert ist.                            **Notes**: nicht auf NULL festgelegt.            |
|name|String|Gibt den Anzeigenamen für das Verzeichnis Extension-Eigenschaft.                            **Notes**: nicht auf NULL festgelegt.            |
|id|String|Der eindeutige Bezeichner für die Berechtigungsbereich. Geerbt von [DirectoryObject](directoryobject.md).                            **Notes**: **Schlüssel**, unveränderlich, nicht NULL-Werte zulässt, eindeutig.             Schreibgeschützt.|
|targetObjects|String-Auflistung|Die Directory-Objekte, die die Directory Extension-Eigenschaft hinzugefügt wird.  Unterstützte Directory-Entitäten, die erweitert werden kann: "User", "Group", "Organisation", "Gerät", "Anwendung" und "ServicePrincipal" **Notes**: nicht auf NULL festgelegt.            |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von extensionProperty](../api/extensionproperty_get.md) | [extensionProperty](extensionproperty.md) |Lesen Sie Eigenschaften und Beziehungen des ExtensionProperty-Objekts.|
|[Update](../api/extensionproperty_update.md) | [extensionProperty](extensionproperty.md)   |ExtensionProperty-Objekt zu aktualisieren. |
|[Löschen](../api/extensionproperty_delete.md) | Keine |ExtensionProperty-Objekt zu löschen. |
|[checkMemberGroups](../api/extensionproperty_checkmembergroups.md)|String-Auflistung||
|[getMemberGroups](../api/extensionproperty_getmembergroups.md)|String-Auflistung||
|[getMemberObjects](../api/extensionproperty_getmemberobjects.md)|String-Auflistung||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "extensionProperty resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
