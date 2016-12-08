# <a name="rangeformat-resource-type"></a>Ressourcentyp RangeFormat

Ein encapsulating der Bereich Schriftart, Füllung, Rahmen, Ausrichtung und andere Eigenschaften Formatobjekt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von RangeFormat](../api/rangeformat_get.md) | [RangeFormat](rangeformat.md) |Lesen Sie Eigenschaften und Beziehungen RangeFormat-Objekts.|
|[RangeBorder erstellen](../api/rangeformat_post_borders.md) |[RangeBorder](rangeborder.md)| Erstellen Sie eine neue RangeBorder, indem Sie das Veröffentlichen in der Borders-Auflistung.|
|[Listenrahmen](../api/rangeformat_list_borders.md) |[RangeBorder](rangeborder.md) -Auflistung| Rufen Sie eine Auflistung der RangeBorder-Objekts.|
|[Update](../api/rangeformat_update.md) | [RangeFormat](rangeformat.md) |Aktualisieren Sie RangeFormat-Objekts. |
|[Autofitcolumns](../api/rangeformat_autofitcolumns.md)|Keine|Die Breite der Spalten des aktuellen Bereichs optimal angepasst, basierend auf den aktuellen Daten in den Spalten.|
|[Autofitrows](../api/rangeformat_autofitrows.md)|Keine|Ändert die Höhe der Zeilen des aktuellen Bereichs optimal angepasst, basierend auf den aktuellen Daten in den Spalten.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|columnWidth|double|Dient zum Abrufen oder Festlegen der Breite des alle Spalten innerhalb des Bereichs. Wenn die Spaltenbreite nicht uniform sind, wird Null zurückgegeben.|
|horizontalAlignment|string|Die horizontale Ausrichtung für das angegebene Objekt darstellt. Possible values are: `General`, `Left`, `Center`, `Right`, `Fill`, `Justify`, `CenterAcrossSelection`, `Distributed`.|
|rowHeight|double|Ruft ab oder legt die Höhe aller Zeilen im Bereich fest. Wenn die Zeilenhöhe nicht uniform sind, wird Null zurückgegeben.|
|verticalAlignment|string|Die vertikale Ausrichtung für das angegebene Objekt darstellt. Mögliche Werte sind: `Top`, `Center`, `Bottom`, `Justify`, `Distributed`.|
|wrapText|boolean|Gibt an, ob den Text im Objekt Excel umbrochen wird. Ein null-Wert gibt an, dass der gesamte Bereich uniform Wrap-Einstellung hat|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Borders|[RangeBorder](rangeborder.md) -Auflistung|Auflistung von Border-Objekten, die für den gesamten ausgewählten Bereich gelten schreibgeschützt.|
|fill|[RangeFill](rangefill.md)|Gibt das Fill-Objekt auf den gesamten Bereich definiert sind. Schreibgeschützt.|
|font|[RangeFont](rangefont.md)|Gibt das Font-Objekt, das auf den gesamten ausgewählten Bereich definiert sind schreibgeschützt.|
|Schutz|[FormatProtection](formatprotection.md)|Gibt das Format Protection-Objekt für einen Bereich zurück. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeFormat"
}-->

```json
{
  "columnWidth": 1024,
  "horizontalAlignment": "string",
  "rowHeight": 1024,
  "verticalAlignment": "string",
  "wrapText": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "RangeFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->