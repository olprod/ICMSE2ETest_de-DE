# <a name="remoteitem-resource-type"></a>RemoteItem Ressourcentyp

Der Ressourcentyp **RemoteItem** gibt an, dass ein [DriveItem](driveitem.md) verweist auf ein Element, das in einem anderen Laufwerk vorhanden und enthält einen Zeiger auf dem Laufwerk.

Es steht auf der `remoteItem` -Eigenschaft des [DriveItem](driveitem.md) Ressourcen, die freigegeben haben und das feature mithilfe der "fügen zu OneDrive" beispielsweise auf einem Laufwerk hinzugefügt.

**Hinweis:** Im Gegensatz zu mit Ordnern in dem gleichen Laufwerk ein Element in ein Remoteelement verschoben möglicherweise seine `id` geändert.

## <a name="json-representation"></a>JSON-Darstellung

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.remoteItem", optionalProperties: ["name", "fileSystemInfo", "file", "folder"] } -->
```json
{
  "id": "string",
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "timestamp",
  "file": { "@odata.type": "microsoft.graph.file" },
  "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" },
  "folder": { "@odata.type": "microsoft.graph.folder" },
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "timestamp",
  "name": "string",
  "package": { "@odata.type": "microsoft.graph.package" },
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },
  "size": 1024,
  "specialFolder": { "@odata.type": "microsoft.graph.specialFolder" },
  "webDavUrl": "url",
  "webUrl": "url"
}
```

## <a name="properties"></a>Eigenschaften

| Name der Eigenschaft   | Typ                                           | Beschreibung                                                              |
|:----------------|:-----------------------------------------------|:-------------------------------------------------------------------------|
| createdBy       | [IdentitySet](identityset.md)            | Die Identität des Benutzers, Gerät, und die Anwendung die Erstellung des Elements. Schreibgeschützt.   |
| createdDateTime | Timestamp                                | Datum und Uhrzeit der Erstellung des Eintrags. Schreibgeschützt. |
| Datei            | [Datei](file.md)                          | Gibt an, dass das entfernte Element um eine Datei handelt. Schreibgeschützt.                     |
| fileSystemInfo  | [FileSystemInfo](filesysteminfo.md)      | Informationen über das entfernte Element im lokalen Dateisystem. Schreibgeschützt. |
| Ordner          | [Ordner](folder.md)                      | Gibt an, dass das entfernte Element um einen Ordner handelt. Schreibgeschützt.                   |
| id              | String                                         | Eindeutiger Bezeichner für das Remoteelement in dem Laufwerk. Schreibgeschützt.           |
| lastModifiedBy  | [IdentitySet](identityset,md)           | Das Element Identität der Benutzer, Geräte und Anwendung, die zuletzt geändert hat. Schreibgeschützt. |
| lastModifiedDateTime | Timestamp                           | Datum und Uhrzeit der letzten des Elements Änderung. Schreibgeschützt.  | 
| name            | String                                         | Optional Dateiname des remote-Elements. Schreibgeschützt.                        |
| Paket         | [Paket](package.md)                    | Falls vorhanden, gibt an, dass dieses Element ein Paket anstelle eines Ordners oder einer Datei ist. Pakete werden wie unter Umständen Dateien und Ordner in anderen behandelt. Schreibgeschützt. |
| parentReference | [ItemReference](itemreference.md) | Eigenschaften der das übergeordnete Objekt des das entfernte Element. Schreibgeschützt.                  |
| sharepointIds   | [SharepointIds](sharepointids.md) | Der vollständige Satz von Elementbezeichner bietet Interop zwischen Elementen in OneDrive für Unternehmen und SharePoint. Schreibgeschützt.  |
| size            | Int64                                          | Die Größe des remote-Elements. Schreibgeschützt.                                      |
| specialFolder   | [SpecialFolder](specialfolder.md) | Wenn das aktuelle Element auch als einen Ordner mit Sonderfunktion verfügbar ist, wird dieser Aspekt zurückgegeben. Schreibgeschützt. |
| webDavUrl       | Url | DAV-kompatible-URL für das Element. |
| webUrl          | Url | URL, die die Ressource im Browser angezeigt wird. Schreibgeschützt. | 


<!-- {
  "type": "#page.annotation",
  "description": "remoteItem resource type provides a link to an item in another drive.",
  "keywords": "remoteitem symlink remote drive shared with me add to onedrive",
  "section": "documentation"
} -->
