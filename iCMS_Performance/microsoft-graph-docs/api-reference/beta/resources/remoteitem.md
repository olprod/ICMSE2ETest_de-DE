# <a name="remoteitem-resource-type"></a>remoteItem resource type

The **remoteItem** resource type indicates that a [driveItem](driveitem.md) references an item that exist in another drive and provides a pointer to that drive.

It is available on the `remoteItem` property of [driveItem](driveitem.md) resources that have been shared and added to a drive, for example, by using the "Add to OneDrive" feature.

**Note:** Unlike with folders in the same drive, an item moved into a remote item might have its `id` changed.

## <a name="json-representation"></a>JSON representation

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

| Eigenschaftsname   | Typ                                           | Beschreibung                                                              |
|:----------------|:-----------------------------------------------|:-------------------------------------------------------------------------|
| createdBy       | [IdentitySet](identityset.md)            | Identity of the user, device, and application which created the item. Read-only.   |
| createdDateTime | Timestamp                                | Datum und Uhrzeit der Cubeerstellung. |
| File            | [File](file.md)                          | Indicates that the remote item is a file. Read-only.                     |
| fileSystemInfo  | [FileSystemInfo](filesysteminfo.md)      | Information about the remote item from the local file system. Read-only. |
| Ordner          | [Folder](folder.md)                      | Indicates that the remote item is a folder. Read-only.                   |
| id              | String                                         | Unique identifier for the remote item in its drive. Read-only.           |
| lastModifiedBy  | [IdentitySet](identityset,md)           | Identity of the user, device, and application which last modified the item. Read-only. |
| lastModifiedDateTime | Timestamp                           | Es wird ein Wert vom Typ Date zurückgegeben, der das Datum und die Uhrzeit der letzten Änderung des Outlook-Elements angibt. Schreibgeschützt.  | 
| name            | String                                         | Optional. Filename of the remote item. Read-only.                        |
| Paket         | [-Paket](package.md)                    | If present, indicates that this item is a package instead of a folder or file. Packages are treated like files in some contexts and folders in others. Read-only. |
| parentReference | [ItemReference](itemreference.md) | Properties of the parent of the remote item. Read-only.                  |
| sharepointIds   | [SharepointIds](sharepointids.md) | Provides interop between items in OneDrive for Business and SharePoint with the full set of item identifiers. Read-only.  |
| size            | Int64                                          | Size of the remote item. Read-only.                                      |
| specialFolder   | [SpecialFolder-Konstanten](specialfolder.md) | If the current item is also available as a special folder, this facet is returned. Read-only. |
| webDavUrl       | Url | DAV compatible URL for the item. |
| WebUrl          | Url | URL that displays the resource in the browser. Read-only. | 


<!-- {
  "type": "#page.annotation",
  "description": "remoteItem resource type provides a link to an item in another drive.",
  "keywords": "remoteitem symlink remote drive shared with me add to onedrive",
  "section": "documentation"
} -->
