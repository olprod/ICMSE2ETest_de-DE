# <a name="inferenceclassification-resource-type"></a>Ressourcentyp inferenceClassification

Klassifizierung von einem Benutzer Nachrichten an den Fokus auf diesen zu aktivieren, die dem Benutzer mehr relevant ist oder wichtig sind. 

Weitere Informationen finden Sie unter [Verwalten von Experten Posteingang](manage_focused_inbox.md).


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erstellen von inferenceClassificationOverride](../api/inferenceclassification_post_overrides.md) |[inferenceClassificationOverride](inferenceclassificationoverride.md)| Erstellen einer Außerkraftsetzung für eine SMTP-Adresse identifizierten Absender. Nachrichten von diesem SMTP-Adresse konsistent eingestuft wird wie in die Außerkraftsetzung angegeben.|
|[Liste hat Vorrang vor](../api/inferenceclassification_list_overrides.md) |[InferenceClassificationOverride](inferenceclassificationoverride.md) -Auflistung| Rufen Sie die überschreibt, die ein Benutzer zum Klassifizieren von Nachrichten von bestimmten Absendern immer auf bestimmte Weise eingerichtet hat.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string| Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|überschreibt|[InferenceClassificationOverride](inferenceclassificationoverride.md) -Auflistung| Eine Reihe von Außerkraftsetzungen für einen Benutzer zum Klassifizieren von Nachrichten von bestimmten Absendern auf bestimmte Weise immer: `focused`, oder `other`. Schreibgeschützt. NULL-Werte zulässt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.inferenceClassification"
}-->

```json
{
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "inferenceClassification resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->