# <a name="copy-a-driveitem-to-a-new-location"></a>Kopieren einer DriveItem an einen neuen Speicherort

Erstellt eine Kopie einer [DriveItem](../resources/driveitem.md) (einschließlich alle untergeordneten Elemente), oder unter einem neuen Namen unter ein neues übergeordnetes Element.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```
POST /me/drive/items/<id>/copy
POST /me/drive/root:/<path>:/copy
POST /groups/<id>/drive/items/<id>/copy
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.


| Name            | Wert                                          | Beschreibung                                                                                                 |
|:----------------|:-----------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| parentReference | [ItemReference](../resources/itemreference.md) | Optional Verweis auf das übergeordnete Element, dem die Kopie in erstellt wird.                                         |
| name            | string                                         | Optional Der neue Name für die Kopie. Wenn dies nicht enthalten ist, wird der gleiche Namen wie die ursprüngliche verwendet werden.    |

**Hinweis:** Die _ParentReference_ sollte entweder enthalten eine `id` oder `path` jedoch nicht beide. Wenn beide enthalten sind, damit Sie das gleiche Objekt verweisen oder, tritt ein Fehler auf.

## <a name="example"></a>Beispiel

<!-- { "blockType": "request", "name": "copy-item", "scopes": "files.readwrite" } -->
```http
POST /me/drive/items/{item-id}/copy
Content-Type: application/json

{
  "parentReference": {
    "path": "/drive/root:/Documents"
  },
  "name": "foobar.txt"
}
```

## <a name="response"></a>Antwort

Ausführliche Informationen zum Überwachen des Fortschritts des die Kopie nach Annahme der Anforderung zurückgegeben.

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 202 Accepted
```

## <a name="remarks"></a>Hinweise

Kopie wird asynchron abgeschlossen. Die Antwort aus der API wird nur laut der Kopiervorgang angenommen wurde oder abgelehnt, sprechen Sie aufgrund der Zieldateiname wird bereits verwendet. Es ist jedoch keine Möglichkeit zum wissen, wann des Kopiervorgangs abgeschlossen hat.

<!-- {
  "type": "#page.annotation",
  "description": "Create a copy of an existing item.",
  "keywords": "copy existing item",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Copy"
} -->
