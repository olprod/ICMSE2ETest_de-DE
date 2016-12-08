# <a name="worksheetprotectionoptions-resource-type"></a>Ressourcentyp WorksheetProtectionOptions

Stellt die Optionen in Arbeitsblattschutz dar.

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|allowAutoFilter|boolean|Stellt die Option automatische Filterfunktion mit Bearbeitungsrechten Arbeitsblatt-Schutz.|
|allowDeleteColumns|boolean|Stellt die Option Arbeitsblatt Protection Löschen von Spalten zu ermöglichen.|
|allowDeleteRows|boolean|Stellt die Option Arbeitsblatt Protection Löschen von Zeilen zu ermöglichen.|
|allowFormatCells|boolean|Stellt die Option Arbeitsblatt Protection Bearbeitungsrechten Zellen formatieren.|
|allowFormatColumns|boolean|Die Option Arbeitsblatt Protection Bearbeitungsrechten Formatieren von Spalten darstellt.|
|allowFormatRows|boolean|Stellt die Option Arbeitsblatt Protection Formatierung von Zeilen zu ermöglichen.|
|allowInsertColumns|boolean|Stellt die Option Arbeitsblatt Protection Bearbeitungsrechten Spalten einfügen.|
|allowInsertHyperlinks|boolean|Stellt die Option Arbeitsblatt Protection Bearbeitungsrechten Hyperlinks einfügen.|
|allowInsertRows|boolean|Stellt die Option Arbeitsblatt Protection Bearbeitungsrechten Zeilen einfügen.|
|allowPivotTables|boolean|Stellt die Option Arbeitsblatt Schutz mit Pivot-Tabelle-Funktion zu ermöglichen.|
|allowSort|boolean|Stellt die Option Arbeitsblatt Protection Bearbeitungsrechten Sort-Feature verwenden.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheetProtectionOptions"
}-->

```json
{
  "allowAutoFilter": true,
  "allowDeleteColumns": true,
  "allowDeleteRows": true,
  "allowFormatCells": true,
  "allowFormatColumns": true,
  "allowFormatRows": true,
  "allowInsertColumns": true,
  "allowInsertHyperlinks": true,
  "allowInsertRows": true,
  "allowPivotTables": true,
  "allowSort": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "WorksheetProtectionOptions resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->