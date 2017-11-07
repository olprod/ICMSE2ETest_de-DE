# <a name="appliedcategoriescollection-resource-type"></a>Ressourcentyp appliedCategoriesCollection

Die Ressource AppliedCategoriesCollection * stellt die Auflistung von Kategorien (oder Etiketten), die mit einer Aufgabe angewendet wurden. Es ist Teil des [Task](task.md) -Objekts.
Bis zu 6 Kategorien angewendet, die mit einer Aufgabe kann vorhanden sein. Namen der Kategorie, z. B. `category0`, `category1` usw., sind Teil des [Plandetails](plandetails.md) -Objekts. 

* Beachten Sie, dass dies ein offener Typ ist.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.appliedCategoriesCollection"
}-->

```json
{
  "String-value": true
}
```

Beispiel: 

```json
{
  "category0": true,
  "category3": true,
  "category5": true
}
```

## <a name="properties"></a>Eigenschaften
Eigenschaften vom Typ Open können vom Client definiert werden. Muss in diesem Fall jedoch der Client bereitstellen `category0`, `category1`, `category3`, `category4` und/oder `category5` als Eigenschaften mit ihren Werten wird die `true` boolescher Wert, wenn die entsprechenden Kategorien auf die Aufgabe angewendet werden. Beispiel oben. Wenn sie nicht zutreffen, werden die Eigenschaften automatisch durch Festlegen der entsprechenden Werte auf entfernt die `false` boolean. 

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appliedCategoriesCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->