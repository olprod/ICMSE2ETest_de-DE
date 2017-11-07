# <a name="hashes-resource-type"></a>Hash Ressourcentyp

Die **Hashes** Facetten gruppiert verschiedene Typen des weiteren in einer einzelnen Struktur, für ein Element.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "sha1Hash", "crc32Hash", "quickXorHash" ],
  "@odata.type": "microsoft.graph.hashes"
}-->

```json
{
  "crc32Hash": "string",
  "sha1Hash": "string",
  "quickXorHash": "string"
}
```


## <a name="properties"></a>Eigenschaften

| Eigenschaft      | Typ                   | Beschreibung                                                       |
|:--------------|:-----------------------|:------------------------------------------------------------------|
| **sha1Hash**  | String  | SHA1-Hash für den Inhalt der Datei (sofern verfügbar). Schreibgeschützt. |
| **crc32Hash** | String  | Der CRC32-Wert der Datei (sofern verfügbar). Schreibgeschützt.            |
| **quickXorHash** | String | Eine proprietäre Hash der Datei, die verwendet werden kann, um festzustellen, ob der Inhalt der Datei (sofern verfügbar) geändert hat. Schreibgeschützt. | 

**Hinweis:** In einigen Fällen Hash Werte möglicherweise nicht zur Verfügung. Wenn dies der Fall ist, werden der Hashwert für ein Element nach dem Download des Elements aktualisiert.



## <a name="remarks"></a>Hinweise

In OneDrive für Unternehmen sind **sha1Hash** und **crc32Hash** nicht verfügbar.

**QuickXorHash** ist in OneDrive persönlich nicht verfügbar.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "hashes resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
