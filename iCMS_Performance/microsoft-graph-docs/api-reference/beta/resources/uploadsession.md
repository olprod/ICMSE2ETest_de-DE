# <a name="uploadsession-resource-type"></a>Ressourcentyp uploadSession

Die Upload-Sitzung bietet Informationen zur Verwendung von großen hochladen zu OneDrive OneDrive for Business oder SharePoint-Dokumentbibliotheken Dateien.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "uploadUrl", "nextExpectedRanges" ],
  "@odata.type": "microsoft.graph.uploadSession"
}-->

```json
{
  "expirationDateTime": "String (timestamp)",
  "nextExpectedRanges": ["string"],
  "uploadUrl": "url"
}

```
## <a name="properties"></a>Eigenschaften


| Eigenschaft           | Typ              |Beschreibung|
|:-------------------|:------------------|:----------|
| expirationDateTime | DateTime          | Datum und Uhrzeit in UTC, der die Sitzung Upload Bootstrapkonto abläuft. Die vollständige Datei muss hochgeladen werden, bevor diese Ablaufzeit erreicht wird. |
| nextExpectedRanges | String-Auflistung | Eine Auflistung von Bytebereiche, die der Server für die Datei nicht vorhanden ist. Diese Bereiche sind 0 indiziert und von dem Format "Start-End" (z. B. "0-26" an, dass die erste 27 Bytes der Datei). |
| uploadUrl          | String            | Der URL-Endpunkt, der PUT-Anforderungen für Bytebereiche der Datei akzeptiert. |

## <a name="additional-resources"></a>Weitere Ressourcen

Ausführliche Informationen zum Hochladen einer Sitzung Hochladen von Dateien finden Sie unter [Hochladen große Dateien mit einer Sitzung hochladen](../api/item_createUploadSession.md) .

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "uploadSession resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->