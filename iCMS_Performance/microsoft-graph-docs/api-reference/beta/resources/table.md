# <a name="table-resource-type"></a>Tabelle Ressourcentyp

Stellt eine Excel-Tabelle.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[-Tabelle](../api/table_get.md) | [Tabelle](table.md) |Eigenschaften lesen und Beziehungen des Table-Objekts.|
|[TableColumn erstellen](../api/table_post_columns.md) |[TableColumn-Element](tablecolumn.md)| Erstellen Sie eine neue TableColumn, indem Sie das Veröffentlichen in der Columns-Auflistung.|
|[Listenspalten](../api/table_list_columns.md) |[TableColumn](tablecolumn.md) -Auflistung| Rufen Sie eine Auflistung der TableColumn-Objekts.|
|[TableRow erstellen](../api/table_post_rows.md) |[TableRow](tablerow.md)| Erstellen Sie eine neue TableRow, indem Sie das Veröffentlichen in der Rows-Auflistung.|
|[Listenzeilen](../api/table_list_rows.md) |[TableRow](tablerow.md) -Auflistung| -Auflistung ein TableRow-Objekts abrufen.|
|[Update](../api/table_update.md) | [Tabelle](table.md)   |Update Table-Objekt. |
|[DataBodyRange](../api/table_databodyrange.md)|[Bereich](range.md)|Ruft das Range-Objekt zugeordneten Daten Hauptteil der Tabelle ab.|
|[HeaderRowRange](../api/table_headerrowrange.md)|[Bereich](range.md)|Ruft die Kopfzeile der Tabelle zugeordnet Bereichsobjekt ab.|
|[Bereich](../api/table_range.md)|[Bereich](range.md)|Ruft das Range-Objekt zugeordneten die gesamte Tabelle.|
|[Totalrowrange](../api/table_totalrowrange.md)|[Bereich](range.md)|Ruft die Ergebniszeile der Tabelle zugeordnet Bereichsobjekt ab.|
|[Clearfilters](../api/table_clearfilters.md)|Keine|Löscht alle Filter, die derzeit in der Tabelle angewendet.|
|[Converttorange](../api/table_converttorange.md)|[Bereich](range.md)|Die Tabelle konvertiert in einem normalen Zellbereich. Alle Daten werden beibehalten.|
|[Löschen](../api/table_delete.md)|Keine|Die Tabelle wird gelöscht.|
|[Reapplyfilters](../api/table_reapplyfilters.md)|Keine|Wendet alle Filter derzeit in der Tabelle an.|
|[Liste](../api/table_list.md) | [Tabelle](table.md) -Auflistung |Tabelle-Auflistung-Objekts abrufen. |
|[Fügen Sie hinzu](../api/tablecollection_add.md)|[Tabelle](table.md)|Erstellen Sie eine neue Tabelle. Die Bereich Quelladresse bestimmt das Arbeitsblatt, unter dem die Tabelle hinzugefügt werden. Falls die Tabelle (z. B., da die Adresse ungültig ist oder die Tabelle mit einer anderen Tabelle überlappen würde) hinzugefügt werden kann, wird ein Fehler ausgelöst.|



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|int|Gibt einen Wert an, der die Tabelle in einer bestimmten Arbeitsmappe eindeutig identifiziert. Der Wert des Bezeichners bleibt gleich, auch wenn die Tabelle umbenannt wird. Schreibgeschützt.|
|name|string|Name der Tabelle.|
|showHeaders|boolean|Gibt an, ob die Kopfzeile angezeigt wird. Dieser Wert kann zum Anzeigen oder entfernen die Kopfzeile festgelegt werden.|
|showTotals|boolean|Gibt an, ob die Ergebniszeile sichtbar ist. Dieser Wert kann ein-oder entfernen die gesamte Zeile festgelegt werden.|
|style|string|Konstanter Wert, der die Tabellenformatvorlage repräsentiert. Mögliche Werte sind: TableStyleLight1 bis TableStyleLight21 TableStyleMedium1 bis TableStyleMedium28 TableStyleStyleDark1 bis TableStyleStyleDark11. Eine benutzerdefinierte benutzerdefinierte Formatvorlage in der Arbeitsmappe vorhanden kann auch angegeben werden.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|columns|[TableColumn](tablecolumn.md) -Auflistung|Stellt eine Auflistung aller Spalten in der Tabelle dar. Schreibgeschützt.|
|Rows|[TableRow](tablerow.md) -Auflistung|Stellt eine Auflistung aller Zeilen in der Tabelle dar. Schreibgeschützt.|
|Sortieren|[TableSort](tablesort.md)|Stellt die Sortierung für die Tabelle. Schreibgeschützt.|
|worksheet|[Arbeitsblatt](worksheet.md)|Das Arbeitsblatt mit der aktuellen Tabelle. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.table"
}-->

```json
{
  "id": 1024,
  "name": "string",
  "showHeaders": true,
  "showTotals": true,
  "style": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Table resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->