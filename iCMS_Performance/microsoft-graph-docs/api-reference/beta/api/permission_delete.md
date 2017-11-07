# <a name="delete-permission"></a>DELETE-Berechtigung

Löschen Sie eine Berechtigung. Nur die Berechtigungen, die nicht vererbt werden, können gelöscht werden. Die Eigenschaft **InheritedFrom** muss null sein. Anwendungen können nur Berechtigungen löschen, die sie erstellt haben.


## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
DELETE /me/drive/root/permissions/<id>
DELETE /me/drive/items/<id>/permissions/<id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |
| If-Match-      | string | Wenn diese Anforderungsheader enthalten und bereitgestellten eTag (oder cTag) nicht das aktuelle Tag für das Element entspricht eine `412 Precondition Failed` Antwort zurückgegeben wird, und das Element wird nicht gelöscht werden. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Es folgt ein Beispiel der Anforderung.

<!-- {
  "blockType": "request",
  "name": "delete_permission"
}-->
```http
DELETE /me/drive/root/permissions/<id>
```

##### <a name="response"></a>Antwort

Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": false
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Delete permission"
}-->
