# <a name="file-resource-type"></a>Resource-Dateityp

**File** -Ressource gruppiert dateibezogenen Datenelemente in eine einzelne Struktur.


## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ                    | Beschreibung                                                                                                                                      |
|:---------|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| Hashes   | [HashesType](hashes.md) | Hashes der Inhalt der Datei binary, sofern verfügbar. Schreibgeschützt.                                                                                    |
| MIME-Typ | string                  | Den MIME-Typ für die Datei. Dies wird durch Logik auf dem Server bestimmt und möglicherweise nicht der Wert bereitgestellt werden, wenn die Datei hochgeladen wurde. Schreibgeschützt. |


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ ],
  "@odata.type": "microsoft.graph.file"
}-->

```json
{
  "hashes": {"@odata.type": "microsoft.graph.hashes"},
  "mimeType": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "file resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
