# <a name="driveitem-resource-type"></a>Ressourcentyp driveItem

Die Ressource **DriveItem** stellt ein Element in ein Laufwerk. Alle Datei der obersten Ebene Systemobjekte in OneDrive werden als Element Ressourcen zurückgegeben. Sie zugegriffen werden können, deren **Id** mit der `/items/{item-id}` Syntax oder ihre Datei System Pfad mit der `/drive/root:/path/to/file` Syntax.

Elemente verfügen Facetten modelliert als Eigenschaften, die Daten über des Elements Identitäten und Funktionen bereitstellen. Ordner vorhanden sind, ein [Facetten **Ordner** ](folder.md) und Dateien vorhanden sind, eine [**Datei Facetten**](file.md). Bilder haben ein [**Bild Facetten**](image.md) neben ihrer Datei Facetten.

Elemente mit dem **Ordner** Facetten fungieren als Container von Elementen und daher ein `children` Verweis auf eine Auflistung von Elementen im Ordner zeigen.

## <a name="methods"></a>Methoden

| Methode                                                 | Rückgabetyp                                | Beschreibung                                                                                                                             |
|:-------------------------------------------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| [Element abrufen](../api/item_get.md)                         | [driveitem](driveitem.md)                  | Eigenschaften lesen und Beziehungen des Item-Objekts.                                                                                       |
| [Untergeordnete Objekte auflisten](../api/item_list_children.md)          | [Driveitem](driveitem.md) -Auflistung       | Rufen Sie eine untergeordnete Auflistung-Objekts.                                                                                                       |
| [Element erstellen](../api/item_post_children.md)            | [driveitem](driveitem.md)                  | Erstellen Sie ein neues Element, indem Sie das Veröffentlichen in der Auflistung untergeordneter Elemente.                                                                                |
| [Update-Element](../api/item_update.md)                   | [driveitem](driveitem.md)                  | Aktualisieren Sie die Item-Objekts.                                                                                                                     |
| [Hochladen von Inhalt](../api/item_uploadcontent.md)         | Einzelheiten finden Sie unter API                        | Die einfachen Upload-API können Sie den Inhalt einer neuen Datei bereitstellen oder Aktualisieren der Inhalte einer vorhandenen Datei in einem einzelnen API-Aufruf. |
| [Herunterladen von Inhalten](../api/item_downloadcontent.md)     | Einzelheiten finden Sie unter API                        | Laden Sie den Inhalt für ein Element.                                                                                                      |
| [Element löschen](../api/item_delete.md)                   | Keine                                       | Löschen Sie die Item-Objekts.                                                                                                                     |
| [Element verschieben](../api/item_move.md)                       | [driveitem](driveitem.md)                  | Aktualisieren des übergeordneten Ordners für ein Element durch ID oder Pfad. Um ein Element verschieben, aktualisieren Sie die ParentReference-Eigenschaft.                           |
| [Element kopieren](../api/item_copy.md)                       | [driveitem](driveitem.md)                  | Erstellen Sie eine Kopie eines Elements und seinen Inhalt mit einem neuen Namen oder das übergeordnete Element.                                                                |
| [Von Suchelementen](../api/item_search.md)                  | [Driveitem](driveitem.md) -Auflistung       | Suchen Sie nach Elementen anhand einer Abfrage.                                                                                                      |
| [Suchen Sie nach Änderungen](../api/item_delta.md)                   | [DriveItem](driveitem.md) -Auflistung       | Änderungen für ein Element und die untergeordneten Elemente anzeigen.                                                                                              |
| [Liste Miniaturansichten](../api/item_list_thumbnails.md)      | [ThumbnailSet](thumbnailset.md) -Auflistung | Rufen Sie eine Auflistung der ThumbnailSet-Objekts.                                                                                                   |
| [Anwendungsfreigabe Link erstellen](../api/item_createlink.md)       | [Berechtigung](permission.md)                | Erstellen Sie einen Freigabe Link, um die Datei für andere Benutzer freigeben.                                                                               |
| [Hinzufügen von Berechtigungen](../api/item_invite.md)               | [Berechtigung](permission.md)                | Erstellen Sie eine neue Berechtigung durch Senden einer freigabeeinladung.                                                                                |
| [Listenberechtigungen](../api/item_list_permissions.md)    | [Permission](permission.md) -Auflistung     | Rufen Sie eine Permission-Objekt-Auflistung.                                                                                                     |
| [DELETE-Berechtigung](../api/permission_delete.md) | Keine                                       | Entfernen Sie eine Berechtigung aus einem Element.                                                                                                       |

## <a name="properties"></a>Eigenschaften

