# <a name="rankedemailaddress-resource-type"></a>Ressourcentyp rankedEmailAddress

Stellt eine bewerteter e-Mail-Adresse dar.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|address|string|E-Mail-Adresse.|
|Rang|double|Die Rangfolge der e-Mail-Adresse. Ein Rang wird als Sortierschlüssel, in Bezug auf die anderen zurückgegebenen Ergebnisse verwendet. Ein höherer Rangwert entspricht ein relevanter Ergebnis. Relevanz ergibt sich für die Zusammenarbeit, Kommunikation und geschäftlichen Beziehung signalisiert.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rankedemailaddress"
}-->

```json
{
  "address": "string",
  "rank": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "rankedEmailAddress resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
