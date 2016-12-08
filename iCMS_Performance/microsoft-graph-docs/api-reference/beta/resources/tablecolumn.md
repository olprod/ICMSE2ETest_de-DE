# <a name="tablecolumn-resource-type"></a>TableColumn Ressourcentyp

Stellt eine Spalte in einer Tabelle dar.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[TableColumn abrufen](../api/tablecolumn_get.md) | [TableColumn-Element](tablecolumn.md) |Lesen Sie Eigenschaften und Beziehungen TableColumn-Objekts.|
|[Update](../api/tablecolumn_update.md) | [TableColumn-Element](tablecolumn.md) |TableColumn-Objekt zu aktualisieren. |
|[DataBodyRange](../api/tablecolumn_databodyrange.md)|[Bereich](range.md)|Ruft das Range-Objekt zugeordneten Daten Hauptteil der Spalte ab.|
|[HeaderRowRange](../api/tablecolumn_headerrowrange.md)|[Bereich](range.md)|Ruft das Range-Objekt, das die Kopfzeile der Spalte zugeordnet.|
|[Bereich](../api/tablecolumn_range.md)|[Bereich](range.md)|Ruft das Range-Objekt, das die gesamte Spalte zugeordnet.|
|[Totalrowrange](../api/tablecolumn_totalrowrange.md)|[Bereich](range.md)|Ruft die Ergebniszeile der Spalte zugeordnet Range-Objekts ab.|
|[Löschen](../api/tablecolumn_delete.md)|Keine|Die Spalte in der Tabelle gelöscht.|
|[Liste](../api/tablecolumn_list.md) | [TableColumn](tablecolumn.md) -Auflistung |Rufen Sie die Auflistung von TableColumn-Objekts. |
|[Itemat](../api/tablecolumncollection_itemat.md)|[TableColumn-Element](tablecolumn.md)|Ruft eine Spalte basierend auf seine Position in der Auflistung ab.|
|[Fügen Sie hinzu](../api/tablecolumncollection_add.md)|[TableColumn-Element](tablecolumn.md)|Der Tabelle hinzugefügt eine neue Spalte.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|int|Gibt einen eindeutigen Schlüssel, der die Spalte in der Tabelle identifiziert. Schreibgeschützt.|
|Index|int|Gibt die Indexnummer der Spalte in der Tabelle der Columns-Auflistung zurück. 0 (null) indiziert. Schreibgeschützt.|
|name|string|Gibt den Namen der Tabellenspalte zurück. Schreibgeschützt.|
|values|json|Die unformatierten Werte des angegebenen Bereichs darstellt. Die zurückgegebenen Daten konnte vom Typ String, Nummer oder ein boolescher Wert sein. Zelle, die Fehler enthalten, gibt die Fehlerzeichenfolge zurück.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|filter|[Filter](filter.md)|Abrufen des Filters auf die Spalte angewendet. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableColumn"
}-->

```json
{
  "id": 1024,
  "index": 1024,
  "name": "string",
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableColumn resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->