# <a name="reminder-resource-type"></a>Erinnerung Ressourcentyp



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|changeKey|String|Identifiziert die Version der Erinnerung. Jedes Mal die Erinnerung geändert wird, wird ebenfalls **ChangeKey** geändert. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen.|
|eventEndTime|[DateTimeTimeZone](datetimetimezone.md)|Datum, Uhrzeit und Zeitzone, die das Ereignis endet.|
|eventId|String|Die eindeutige ID des Ereignisses. Nur lesen.|
|eventLocation|[Speicherort](location.md)|Der Speicherort des Ereignisses.|
|eventStartTime|[DateTimeTimeZone](datetimetimezone.md)|Das Datum, Uhrzeit und Zeitzone, die das Ereignis beginnt.|
|eventSubject|String|Der Text der Betreffzeile des Ereignisses.|
|eventWebLink|String|Die URL, die das Ereignis in Outlook im Web zu öffnen.<br/><br/>Das Ereignis wird im Browser geöffnet, wenn Sie mit Ihrem Postfach über Outlook im Web angemeldet sind. Sie werden aufgefordert, anmelden, wenn Sie sich mit den Browser nicht bereits angemeldet sind.<br/><br/>Diese URL kann innerhalb eines iFrame aus zugegriffen werden.|
|reminderFireTime|[DateTimeTimeZone](datetimetimezone.md)|Das Datum, Uhrzeit und Zeitzone, die die Erinnerung festgelegt wird, erfolgt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.reminder"
}-->

```json
{
  "changeKey": "string",
  "eventEndTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventId": "string",
  "eventLocation": {"@odata.type": "microsoft.graph.location"},
  "eventStartTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventSubject": "string",
  "eventWebLink": "string",
  "reminderFireTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "reminder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->