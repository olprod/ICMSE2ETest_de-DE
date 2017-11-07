# <a name="move-an-item"></a>Verschieben eines Elements

Aktualisieren des übergeordneten Ordners für ein Element durch ID oder Pfad. Wenn ein Element verschieben möchten, aktualisieren Sie dessen ParentReference-Eigenschaft.

Sie können auch ein Element in einen anderen Ordner verschieben, durch die **parentInfo.id** oder **parentInfo.path** -Eigenschaft auf die ID des übergeordneten Ziel aktualisieren.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

```http
PATCH /me/drive/items/{item-id}
PATCH /me/drive/root:/{item-path}
PATCH /groups/<id>/drive/<item-id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                         |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                           |
| If-Match-      | String | Wenn diese Anforderungsheader enthalten und bereitgestellten eTag (oder cTag) nicht das aktuelle eTag für den Ordner entspricht ein `412 Precondition Failed` Antwort zurückgegeben wird. |


## <a name="request-body"></a>Anforderungstext
Geben Sie den neuen Wert für die **ParentReference** -Eigenschaft im Textkörper Anforderung.
Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

**Hinweis:** Beim Verschieben von Elementen in den Stamm des einer OneDrive kann nicht verwendet werden die `"id:" "root"` Syntax. Sie müssen entweder die tatsächliche ID des Stammordners verwenden, oder verwenden Sie `{"path": "/drive/root"}` für den übergeordneten Verweis.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [Artikel](../resources/driveitem.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
Dieses Beispiel verschiebt einen Ordner in einen neuen übergeordneten Pfad.

<!-- {
  "blockType": "request",
  "name": "update_item"
}-->
```http
PATCH /drive/items/{item-id}
Content-type: application/json

{
    "name": "new-item-name",
    "parentReference" : {"path": "/drive/root:/Documents"}
}
```

## <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "0123456789abc",
    "name": "BFolder",
    "folder": { "childCount": 3 }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Move item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
