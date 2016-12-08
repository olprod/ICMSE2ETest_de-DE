# <a name="identity-resource-type"></a>Identität Ressourcentyp

Die **Identität** Ressource stellt eine Identität eines _Akteur_dar. Für das Beispiel und Actor Benutzern, Gerät oder einer Anwendung werden können.

## <a name="properties"></a>Eigenschaften

| Eigenschaft    | Typ   | Beschreibung                                                                                                                                                                                                                                                                                                           |
|:------------|:-------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| displayName | String | Die Identität der Anzeigename. Beachten Sie, dass dies möglicherweise nicht immer verfügbar oder auf dem aktuellen Stand. Beispielsweise wenn ein Benutzer auf ihren Anzeigenamen ändert, die API kann in einer zukünftigen Antwort den neuen Wert anzeigen, jedoch der Elemente des Benutzers werden nicht angezeigt, [Suchen Sie nach Änderungen](../api/item_delta.md) Verwendung geändert hat |
| id          | String | Eindeutiger Bezeichner für die Identität.                                                                                                                                                                                                                                                                                   |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.identity"
}-->

```json
{
  "displayName": "string",
  "id": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "identity resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
