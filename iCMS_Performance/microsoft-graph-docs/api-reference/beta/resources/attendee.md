# <a name="attendee-resource-type"></a>ATTENDEE Ressourcentyp

Teilnehmer.
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|status|[ResponseStatus](responsestatus.md)|Die Antwort des Teilnehmers (keine, akzeptiert, abgelehnt, usw.) für das Ereignis und Datum-Zeit, die die Antwort gesendet wurde.|
|Typ|String|Der Teilnehmertyp: `Required`, `Optional`, `Resource`.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.attendee"
}-->

```json
{
  "status": {"@odata.type": "microsoft.graph.responseStatus"},
  "type": "String"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "attendee resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->