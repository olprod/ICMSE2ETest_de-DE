# <a name="drive-resource-type"></a>Laufwerk Ressourcentyp

Das Objekt der obersten Ebene innerhalb eines Benutzers OneDrive ist.
Ein Benutzer muss immer mindestens ein Laufwerk verfügbar – Standard Laufwerk.
Die Laufwerkressource stellt auch eine Dokumentbibliothek auf einer SharePoint-Website oder eine Gruppe von Office 365.

## <a name="methods"></a>Methoden

Die folgenden Methoden sind für Laufwerksressourcen verfügbar.


| Methode                                                    | Rückgabetyp                          | Beschreibung                                             |
|:----------------------------------------------------------|:-------------------------------------|:--------------------------------------------------------|
| [Standard-Laufwerk des Benutzers abrufen](../api/drive_get.md)           | [Laufwerk](drive.md)                    | Lesen Sie Eigenschaften der Laufwerkressource.                      |
| [Abrufen eines anderen Benutzers Laufwerk](../api/drive_get.md)           | [Laufwerk](drive.md)                    | Lesen Sie Eigenschaften der Laufwerkressource.                      |
| [Rufen Sie Stammordner für ein Laufwerk](../api/item_get.md)    | [driveItem](driveitem.md)            | Lesen Sie Eigenschaften des Stammordners des Laufwerks.        |
| [Auflisten von Elementen auf einem Laufwerk](../api/item_list_children.md)     | [DriveItem](driveitem.md) -Auflistung | Rufen Sie eine Auflistung der Item-Objekts.                           |
| [Liste der Änderungen in ein Laufwerk](../api/item_delta.md)           | [DriveItem](driveitem.md) -Auflistung | Nachverfolgen von Änderungen an Elementen in einem Laufwerk.                      |
| [Von Suchelementen in einem Laufwerk](../api/item_search.md)          | [DriveItem](driveitem.md) -Auflistung | Suchen Sie nach Elementen anhand von Schlüsselwörtern in ein Laufwerk.          |


## <a name="properties"></a>Eigenschaften

| Eigenschaft  | Typ                          | Beschreibung                                                                                          |
|:----------|:------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| id        | String                        | Der eindeutige Bezeichner des Laufwerks. Schreibgeschützt.                                                                                                           |
| driveType | String                        | Beschreibt die Art des Laufwerks durch diese Ressource dargestellt. Persönliche OneDrive-Laufwerken gibt zurück `personal`. OneDrive für Unternehmen zurückgegebenen `business`. Schreibgeschützt. |
| Besitzer     | [identitySet](identityset.md) | Das Benutzerkonto, das das Laufwerk besitzt.                                                                                                                    |
| Kontingent     | [Kontingent](quota.md)             | Informationen über das Laufwerk Speicherkontingent Speicherplatz.                                                                                                       |

## <a name="relationships"></a>Beziehungen

| Beziehung | Typ |Beschreibung |
|:--------|:---------------------------|:-------------------------------------------------------------------------|
| Items   | [Driveitem](driveitem.md) -Auflistung | Alle Elemente in das Laufwerk. Schreibgeschützt. NULL-Werte zulässt.                   |
| Stamm    | [driveitem](driveitem.md)            | Der Stammordner des Laufwerks. Schreibgeschützt.                                 |
| spezielle | [Driveitem](driveitem.md) -Auflistung | Auflistung der verfügbaren in OneDrive gemeinsamen Ordner. Schreibgeschützt. NULL-Werte zulässt. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "items", "root", "special" ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.drive"
}-->

```json
{
  "id": "string (identifier)",
  "driveType": "string",
  "owner": {"@odata.type": "microsoft.graph.identitySet"},
  "quota": {"@odata.type": "microsoft.graph.quota"},
  "root": {"@odata.type": "microsoft.graph.driveItem" },
  "items": [ {"@odata.type": "microsoft.graph.driveItem" }],
  "special": [ {"@odata.type": "microsoft.graph.driveItem" }]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "drive resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive"
}-->
