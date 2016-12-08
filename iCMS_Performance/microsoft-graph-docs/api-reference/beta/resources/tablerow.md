# <a name="tablerow-resource-type"></a>TableRow-Ressourcentyp

Eine Zeile in einer Tabelle darstellt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[TableRow abrufen](../api/tablerow_get.md) | [TableRow](tablerow.md) |Lesen Sie Eigenschaften und Beziehungen TableRow-Objekts.|
|[Update](../api/tablerow_update.md) | [TableRow](tablerow.md)  |TableRow-Objekt zu aktualisieren. |
|[Bereich](../api/tablerow_range.md)|[Bereich](range.md)|Gibt das Range-Objekt, das die gesamte Zeile zugeordnet.|
|[Löschen](../api/tablerow_delete.md)|Keine|Die Zeile aus der Tabelle gelöscht.|
|[Liste](../api/tablerow_list.md) | [TableRow](tablerow.md) -Auflistung |Rufen Sie die Auflistung von TableRow-Objekts. |
|[Itemat](../api/tablerowcollection_itemat.md)|[TableRow](tablerow.md)|Ruft eine Zeile basierend auf seine Position in der Auflistung ab.|
|[Fügen Sie hinzu](../api/tablerowcollection_add.md)|[TableRow](tablerow.md)|Fügt eine neue Zeile der Tabelle an.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Index|int|Gibt die Indexnummer der Zeile in der Tabelle der Rows-Auflistung zurück. 0 (null) indiziert. Schreibgeschützt.|
|values|json|Die unformatierten Werte des angegebenen Bereichs darstellt. Die zurückgegebenen Daten konnte vom Typ String, Nummer oder ein boolescher Wert sein. Zelle, die Fehler enthalten, gibt die Fehlerzeichenfolge zurück.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableRow"
}-->

```json
{
  "index": 1024,
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableRow resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->