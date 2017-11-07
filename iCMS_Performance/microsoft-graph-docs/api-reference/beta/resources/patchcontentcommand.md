# <a name="patchcontentcommand-resource-type"></a>Ressourcentyp patchContentCommand

Die Änderungen an einer OneNote-Seite in einer Anforderung PATCH vornehmen.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource, die im Textkörper der gesendet wird die [PATCH Seiten /<id> ](../api/page_update.md) Anforderung. 

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.patchcontentcommand"
}-->

```json
{
  "action": "String",
  "content": "string",
  "position": "String",
  "target": "string"
}

```

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Aktion|String|Die für das Zielelement auszuführende Aktion. Mögliche Werte sind: `replace`, `append`, `insert`, oder `prepend`.|
|Inhalt|String|Eine Zeichenfolge wohlgeformt HTML-Code für die Seite und alle Bild oder Datei binären Daten hinzufügen. Wenn der Inhalt binäre Daten enthält, die Anforderung muss gesendet werden mithilfe der `multipart/form-data` Inhaltstyp mit einem Webpart "Befehle". |
|position|String|Der Speicherort, um den angegebenen Inhalt, relativ zum Zielelement hinzuzufügen. Mögliche Werte sind: `after` (Standard) oder `before`.|
|target|String|Das Element, zu aktualisieren. Muss die `#<data-id>` oder die generierte `<id>` des Elements, oder die `body` oder `title` Schlüsselwort.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "patchContentCommand resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->