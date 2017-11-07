# <a name="inferenceclassificationoverride-resource-type"></a>Ressourcentyp inferenceClassificationOverride

Stellt die Außerkraftsetzung für eingehende von einem bestimmten Absender wie Nachrichten des Benutzers sollte immer als eingestuft werden.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Update](../api/inferenceclassificationoverride_update.md) | [inferenceClassificationOverride](inferenceclassificationoverride.md) |Ändern einer Außerkraftsetzung als angegebene Feld **ClassifyAs** . |
|[Löschen](../api/inferenceclassificationoverride_delete.md) | Keine |Löschen Sie eine durch seine ID angegebenen Überschreibung |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|classifyAs|string| Gibt an, wie eingehende-Nachrichten von einer bestimmten Absender sollte stets als klassifiziert werden. Mögliche Werte sind: `focused`, `other`.|
|id|string| Der eindeutige Bezeichner, der die Außerkraftsetzung. Schreibgeschützt.|
|senderEmailAddress|[emailAddress](emailaddress.md)|Die e-Mail-Adressinformationen des Absenders für den die Überschreibung erstellt wird.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.inferenceClassificationOverride"
}-->

```json
{
  "classifyAs": "string",
  "id": "string (identifier)",
  "senderEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "inferenceClassificationOverride resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->