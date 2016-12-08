# <a name="range-resource-type"></a>Bereich Ressourcentyp

Bereich stellt einen Satz von einer oder mehreren zusammenhängenden Zellen wie eine Zelle, eine Zeile, eine Spalte Block von Zellen usw..


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von Bereichen](../api/range_get.md) | [Bereich](range.md) |Eigenschaften lesen und Beziehungen des Range-Objekts.|
|[Update](../api/range_update.md) | [Bereich](range.md)   |Update Range-Objekt. |
|["BoundingRect"](../api/range_boundingrect.md)|[Bereich](range.md)|Ruft die kleinste Range-Objekts, die die angegebenen Bereichen umfasst. Beispielsweise ist der GetBoundingRect von "B2:C5" und "D10:E15" "B2:E16".|
|[Zelle](../api/range_cell.md)|[Bereich](range.md)|Ruft das Range-Objekt, die einzelne Zelle basierend auf Zeile und Spalte Zahlen enthält. Die Zelle kann außerhalb des dem übergeordneten Bereich, solange es bleibt innerhalb des Rasters Arbeitsblatt ist. Die zurückgegebene Zelle ist relativ zu der linken oberen Zelle des Bereichs befindet.|
|[Spalte](../api/range_column.md)|[Bereich](range.md)|Dient zum Abrufen einer Spalteninhalts im Bereich enthalten.|
|[EntireColumn](../api/range_entirecolumn.md)|[Bereich](range.md)|Ruft ein Objekt, das die gesamte Spalte des Bereichs darstellt.|
|[EntireRow](../api/range_entirerow.md)|[Bereich](range.md)|Ruft ein Objekt, das die gesamte Zeile des Bereichs darstellt.|
|[Schnittmenge](../api/range_intersection.md)|[Bereich](range.md)|Ruft das Range-Objekt, das die rechteckige Schnittmenge von den angegebenen Bereichen darstellt.|
|[Lastcell](../api/range_lastcell.md)|[Bereich](range.md)|Ruft die letzte Zelle innerhalb des Bereichs. Die letzte Zelle der "B2:D5" ist beispielsweise "D5".|
|[LastColumn](../api/range_lastcolumn.md)|[Bereich](range.md)|Ruft die letzte Spalte innerhalb des Bereichs. Die letzte Spalte des "B2:D5" ist beispielsweise "D2:D5".|
|[LastRow](../api/range_lastrow.md)|[Bereich](range.md)|Ruft die letzte Zeile innerhalb des Bereichs. Beispielsweise ist die letzte Zeile der "B2:D5", "B5:D5".|
|[Offsetrange](../api/range_offsetrange.md)|[Bereich](range.md)|Ruft ein Objekt, das einen Bereich darstellt, der gegenüber dem angegebenen Bereich versetzt ist. Die Dimension der zurückgegebene Bereich entspricht diesem Bereich. Wenn der resultierende Bereich außerhalb des Arbeitsblatts Raster erzwungen wird, wird eine Ausnahme ausgelöst.|
|[Zeile](../api/range_row.md)|[Bereich](range.md)|Dient zum Abrufen einer Zeile im Bereich enthalten.|
|[UsedRange](../api/range_usedrange.md)|[Bereich](range.md)|Gibt den verwendeten Bereich des angegebenen Range-Objekts zurück.|
|[Löschen](../api/range_clear.md)|Keine|Clear Wertebereiche, Format, Füllung, Rahmen, etc.|
|[Löschen](../api/range_delete.md)|Keine|Löscht die Zellen im Bereich verknüpft ist.|
|[Einfügen](../api/range_insert.md)|[Bereich](range.md)|Fügt eine Zelle oder einen Zellbereich in das Arbeitsblatt an der Stelle in diesem Bereich, und verschiebt die anderen Zellen entsprechend. Gibt ein neues Range-Objekt an die jetzt Leerzeichen.|
|[Zusammenführen](../api/range_merge.md)|Keine|Die Zellen des Bereichs in einem Bereich in dem Arbeitsblatt zusammenführen.|
|[UnMerge](../api/range_unmerge.md)|Keine|Heben Sie die Verbindung Bereich in einzelne Zellen.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|address|string|Stellt den Bereichsbezug in der A1-Schreibweise. Adresswert enthält die Blattreferenz (z. B. Sheet1! A1: B4). Schreibgeschützt.|
|addressLocal|string|Bereichsbezug für den angegebenen Bereich in der Sprache des Benutzers darstellt. Schreibgeschützt.|
|cellCount|int|Anzahl der Zellen im Bereich. Schreibgeschützt.|
|columnCount|int|Die Gesamtzahl der Spalten im Bereich darstellt. Schreibgeschützt.|
|columnHidden|boolean|Darstellt, wenn alle Spalten des aktuellen Bereichs ausgeblendet sind.|
|columnIndex|int|Die Spaltennummer der ersten Zelle im Bereich darstellt. 0 (null) indiziert. Schreibgeschützt.|
|formulas|json|Stellt die Formel in A1-Schreibweise.|
|formulasLocal|json|Die Formel in A1-Schreibweise, Sprache und Gebietsschema Formatieren von Zahlen des Benutzers darstellt.  Beispielsweise würde die englische Formel "= SUM (A1, 1,5)" werden "= SUMME(A1; 1,5) "auf Deutsch.|
|formulasR1C1|json|Stellt die Formel in Z1S1-Schreibweise.|
|ausgeblendet|boolean|Stellt dar, wenn alle Zellen des aktuellen Bereichs ausgeblendet sind. Schreibgeschützt.|
|numberFormat|json|Excel Zahlenformat für die angegebene Zelle darstellt.|
|rowCount|int|Gibt die Gesamtzahl der Zeilen im Bereich zurück. Schreibgeschützt.|
|rowHidden|boolean|Stellt dar, ob alle Zeilen des aktuellen Bereichs ausgeblendet werden.|
|rowIndex|int|Gibt die Zeilennummer der ersten Zelle im Bereich zurück. 0 (null) indiziert. Schreibgeschützt.|
|text|json|Textwerte des angegebenen Bereichs. Der Textwert hängt nicht die Breite der Zelle. Die # Anmelde Ersetzung, die in Excel-Benutzeroberfläche geschieht wirkt sich nicht auf den von der API zurückgegebenen Textwert aus. Schreibgeschützt.|
|Werttypen|string|Stellt den Typ der Daten, die jeder Zelle. Possible values are: `Unknown`, `Empty`, `String`, `Integer`, `Double`, `Boolean`, `Error`. Schreibgeschützt.|
|values|json|Die unformatierten Werte des angegebenen Bereichs darstellt. Die zurückgegebenen Daten konnte vom Typ String, Nummer oder ein boolescher Wert sein. Zelle, die Fehler enthalten, gibt die Fehlerzeichenfolge zurück.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Format|[RangeFormat](rangeformat.md)|Gibt ein Formatobjekt, das den Bereich Schriftart, Füllung, Rahmen, Ausrichtung und andere Eigenschaften zurück. Schreibgeschützt.|
|Sortieren|[RangeSort](rangesort.md)|Das Arbeitsblatt, das den aktuellen Bereich enthält. Schreibgeschützt.|
|worksheet|[Arbeitsblatt](worksheet.md)|Das Arbeitsblatt, das den aktuellen Bereich enthält. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.range"
}-->

```json
{
  "address": "string",
  "addressLocal": "string",
  "cellCount": 1024,
  "columnCount": 1024,
  "columnHidden": true,
  "columnIndex": 1024,
  "formulas": "json",
  "formulasLocal": "json",
  "formulasR1C1": "json",
  "hidden": true,
  "numberFormat": "json",
  "rowCount": 1024,
  "rowHidden": true,
  "rowIndex": 1024,
  "text": "json",
  "valueTypes": "string",
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Range resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->