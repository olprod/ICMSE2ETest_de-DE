# <a name="update-a-driveitem-metadata"></a>Aktualisieren Sie eine DriveItem Metadaten

Aktualisieren Sie die Metadaten für ein DriveItem durch ID oder Pfad.

Sie können auch Update verwenden, um ein Element in einer anderen übergeordneten verschieben, durch die Elementeigenschaft **ParentReference** aktualisieren.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/drive/items/{item-id}
PATCH /me/drive/root:/{item-path}
PATCH /groups/<id>/drive/items/<item-id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                         |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                           |
| If-Match-      | String | Wenn diese Anforderungsheader enthalten und bereitgestellten eTag (oder cTag) nicht das aktuelle eTag für den Ordner entspricht ein `412 Precondition Failed` Antwort zurückgegeben wird. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für Eigenschaften, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten Ihre app nicht Eigenschaften enthalten, die nicht geändert haben.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [Artikel](../resources/driveitem.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
In diesem Beispiel wird die Datei und fügt eine Beschreibung der DriveItem hinzu.

<!-- {
  "blockType": "request",
  "name": "update_item"
}-->
```http
PATCH /me/drive/items/<item-id>
Content-type: application/json

{
    "name": "new-file-name.docx",
  "description": "Adding a description to this file",
}
```

## <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Diese Antwort wird zur besseren Lesbarkeit wurde abgeschnitten.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
    "name": "new-file-name.docx",
  "description": "Adding a description to this file",
    "file": { }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Update item"
}-->
