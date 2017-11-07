# <a name="singlevaluelegacyextendedproperty-resource-type"></a>Ressourcentyp singleValueLegacyExtendedProperty

Eine erweiterte Eigenschaft, die einen einzelnen Wert enthält. 

Weitere Informationen zur Verwendung von Office 365 Daten Extensions oder erweiterten Eigenschaften und zur Angabe der erweiterter Eigenschaften finden Sie unter [Erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) . 


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Bereitstellen](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) | Eine Ressourceninstanz der unterstützten: [Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md), [Kalender](../resources/calendar.md), [wenden Sie sich an](../resources/contact.md), oder [ContactFolder](../resources/contactfolder.md), jedoch nicht der Gruppe [Bereitstellen](../resources/post.md). | Eine **SingleValueLegacyExtendedProperty** in einem neuen oder vorhandenen Instanz einer unterstützten Ressource zu erstellen. |
|[Erhalten](../api/singlevaluelegacyextendedproperty_get.md) |Eine oder eine Auflistung von unterstützten Ressourceninstanz ([Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md), [Kalender](../resources/calendar.md), [wenden Sie sich an](../resources/contact.md), [ContactFolder](../resources/contactfolder.md)oder Gruppe [Buchen](../resources/post.md)) oder eine solche Instanz erweitert mit einem [SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Objekt. |Abrufen eine Instanz der Ressource mit einer erweiterten Eigenschaft mit `$expand` oder `$filter`.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|Der Bezeichner der. Schreibgeschützt.|
|value|string|Der Wert einer Eigenschaft.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.singlevaluelegacyextendedproperty"
}-->

```json
{
  "id": "string (identifier)",
  "value": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "singleValueLegacyExtendedProperty resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->