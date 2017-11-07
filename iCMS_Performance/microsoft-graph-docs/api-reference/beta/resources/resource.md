# <a name="resource-resource-type"></a>Ressourcentyp-Ressource

Ein Bild oder einer anderen Dateiressource auf einer OneNote-Seite. 

Sie können die binären Daten einer Ressource abrufen, jedoch eine JSON-Darstellung der eines Ressourcenobjekts oder eine Ressource Auflistung abrufen wird nicht unterstützt.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.resource"
}-->

Die binären Daten von einer bestimmten Ressource durch Senden einen GET an der Ressource Anforderung Get `content` Endpunkt:

```
GET ../notes/resources/<id>/content
```

Die File-Ressource wird URI zurückgegeben, wenn Sie HTML-Inhalt einer Seite mithilfe der folgenden Anforderung abrufen:

```
GET ../notes/pages/<id>/content
```

In der HTML-Seite ein `img` Tag enthält Endpunkte für die ursprünglichen Bildressource in der `data-fullres-src` -Attribut und das optimierte Bild in die `src` Attribut:
```
<img 
    src="image-resource-url"  
    data-src-type="media-type"
    data-fullres-src="image-resource-url"  
    data-fullres-src-type="media-type" ... />
```

Ein `object` Tag (die Dateien wie PDF, DOCX und PNG darstellt) enthält den Endpunkt für die Ressource in der `data` Attribut:

```
<object
    data="file-resource-url"
    data-attachment="file-name.file-type" 
    type="media-type" ... />
```

## <a name="properties"></a>Eigenschaften
Keine.

## <a name="relationships"></a>Beziehungen
Keine.


## <a name="methods"></a>Methoden
| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Ressource binäre Daten abrufen](../api/resource_get.md) | Stream |Rufen Sie die binären Daten einer Datei oder Bild Ressource ab.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "resource resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->