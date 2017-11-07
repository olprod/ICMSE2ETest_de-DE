# <a name="upload-or-replace-the-contents-of-a-driveitem"></a>Hochladen Sie oder Ersetzen Sie den Inhalt von einer driveItem

Die einfachen Upload-API können Sie den Inhalt einer neuen Datei bereitstellen oder Aktualisieren der Inhalte einer vorhandenen Datei in einem einzelnen API-Aufruf. Diese Methode unterstützt nur die Dateien bis zu 4MB groß.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PUT /me/drive/items/{parent-id}:/{filename}:/content
PUT /me/drive/root:/{parent-path}/{filename}:/content
PUT /me/drive/items/{parent-id}/children/{filename}/content
PUT /groups/<id>/drive/items/<parent-id>/children/<filename>/content
```

## <a name="request-body"></a>Anforderungstext
Der Inhalt der Textkörper der Anforderung sollte den binären Stream, der die Datei hochgeladen werden.

## <a name="response"></a>Antwort
Wenn erfolgreich, gibt diese Methode ein [DriveItem](../resources/driveitem.md) Objekt im Antworttext für die neu erstellte Datei.

## <a name="example"></a>Beispiel
In diesem Beispiel wird eine Datei durch den Pfad zu OneDrive des angemeldeten Benutzers hochlädt.

<!-- {
  "blockType": "request",
  "name": "upload_item"
}-->
```http
PUT /me/drive/root:/{item-path}:/content
Content-type: text/plain

The contents of the file goes here.
```

## <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "myfile.jpg",
  "size": 10191,
  "file": { }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Upload item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
