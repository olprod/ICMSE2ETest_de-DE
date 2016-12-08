# <a name="formatprotection-resource-type"></a>Ressourcentyp FormatProtection

Den Format-Schutz, der ein Range-Objekt darstellt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von FormatProtection](../api/formatprotection_get.md) | [FormatProtection](formatprotection.md) |Lesen Sie Eigenschaften und Beziehungen des FormatProtection-Objekts.|
|[Update](../api/formatprotection_update.md) | [FormatProtection](formatprotection.md)  |Update FormatProtection-Objekt. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|formulaHidden|boolean|Gibt an, ob Excel die Formel für die Zellen im Bereich werden ausgeblendet. Ein null-Wert gibt an, dass der gesamte Bereich uniform Formel ausgeblendete Einstellung hat.|
|gesperrt|boolean|Gibt an, ob Excel die Zellen in das Objekt gesperrt. Ein null-Wert gibt an, dass der gesamte Bereich uniform Sperrung nicht.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.formatProtection"
}-->

```json
{
  "formulaHidden": true,
  "locked": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "FormatProtection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->