# <a name="hashes-resource-type"></a>Hash Ressourcentyp

Die **Hashes** Facetten gruppiert verschiedene Typen des weiteren in einer einzelnen Struktur, für ein Element.


## <a name="properties"></a>Eigenschaften

| Eigenschaft      | Typ                   | Beschreibung                                                       |
|:--------------|:-----------------------|:------------------------------------------------------------------|
| **sha1Hash**  | String (Hex-Format) | SHA1-Hash für den Inhalt der Datei (sofern verfügbar). Schreibgeschützt. |
| **crc32Hash** | String (Hex-Format) | Der CRC32-Wert der Datei (sofern verfügbar). Schreibgeschützt.            |


**Hinweis:** In einigen Fällen Hash Werte möglicherweise nicht zur Verfügung. Wenn dies der Fall ist, werden der Hashwert für ein Element nach dem Download des Elements aktualisiert.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.hashes"
}-->

```json
{
  "crc32Hash": "string",
  "sha1Hash": "string"
}
```

## <a name="remarks"></a>Hinweise

Werte sind in OneDrive for Business Hash nicht verfügbar.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "hashes resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