| Eigenschaft             | Typ                                | Beschreibung                                                                                                                                                               |
|:---------------------|:------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Audio                | [Audio](audio.md)                   | Audio Metadaten, wenn das Element einer Audiodatei ist. Schreibgeschützt.                                                                                                                  |
| Inhalt              | Stream                              | Der Inhaltsstream, wenn das Element eine Datei darstellt.                                                                                                                        |
| createdBy            | [identitySet](identityset.md)       | Die Identität des Benutzers, Gerät, und die Anwendung die Erstellung des Elements. Schreibgeschützt.                                                                                          |
| createdDateTime      | DateTimeOffset                      | Datum und Uhrzeit der Erstellung des Eintrags. Schreibgeschützt.                                                                                                                                |
| cTag                 | String                              | ETag für den Inhalt des Elements. Diese eTag wird nicht geändert, wenn nur die Metadaten geändert wird. **Hinweis** Diese Eigenschaft wird nicht zurückgegeben, wenn das Element einen Ordner handelt. Schreibgeschützt. |
| gelöscht              | [gelöscht](deleted.md)               | Informationen zum gelöschten Status des Elements. Schreibgeschützt.                                                                                                               |
| eTag                 | String                              | eTag für das gesamte Element (Metadaten + Inhalte). Schreibgeschützt.                                                                                                                 |
| Datei                 | [Datei](file.md)                     | Datei Metadaten, wenn das Element eine Datei ist. Schreibgeschützt.                                                                                                                          |
| fileSystemInfo       | [fileSystemInfo](filesysteminfo.md) | Systeminformationen auf Client. Lese-/ Schreibzugriff.                                                                                                                            |
| Ordner               | [Ordner](folder.md)                 | Ordnermetadaten, wenn das Element einen Ordner handelt. Schreibgeschützt.                                                                                                                      |
| id                   | String                              | Der eindeutige Bezeichner des Elements in das Laufwerk. Schreibgeschützt.                                                                                                            |
| image                | [Bild](image.md)                   | Bildmetadaten, wenn das Element ein Bild ist. Schreibgeschützt.                                                                                                                       |
| lastModifiedBy       | [identitySet](identityset.md)       | Das Element Identität der Benutzer, Geräte und Anwendung, die zuletzt geändert hat. Schreibgeschützt.                                                                                    |
| lastModifiedDateTime | DateTimeOffset                      | Datum und Uhrzeit der letzten des Elements Änderung. Schreibgeschützt.                                                                                                                      |
| Speicherort             | [geoCoordinates](geoCoordinates.md) | Metadaten Speicherort Standortdaten besitzt. Schreibgeschützt.                                                                                                              |
| name                 | String                              | Der Name des Elements (Dateiname und Erweiterung). Lese-/ Schreibzugriff.                                                                                                                |
| Paket              | [Paket](package.md)               | Falls vorhanden, gibt an, dass dieses Element ein Paket anstelle eines Ordners oder einer Datei ist. Pakete werden wie unter Umständen Dateien und Ordner in anderen behandelt. Schreibgeschützt.         |
| parentReference      | [itemReference](itemreference.md)   | Informationen zur übergeordneten, wenn das Element ein übergeordnetes Objekt ist. Lese-/ Schreibzugriff.                                                                                                                 |
| Foto                | [Foto](photo.md)                   | Foto Metadaten, wenn das Element ein Foto ist. Schreibgeschützt.                                                                                                                        |
| remoteItem           | [remoteItem](remoteitem.md)         | Remoteelement Daten, wenn das Element auf ein anderes Laufwerk als das zugegriffen wird freigegeben ist. Schreibgeschützt.                                                                        |
| searchResult         | [searchResult](searchresult.md)     | Suchen Sie Metadaten, wenn das Element aus einem Suchergebnis ist. Schreibgeschützt.                                                                                                          |
| Freigegeben               | [Shared](shared.md)                 | Gibt an, dass das Element für andere Personen freigegeben wurde und Informationen zu den freigegebenen Zustand des Elements enthält. Schreibgeschützt.                                               |
| sharepointIds        | [sharepointIds](sharepointIds.md)   | Der vollständige Satz von Elementbezeichner bietet Interop zwischen Elementen in OneDrive für Unternehmen und SharePoint. Schreibgeschützt. |
| size                 | Int64                               | Die Größe des Elements in Bytes. Schreibgeschützt.                                                                                                                                     |
| specialFolder        | [specialFolder](specialfolder.md)   | Wenn das aktuelle Element auch als einen Ordner mit Sonderfunktion verfügbar ist, wird dieser Aspekt zurückgegeben. Schreibgeschützt.                                                                             |
| Video                | [Video](video.md)                   | Video-Metadaten, wenn das Element ein Video ist. Schreibgeschützt.                                                                                                                        |
| webUrl               | String                              | URL, die die Ressource im Browser angezeigt wird. Schreibgeschützt.                                                                                                                 |

                                                                                                                |

**Hinweis:** Die eTag und cTag-Eigenschaften arbeiten unterschiedlich für Container (Ordner). Der Wert cTag wird geändert, wenn Inhalt oder die Metadaten des alle Nachfolger des Ordners geändert wird. Der eTag-Wert wird nur geändert, wenn die Eigenschaften des Ordners geändert werden, mit Ausnahme von Eigenschaften, die untergeordnete Objekte (wie **ChildCount** oder **LastModifiedDateTime**) abgeleitet sind.

