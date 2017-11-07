# <a name="automaticrepliessetting-resource-type"></a>Ressourcentyp automaticRepliesSetting

Konfigurationseinstellungen für den Absender einer eingehenden e-Mail mit einer Nachricht vom angemeldeten Benutzer automatisch zu benachrichtigen. Beispielsweise eine automatische Antwort zu benachrichtigen, dass der Benutzer angemeldet, auf e-Mails zu reagieren nicht verfügbar ist. 


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|externalAudience|String| Der Satz von außerhalb des angemeldeten Benutzers Unternehmens Benutzergruppe, die **ExternalReplyMessage**erhält, wenn **Status** `AlwaysEnabled` oder `Scheduled`. Mögliche Werte sind: `none`, `contactsOnly`, `all`.|
|externalReplyMessage|string|Die automatische Antwort an die angegebenen externen Benutzergruppe zu senden, wenn **Status** ist `AlwaysEnabled` oder `Scheduled`.|
|internalReplyMessage|string|Die automatische Antwort an die Zielgruppe interne Organisation des angemeldeten Benutzers, senden **Status** ist `AlwaysEnabled` oder `Scheduled`. |
|scheduledEndDateTime|[dateTimeTimeZone](datetimetimezone.md)|Datum und Uhrzeit, die automatische Antworten zu beenden, festgelegt sind Wenn der **Status** festgelegt ist, `Scheduled`. |
|scheduledStartDateTime|[dateTimeTimeZone](datetimetimezone.md)|Datum und Uhrzeit, die automatische Antworten beginnen soll, festgelegt sind, wenn der **Status** festgelegt ist, `Scheduled`.|
|status|String|Status der Konfigurationen für automatische Antworten. Mögliche Werte sind: `disabled`, `alwaysEnabled`, `scheduled`.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.automaticRepliesSetting"
}-->

```json
{
  "externalAudience": "String",
  "externalReplyMessage": "string",
  "internalReplyMessage": "string",
  "scheduledEndDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "scheduledStartDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "automaticRepliesSetting resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->