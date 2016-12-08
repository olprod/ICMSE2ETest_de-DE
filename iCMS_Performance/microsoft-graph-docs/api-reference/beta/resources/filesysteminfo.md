# <a name="filesysteminfo-resource-type"></a>FileSystemInfo Ressourcentyp

Die Ressource **FileSystemInfo** enthält Eigenschaften, die vom lokalen Dateisystem des Geräts, für die lokale Version eines Elements gemeldet werden. Dieser Aspekt kann verwendet werden, um anzugeben, das letzte Änderungsdatum oder Erstellungsdatum des Elements auf dem lokalen Gerät war.


## <a name="properties"></a>Eigenschaften

| Eigenschaft                 | Typ           | Beschreibung                                                   |
|:-------------------------|:---------------|:--------------------------------------------------------------|
| **createdDateTime**      | DateTimeOffset | UTC-Datum und Uhrzeit die Datei auf einem Client erstellt wurde.       |
| **lastModifiedDateTime** | DateTimeOffset | UTC-Datum und Uhrzeit der letzten Änderung die Datei auf einem Client. |

## <a name="notes"></a>Hinweise

Werte für CreatedDateTime und LastModifiedDateTime unterscheiden sich die gleichen Eigenschaften für die Ressource [Driveitem](driveitem.md) . Die Werte für die Ressource Element sind Erstellungsdatum und Datum und Uhrzeit des Diensts gesehen.
Die Werte in der **FileSystemInfo** Facetten gespeichert werden vom Client bereitgestellt.

Beispielsweise, wenn eine Datei wurde auf dem Gerät am Montag erstellt, aber nicht mit dem Dienst bis Dienstag hochgeladen, der Client, der die Datei hochgeladen wird sollte geschrieben werden die `fileSystemInfo` Facetten Einbeziehung der Erstellungsdatum am Montag. Wenn die Elementmetadaten das Erstellungsdatum, abgerufen wird für das Element Dienstag, mehr wieder, aber die `fileSystemInfo` Facetten zeigt an den ursprünglichen Erstellungsdatum am Montag.

Diese Eigenschaften sind schreibgeschützt. Wenn Sie eine Datei hochladen und des lokalen Clients Werte für diese Felder wissen, sollten Sie sie in der Anforderung einschließen.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.fileSystemInfo"
}-->

```json
{
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}

```

## <a name="remarks"></a>Hinweise

Die **FileSystemInfo** -Eigenschaft ist nicht verfügbar für Elemente in SharePoint oder OneDrive für Unternehmen.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "fileSystemInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
