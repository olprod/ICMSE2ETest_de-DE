# <a name="worksheet-resource-type"></a>Typ des Arbeitsblatts Ressource

Ein Excel-Arbeitsblatt ist ein Raster von Zellen. Sie können Daten, Tabellen, Diagramme enthalten.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erste Arbeitsblatt](../api/worksheet_get.md) | [Arbeitsblatt](worksheet.md) |Lesen Sie Eigenschaften und Beziehungen des Worksheet-Objekts.|
|[Erstellen eines Diagramms](../api/worksheet_post_charts.md) |[Diagramm](chart.md)| Erstellen eines neuen Diagramms durch das Veröffentlichen in Charts-Auflistung.|
|[Liste Diagramme](../api/worksheet_list_charts.md) |[Diagramm](chart.md) -Auflistung| Get-Auflistung ein Chart-Objekts.|
|[Tabelle erstellen](../api/worksheet_post_tables.md) |[Tabelle](table.md)| Erstellen einer neuen Tabelle durch die Veröffentlichung auf die Tables-Auflistung.|
|[Liste Tabellen](../api/worksheet_list_tables.md) |[Tabelle](table.md) -Auflistung| Rufen Sie eine Auflistung der Tabelle-Objekts.|
|[Update](../api/worksheet_update.md) | [Arbeitsblatt](worksheet.md)   |Worksheet-Objekt zu aktualisieren. |
|[Zelle](../api/worksheet_cell.md)|[Bereich](range.md)|Ruft das Range-Objekt, die einzelne Zelle basierend auf Zeile und Spalte Zahlen enthält. Die Zelle kann außerhalb des dem übergeordneten Bereich, solange es bleibt innerhalb des Rasters Arbeitsblatt ist.|
|[Bereich](../api/worksheet_range.md)|[Bereich](range.md)|Ruft den Namen oder die Adresse angegeben Range-Objekt ab.|
|[UsedRange](../api/worksheet_usedrange.md)|[Bereich](range.md)|Der verwendete Bereich wird der kleinste Bereich, der alle Zellen umfasst, deren Wert oder Formatierung zugewiesen werden. Wenn das Arbeitsblatt leer ist, gibt diese Funktion die linke obere Zelle zurück.|
|[Löschen](../api/worksheet_delete.md)|Keine|Das Arbeitsblatt aus der Arbeitsmappe gelöscht.|
|[Liste](../api/worksheet_list.md) | [Arbeitsblatt](worksheet.md) -Auflistung |Arbeitsblatt-Auflistung-Objekts abrufen. |
|[Fügen Sie hinzu](../api/worksheetcollection_add.md)|[Arbeitsblatt](worksheet.md)|Fügt ein neues Arbeitsblatt in der Arbeitsmappe. Das Arbeitsblatt wird am Ende des vorhandenen Arbeitsblätter hinzugefügt. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|Gibt einen Wert an, der im Arbeitsblatt in einer bestimmten Arbeitsmappe eindeutig identifiziert. Der Wert des Bezeichners bleibt gleich, auch wenn das Arbeitsblatt umbenannt oder verschoben wird. Schreibgeschützt.|
|name|string|Der Anzeigename des Arbeitsblatts ein.|
|position|int|Die nullbasierte Position des Arbeitsblatts in der Arbeitsmappe.|
|visibility|string|Die Sichtbarkeit des Arbeitsblatts ein. Mögliche Werte sind: `Visible`, `Hidden`, `VeryHidden`.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Diagramme|[Chart](chart.md) -Auflistung|Gibt die Auflistung der Diagramme, die Teil des Arbeitsblatts sind zurück. Schreibgeschützt.|
|Schutz|[WorksheetProtection](worksheetprotection.md)|Gibt Blatt Protection-Objekt für ein Arbeitsblatt. Schreibgeschützt.|
|Tabellen|[Tabelle](table.md) -Auflistung|Die Auflistung von Tabellen, die Teil des Arbeitsblatts sind. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheet"
}-->

```json
{
  "id": "string",
  "name": "string",
  "position": 1024,
  "visibility": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Worksheet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->