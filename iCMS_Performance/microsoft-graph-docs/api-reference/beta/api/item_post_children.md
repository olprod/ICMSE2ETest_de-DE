# <a name="create-a-new-folder-driveitem"></a>Erstellt einen neuen Ordner driveItem

Verwenden Sie diese API, um einen neuen Ordner in einem Laufwerk zu erstellen. Ihre app kann Ordner im Stamm des ein Laufwerk, unter einer vorhandenen DriveItem mit einer Ordnereigenschaft oder im OneDrive-Ordner [ **Approot** erstellen](https://dev.onedrive.com/misc/appfolder.htm)

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/root/children
POST /me/drive/items/<id>/children
POST /me/drives/<id>/root/children
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung eines [DriveItem](../resources/driveitem.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Element](../resources/driveitem.md) im Antworttext.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Es folgt ein Beispiel einer Anforderung für einen neuen Ordner im Stamm des OneDrive eines Benutzers zu erstellen.

<!-- {
  "blockType": "request",
  "name": "create_item_from_item"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/root/children
Content-Type: application/json

{
  "folder": { },
  "name": "Graph Project Files"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Item](../resources/driveitem.md) -Objekts.

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "createdBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "createdDateTime": "2016-03-21T20:01:37Z",
  "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
  "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
  "folder": {
      "childCount": 0
  },
  "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
  "lastModifiedBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "lastModifiedDateTime": "2016-03-21T20:01:37Z",
  "name": "Graph Project Files",
  "parentReference": {
      "driveId": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "id": "01NKDM7HN6Y2GOVW7725BZO354PWSELRRZ",
      "path": "/drive/root:"
  },
  "size": 0,
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/Graph%20Project%20Files"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create children",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Create folder"
}-->
