# <a name="remoteitem-resource-type"></a>RemoteItem Ressourcentyp

Der Ressourcentyp **RemoteItem** gibt an, dass ein [DriveItem](driveitem.md) verweist auf ein Element, das in einem anderen Laufwerk vorhanden und enthält einen Zeiger auf dem Laufwerk.

Es steht auf der `remoteItem` -Eigenschaft des [DriveItem](driveitem.md) Ressourcen, die freigegeben haben und das feature mithilfe der "fügen zu OneDrive" beispielsweise auf einem Laufwerk hinzugefügt.

**Hinweis:** Im Gegensatz zu mit Ordnern in dem gleichen Laufwerk ein Element in ein Remoteelement verschoben möglicherweise seine `id` geändert.


## <a name="properties"></a>Eigenschaften

| Name der Eigenschaft   | Typ                                           | Beschreibung                                                              |
|:----------------|:-----------------------------------------------|:-------------------------------------------------------------------------|
| Datei            | [Datei](file.md)                          | Gibt an, dass das entfernte Element um eine Datei handelt. Schreibgeschützt.                     |
| fileSystemInfo  | [FileSystemInfo](filesysteminfo.md)      | Informationen über das entfernte Element aus dem lokalen Dateisystem. Schreibgeschützt. |
| Ordner          | [Ordner](folder.md)                      | Gibt an, dass das entfernte Element einen Ordner handelt. Schreibgeschützt.                   |
| id              | String                                         | Eindeutiger Bezeichner für das Remoteelement in dem Laufwerk. Schreibgeschützt.           |
| name            | String                                         | Optional Der Dateiname des remote-Elements. Schreibgeschützt.                        |
| parentReference | [ItemReference](itemreference.md) | Die Eigenschaften des übergeordneten Elements des remote-Elements. Schreibgeschützt.                  |
| size            | Int64                                          | Die Größe des remote-Elements. Schreibgeschützt.                                      |


## <a name="json-representation"></a>JSON-Darstellung

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.remoteItem", optionalProperties: ["name", "fileSystemInfo", "file", "folder"] } -->
```json
{
  "id": "string",
  "file": { "@odata.type": "microsoft.graph.file" },
  "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" },
  "folder": { "@odata.type": "microsoft.graph.folder" },
  "name": "string",
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "size": 1024
}
```
<!-- {
  "type": "#page.annotation",
  "description": "remoteItem resource type provides a link to an item in another drive.",
  "keywords": "remoteitem symlink remote drive shared with me add to onedrive",
  "section": "documentation"
} -->
