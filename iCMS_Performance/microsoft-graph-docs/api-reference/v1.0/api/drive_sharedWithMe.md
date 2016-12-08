# <a name="list-items-shared-with-the-signed-in-user"></a>Listenelemente, die gemeinsam mit dem angemeldeten Benutzers

Listen Sie den Satz der Elemente, die für den aktuellen Benutzer freigegeben werden auf.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```
GET /me/drive/sharedWithMe
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="example"></a>Beispiel

<!-- { "blockType": "request", "name": "drive-sharedwithme", "scopes": "files.read" } -->
```http
GET /me/drive/sharedWithMe
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
      "id": "1312abc",
      "remoteItem": {
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
      "id": "1312def",
      "remoteItem": {
        "id": "1991210caf!1991",
        "name": "Team Roster.xlsx",
        "file": { },
        "size": 37619,
        "parentReference": {
          "driveId": "1991210caf",
          "id": "1991210caf!104"
        }
      }
    }
  ]
}
```

## <a name="remarks"></a>Hinweise

Die Aktion **SharedWithMe** zurückgegebenes DriveItems berücksichtigt immer die **RemoteItem** Facetten gibt an, dass sie Elemente von einem anderen Laufwerk sind. Zugriff auf das ursprüngliche DriveItem-Objekt müssen Sie die Anforderung mithilfe der Informationen in **RemoteItem** im folgenden Format:

<!-- {"blockType": "ignored"} -->
```http
GET /drives/<remoteItem.parentReference.driveId>/items/<id>
```

<!-- {
  "type": "#page.annotation",
  "description": "Retrieve a list of files shared with the signed-in user.",
  "keywords": "sharedWithMe onedrive shared files",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Shared with me"
} -->
