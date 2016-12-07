# <a name="workbook-resource-type"></a>Workbook resource type

Die Arbeitsmappe ist das Objekt auf oberster Ebene , das dazugehörige Arbeitsmappenobjekte wie z. B. Arbeitsblätter, Tabellen, Bereiche usw. enthält.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[List names](../api/workbook_list_names.md) |[NamedItem](nameditem.md) collection| Get a NamedItem object collection.|
|[Create Table](../api/workbook_post_tables.md) |[Table](table.md)| Create a new Table by posting to the tables collection.|
|[List tables](../api/workbook_list_tables.md) |[Table](table.md) collection| Get a Table object collection.|
|[List worksheets](../api/workbook_list_worksheets.md) |[Worksheet](worksheet.md) collection| Get a Worksheet object collection.|

## <a name="properties"></a>Eigenschaften
Keine

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Namen|[NamedItem](nameditem.md) collection|Stellt eine Auflistung der benannten Elemente des Arbeitsmappenbereichs dar (benannte Bereiche und Konstanten). Schreibgeschützt.|
|Tabellen|[Table](table.md) collection|Stellt eine Auflistung der mit der Arbeitsmappe verknüpften Tabellen dar. Schreibgeschützt.|
|Worksheets|[Worksheet](worksheet.md) collection|Stellt eine Auflistung der mit der Arbeitsmappe verknüpften Arbeitsblätter dar. Schreibgeschützt.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Workbook resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->