## <a name="instance-attributes"></a>Instanzattribute

Instanzattribute sind Eigenschaften mit besonderen Verhaltensweisen. Diese Eigenschaften sind temporäre und entweder eine) definieren das Verhalten der Dienst sollte ausführen oder b) bieten kurzfristige Eigenschaftswerte, wie eine URL zum Herunterladen für ein Element, das läuft ab.

| Name der Eigenschaft                     | Typ   | Beschreibung                                                                                                                                                         |
|:----------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @microsoft.graph.conflictBehavior | string | Das Conflict Lösung Verhalten für Aktionen, die ein neues Element erstellen. Ein Element wird mit dieser Anmerkung niemals zurückgegeben. Nur schreiben.                               |
| @microsoft.graph.downloadUrl      | string | Eine URL, die zum Herunterladen von Inhalten mit dieser Datei verwendet werden kann. Authentifizierung ist nicht mit dieser URL erforderlich. Schreibgeschützt.                                                    |
| @microsoft.graph.sourceUrl        | string | Beim Ausgeben einer PUT-Anforderung, kann diese Instanz Anmerkung angewiesen, den Dienst zu laden Sie den Inhalt der URL, und speichern Sie sie, wie die Datei verwendet werden. Nur schreiben. |

**Hinweis:** Die @microsoft.graph.downloadUrl Wert ist eine kurzlebige URL und können nicht zwischengespeichert werden. Die URL ist verfügbar für kurze Zeit an, bevor es ungültig ist.

## <a name="relationships"></a>Beziehungen

| Beziehung       | Typ                                       | Beschreibung                                                                                                                                                                       |
|:-------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| untergeordnete Elemente           | [Driveitem](driveitem.md) -Auflistung       | Auflistung mit der Item-Objekte für die unmittelbar untergeordneten Elemente des Elements. Nur Elemente, die Ordner darstellen haben untergeordnete Elemente. Schreibgeschützt. NULL-Werte zulässt.                                        |
| createdByUser      | [Benutzer](user.md)                            | Die Identität des Benutzers, Gerät, und die Anwendung die Erstellung des Elements. Schreibgeschützt.                                                                                                  |
| lastModifiedByUser | [Benutzer](user.md)                            | Das Element Identität der Benutzer, Geräte und Anwendung, die zuletzt geändert hat. Schreibgeschützt.                                                                                            |
| Berechtigungen        | [Permission](permission.md) -Auflistung     | Der Satz von Berechtigungen für das Element. Schreibgeschützt. NULL-Werte zulässt.                                                                                                                         |
| Miniaturansichten         | [ThumbnailSet](thumbnailset.md) -Auflistung | -Auflistung, die dem Element zugeordneten [ThumbnailSet](thumbnailSet.md) -Objekte enthält. Weitere Informationen finden Sie unter [erste Miniaturansichten](../api/thumbnailset_get.md). Schreibgeschützt. NULL-Werte zulässt. |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "children", "createdByUser", "lastModifiedByUser", "permissions", "thumbnails"],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.driveItem"
}-->

```json
{
  "audio": {"@odata.type": "microsoft.graph.audio"},
  "cTag": "string",
  "content": "stream",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "eTag": "string",
  "file": {"@odata.type": "microsoft.graph.file"},
  "fileSystemInfo": {"@odata.type": "microsoft.graph.fileSystemInfo"},
  "folder": {"@odata.type": "microsoft.graph.folder"},
  "id": "string (identifier)",
  "image": {"@odata.type": "microsoft.graph.image"},
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.geoCoordinates"},
  "name": "string",
  "package": {"@odata.type": "microsoft.graph.package"},
  "parentReference": {"@odata.type": "microsoft.graph.itemReference"},
  "photo": {"@odata.type": "microsoft.graph.photo"},
  "remoteItem": {"@odata.type": "microsoft.graph.remoteItem"},
  "searchResult": {"@odata.type": "microsoft.graph.searchResult"},
  "shared": {"@odata.type": "microsoft.graph.shared"},
  "size": 1024,
  "specialFolder": {"@odata.type": "microsoft.graph.specialFolder"},
  "video": {"@odata.type": "microsoft.graph.video"},
  "webDavUrl": "string",
  "webUrl": "string",

  "createdByUser": { "@odata.type": "microsoft.graph.user" },
  "lastModifiedByUser": { "@odata.type": "microsoft.graph.user" },
  "children": [ { "@odata.type": "microsoft.graph.driveItem" }],
  "thumbnails": [ {"@odata.type": "microsoft.graph.thumbnailSet"}],
  "permissions": [ {"@odata.type": "microsoft.graph.permission"} ]
}

```

## <a name="remarks"></a>Hinweise

Die **cTag** -Eigenschaft wird in OneDrive for Business nicht zurückgegeben, wenn das Element einen [Ordner](folder.md)handelt.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
