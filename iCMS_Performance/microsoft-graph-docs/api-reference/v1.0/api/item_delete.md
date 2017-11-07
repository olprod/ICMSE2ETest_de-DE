# <a name="delete-an-item"></a>Löschen eines Elements

Löschen eines Elements mithilfe von dessen ID oder den Pfad an. Beachten Sie, dass Elemente, die mit dieser Methode gelöscht werden die Elemente in den Papierkorb, anstatt Sie dauerhaft löschen verschoben werden.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```
DELETE /me/drive/items/{item-id}
DELETE /me/drive/root:/{item-path}
DELETE /groups/<id>/drive/items/<item-id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |
| If-Match-      | String | Wenn diese Anforderungsheader enthalten und bereitgestellten eTag (oder cTag) nicht das aktuelle Tag für das Element entspricht eine `412 Precondition Failed` Antwort zurückgegeben wird, und das Element wird nicht gelöscht werden. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="example"></a>Beispiel

Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.

<!-- {
  "blockType": "request",
  "name": "delete-item"
}-->
```
DELETE /me/drive/items/{item-id}
```

## <a name="response"></a>Antwort

Wenn erfolgreich ist, dieses Anrufs gibt eine `204 No Content` Antwort an, dass diese Ressource wurde gelöscht und gab es nothing zurückgegeben.

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Delete item"
}-->
