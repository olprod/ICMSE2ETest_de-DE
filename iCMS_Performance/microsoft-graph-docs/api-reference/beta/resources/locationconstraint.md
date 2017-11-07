# <a name="locationconstraint-resource-type"></a>LocationConstraint Ressourcentyp

Die Bedingungen, die von einem Client für den Ort einer Besprechung angegeben.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.locationconstraint"
}-->

```json
{
  "isRequired": true,
  "locations": [{"@odata.type": "microsoft.graph.location"}],
  "suggestLocation": true
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|isRequired|Boolean|Der Client fordert den Dienst in der Antwort enthalten einen Besprechungsort für die Besprechung.|
|Speicherorte|[Standort](location.md) -Auflistung|Eine oder mehrere Standorte, die die Clientanforderungen für die Besprechung.|
|suggestLocation|Boolean|Der Client fordert den Dienst zum Vorschlagen des Meeting-Speicherorte.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "locationConstraint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->