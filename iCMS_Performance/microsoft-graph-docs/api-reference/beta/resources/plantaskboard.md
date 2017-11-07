# <a name="plantaskboard-resource-type"></a>Ressourcentyp planTaskBoard

Die Ressource PlanTaskBoard stellt die Informationen verwendet, um einen Plan Pinnwand Vorgangsansicht ordnungsgemäß gerendert. Wie drei Pinnwand Vorgangsansichten für einen Plan für können müssen jeden [Plan](plan.md) drei PlanTaskBoard Objekte.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.plantaskboard"
}-->

```json
{
  "id": "string (identifier)",
  "type": "String (identifier)"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| Schreibgeschützt. ID des Plans. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst. |
|Typ|String| Schreibgeschützt. Verwendet, um den Typ der Vorgangsansicht Pinnwand festzulegen, in denen dieses Objekt zum Rendern verwendet wird. Mögliche Werte sind: `progress`, `assignedTo`, `bucket`.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von planTaskBoard](../api/plantaskboard_get.md) | [planTaskBoard](plantaskboard.md) |Lesen Sie Eigenschaften und Beziehungen des PlanTaskBoard-Objekts.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "planTaskBoard resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->