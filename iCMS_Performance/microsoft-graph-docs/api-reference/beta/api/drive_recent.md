# <a name="list-recently-used-files"></a>List recently used files

List a set of items that have been recently used by the signed in user. This list includes items that are in the user's drive as well as items they have access to from other drives.

## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API:

  * Files.Read

## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```
GET /me/drive/recent
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Required.                                                                                                                                                                         |

## <a name="request-body"></a>Anforderungstextkörper
Do not supply a request body for this method.

## <a name="example"></a>Beispiel

<!-- { "blockType": "request", "name": "drive-recent", "scopes": "files.read" } -->
```http
GET /me/drive/recent
```

## <a name="response"></a>Antwort

This returns a collection of [driveItem resources](../resources/driveitem.md) that contains items which have been shared with the signed-in user.


<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "isCollection": true, "truncated": true } -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "1312abc!1231",
      "remoteItem":
      {
        "id": "1991210caf!192",
        "name": "March Proposal.docx",
        "file": { },
        "size": 19121,
        "parentReference": {
          "driveId": "1991210caf",
          "id": "1991210caf!104"
        }
      }
    },
    {
      "id": "1312def!9943",
      "name": "Vacation.jpg",
      "file": { },
      "size": 37810,
      "parentReference": {
        "driveId": "1312def",
        "id": "1312def!123"
      }
    }
  ]
}
```

## <a name="remarks"></a>Hinweise

Some driveItems returned from the **recent** action will include the **remoteItem** facet which indicates they are items from another drive. To access the original driveItem object, you will need to make a request using the information provided in **remoteItem** in the following format:

<!-- {"blockType": "ignored"} -->
```http
GET /drives/<remoteItem.driveId>/items/<id>
```

<!-- {
  "type": "#page.annotation",
  "description": "Retrieve a list of files shared with the signed-in user.",
  "keywords": "sharedWithMe onedrive shared files",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Shared with me"
} -->
