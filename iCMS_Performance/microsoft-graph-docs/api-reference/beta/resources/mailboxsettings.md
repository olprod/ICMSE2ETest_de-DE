# <a name="mailboxsettings-resource-type"></a>Ressourcentyp mailboxSettings

Einstellungen für das primäre Postfach des angemeldeten Benutzers.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|automaticRepliesSetting|[automaticRepliesSetting](automaticrepliessetting.md)|Konfigurationseinstellungen für den Absender einer eingehenden e-Mail mit einer Nachricht vom angemeldeten Benutzer automatisch zu benachrichtigen.|
|language|[localeInfo](localeinfo.md)|Die Gebietsschemainformationen für den Benutzer, einschließlich der bevorzugten Sprache und Land/Region.|
|Zeitzone|string|Die Standardzeitzone für das Postfach des Benutzers.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.mailboxSettings"
}-->

```json
{
  "automaticRepliesSetting": {"@odata.type": "microsoft.graph.automaticRepliesSetting"},
  "language": {"@odata.type": "microsoft.graph.localeInfo"},
  "timeZone": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "mailboxSettings resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->