# <a name="application-resource-type"></a>Anwendung Ressourcentyp

Stellt die Excel-Anwendung, die die Arbeitsmappe verwaltet.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen der Anwendung](../api/excelapplication_get.md) | [Anwendung](application.md) |Lesen Sie Eigenschaften und Beziehungen des Application-Objekts.|
|[Berechnen](../api/excelapplication_calculate.md)|Keine|Neu berechnet alle geöffnete Arbeitsmappen in Excel.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|calculationMode|string|Gibt den Berechnungsmodus in der Arbeitsmappe verwendet. Mögliche Werte sind: `Automatic`, `AutomaticExceptTables`, `Manual`. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.application"
}-->

```json
{
  "calculationMode": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Application resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->