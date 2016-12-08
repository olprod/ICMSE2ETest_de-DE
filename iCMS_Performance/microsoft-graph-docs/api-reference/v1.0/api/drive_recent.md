# <a name="list-recently-used-files"></a>Liste der zuletzt verwendeten Dateien

Auflisten einer Reihe von Elementen, die vom angemeldeten Benutzer zuletzt verwendet wurden. Diese Liste enthält Elemente, die sich in dem Laufwerk des Benutzers sowie Elemente, die von anderen Laufwerken zugreifen kann.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```
GET /me/drive/recent
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="example"></a>Beispiel

<!-- { "blockType": "request", "name": "drive-recent", "scopes": "files.read" } -->
```http
GET /me/drive/recent
```

## <a name="response"></a>Antwort

Dies gibt eine Auflistung von [DriveItem Ressourcen](../resources/driveitem.md) , die Elemente enthält, die mit dem angemeldeten Benutzer freigegeben wurden.


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

Einige DriveItems zurückgegeben, die durch die **letzte** Aktion wird das **RemoteItem** Facetten enthalten, die gibt an, dass sie Elemente aus einem anderen Laufwerk sind. Zugriff auf das ursprüngliche DriveItem-Objekt müssen Sie die Anforderung mithilfe der Informationen in **RemoteItem** im folgenden Format:

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
