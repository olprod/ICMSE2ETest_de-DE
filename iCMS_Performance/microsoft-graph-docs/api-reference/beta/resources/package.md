# <a name="package-resource-type"></a>Paket Ressourcentyp

Das **Paket** Facetten gibt an, dass ein Element das Element der obersten Ebene in einem "Paket" oder eine Auflistung von Elementen, die als eine Sammlung von Daten, anstatt einzelne Elemente behandelt werden.

Ein Beispiel für ein Paket ist ein OneNote-Notizbuch. Während das Notizbuch von Dateien und Ordnern, die den Inhalt des Notizbuchs darstellen besteht, hat das Element der obersten Ebene, das das Notizbuch darstellt ein **Paket** Facetten Clients an, dass dies ist eine Auflistung von Daten, die spezielle behandelt werden soll.

Elemente mit dem **Paket** Facetten enthalten einen **Ordner** oder eine **Datei** Facetten nicht jedoch ähneln ein Element mit einem **Ordner** Facetten.

## <a name="json-representation"></a>JSON-Darstellung

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.package" } -->
```json
{
  "type": "oneNote"
}
```

| Name der Eigenschaft | Typ   | Beschreibung                                                                                                                                                                      |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Typ**      | string | Eine Zeichenfolge, die den Typ des Pakets angibt. Während `oneNote` ist der einzige Wert derzeit definierten, sollten Sie erwarten, andere Pakettypen zurückgegeben werden, und sie entsprechend behandelt. |

<!-- {
  "type": "#page.annotation",
  "description": "The Package facet indicates that an item is the root of a special collection of items that should be treated as a single unit.",
  "keywords": "package, facet, onenote",
  "section": "documentation"
} -->
