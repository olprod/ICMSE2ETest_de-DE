# <a name="attendeebase-resource-type"></a>Ressourcentyp attendeeBase

Der Typ des Teilnehmers.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.attendeeBase"
}-->

```json
{
  "type": "String"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Typ|String| Der Typ des Teilnehmers. Mögliche Werte sind: `Required`, `Optional`, `Resource`. Derzeit Wenn Teilnehmer einer Person ist, [FindMeetingTimes](../api/user_findmeetingtimes.md) immer berücksichtigt die Person ist, der die `Required` Typ.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "attendeeBase resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->