# <a name="tablesort-resource-type"></a>Ressourcentyp TableSort

Verwaltet Sortierung Vorgänge im Table-Objekte.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von TableSort](../api/tablesort_get.md) | [TableSort](tablesort.md) |Lesen Sie Eigenschaften und Beziehungen des TableSort-Objekts.|
|[Anwenden](../api/tablesort_apply.md)|Keine|Führen Sie einen Sortiervorgang.|
|[Löschen](../api/tablesort_clear.md)|Keine|Löscht die Sortierung, die derzeit in der Tabelle ist. Während dies die Sortierung der Tabelle nicht geändert, den Status der Kopfzeile Schaltflächen gelöscht.|
|[Erneutes Anwenden](../api/tablesort_reapply.md)|Keine|Wendet die aktuellen Sortierparameter auf die Tabelle erstellen.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|matchCase|boolean|Stellt dar, ob die Groß-/Kleinschreibung die letzte Sortieren der Tabelle betroffen. Schreibgeschützt.|
|Methode|string|Stellt Chinesisches Zeichen Sortierung Methode zuletzt verwendet, um die Tabelle zu sortieren. Mögliche Werte sind: `PinYin`, `StrokeCount`. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Felder|[SortField](sortfield.md)|Stellt die aktuellen Bedingungen verwendet, um die Tabelle zuletzt zu sortieren. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableSort"
}-->

```json
{
  "matchCase": true,
  "method": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableSort resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->