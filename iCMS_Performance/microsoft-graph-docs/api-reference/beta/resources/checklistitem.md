# <a name="checklistitem-resource-type"></a>Ressourcentyp checklistItem

Die Ressource ChecklistItem stellt ein Element in der Prüfliste eines Vorgangs dar. Die Checkliste für einen Vorgang wird durch die [ChecklistItemCollection](checklistitemcollection.md)dargestellt.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.checklistitem"
}-->

```json
{
  "isChecked": true,
  "lastModifiedBy": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "orderHint": "string",
  "title": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|isChecked|Boolean| Ist der Wert `true` Wenn das Element aktiviert ist und `false` anders. |
|lastModifiedBy|String| Schreibgeschützt. Benutzer-Id mit dem dies geändert wird. |
|lastModifiedDateTime|DateTimeOffset| Schreibgeschützt. Datum und Uhrzeit, an dem dieses geändert wird. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|orderHint|String| Verwendet, um die relative Reihenfolge der Elemente in der Prüfliste festzulegen. Drei Elemente in der Reihenfolge der berücksichtigen: `'O'`, `'P'`, `'Q'`. So verschieben Sie `'P'` an den Anfang der Prüfliste, legen Sie dessen `'orderHint'` zu kleiner als der von `'O'`. Vergleich wird ein ordinal Zeichenfolgenvergleich. |
|title|String| Titel des Elements. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "checklistItem resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->