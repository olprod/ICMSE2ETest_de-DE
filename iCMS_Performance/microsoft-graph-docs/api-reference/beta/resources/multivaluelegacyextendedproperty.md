# <a name="multivaluelegacyextendedproperty-resource-type"></a>Ressourcentyp multiValueLegacyExtendedProperty

Eine erweiterte Eigenschaft, die eine Auflistung von Werten enthält.

Weitere Informationen zur Verwendung von Office 365 Daten Extensions oder erweiterten Eigenschaften und zur Angabe der erweiterter Eigenschaften finden Sie unter [Erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) .

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Bereitstellen](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | Eine Ressourceninstanz der unterstützten: [Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md), [Kalender](../resources/calendar.md), [wenden Sie sich an](../resources/contact.md), oder [ContactFolder](../resources/contactfolder.md), jedoch nicht der Gruppe [Bereitstellen](../resources/post.md). | Erstellen Sie eine **MultiValueLegacyExtendedProperty** in eine neue oder vorhandene Instanz einer unterstützten Ressource. |
|[Erhalten](../api/multivaluelegacyextendedproperty_get.md) |Eine Ressourceninstanz unterstützte ([Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md), [Kalender](../resources/calendar.md), [wenden Sie sich an](../resources/contact.md), [ContactFolder](../resources/contactfolder.md)oder Gruppe [Buchen](../resources/post.md)) erweitert mit einem [MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) Objekt verwendet werden. |Abrufen eine Instanz der Ressource mit einer erweiterten Eigenschaft mit `$expand`.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|Der Bezeichner der. Schreibgeschützt.|
|value|zeichenfolgenauflistung|Eine Auflistung von Eigenschaftswerten.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.multivaluelegacyextendedproperty"
}-->

```json
{
  "id": "string (identifier)",
  "value": ["string"]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "multiValueLegacyExtendedProperty resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->