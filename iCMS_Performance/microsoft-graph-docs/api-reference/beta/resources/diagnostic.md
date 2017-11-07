# <a name="diagnostic-resource-type"></a>Diagnose Ressourcentyp

Informationen zu einer Fehlermeldung oder einer Warnung für eine OneNote-Operation.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.diagnostic"
}-->

```json
{
  "message": "string",
  "url": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Nachricht|String|Die Nachricht, beschreibt die Bedingung, die den Fehler oder eine Warnung ausgelöst.|
|URL|String|Die Verknüpfung mit der Dokumentation für dieses Problem.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "diagnostic resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->