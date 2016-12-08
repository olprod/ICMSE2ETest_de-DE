# <a name="list-thumbnails-for-driveitem"></a>Liste von Miniaturansichten für driveItem

Rufen Sie eine Reihe von ThumbnailSet Ressourcen für ein [DriveItem-Objekt](../resources/driveitem.md)ab.

Ein Element in einem Laufwerk kann durch null oder mehrere [ThumbnailSet](../resources/thumbnailset.md) -Objekte dargestellt werden. Jedes **ThumbnailSet** möglich mindestens [**Miniaturansicht**](../resources/thumbnail.md) -Objekte, die Bilder sind, die das Element darstellen. Beispielsweise kann ein **ThumbnailSet** **Miniaturansicht** -Objekte, wie allgemeine Spalten einschließlich enthalten `small`, `medium`, oder `large`.

Es gibt viele Arten Miniaturansichten in OneDrive entwickelt.
Es folgen die häufigsten:

* Aufzählen von verfügbaren Miniaturansichten für ein Element
* Eine einzelne Miniaturansicht für ein Element abrufen
* Abrufen von Inhalten Miniaturansicht
* Abrufen von Miniaturansichten für mehrere Elemente in einer Anforderung
* Abrufen von benutzerdefinierten Miniaturansichten
* Hochladen einer benutzerdefinierten Miniaturansicht für ein Element
* Bestimmen der Miniaturansicht vorhanden ist, wenn eine benutzerdefinierte hochgeladen


## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite


## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root:/{item-path}:/thumbnails
GET /me/drive/items/{item-id}/thumbnails
GET /groups/<id>/drive/items/<item-id>/thumbnails
```
## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [ThumbnailSet](../resources/thumbnailset.md) .

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Es folgt ein Beispiel der Anforderung.

<!-- {
  "blockType": "request",
  "name": "get_thumbnails"
}-->
```http
GET /me/drive/items/<item-id>/thumbnails
```


##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.thumbnailSet",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "id": "0",
      "small": { "height": 64, "width": 96, "url": "https://sn3302files..."},
      "medium": { "height": 117, "width": 176, "url": "https://sn3302files..."},
      "large": { "height": 533, "width": 800, "url": "https://sn3302files..."}
    }
  ]
}
```

## <a name="retrieve-a-single-thumbnail"></a>Abrufen einer einzelnen Miniaturansicht

Rufen Sie die Metadaten für eine einzelne Miniaturansicht und Größe, indem Sie direkt in einer Anforderung stoßen.

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "request", "name": "get-one-thumbnail" } -->
```http
GET /me/drive/items/<item-id>/thumbnails/<thumb-id>/<size>
```

## <a name="path-parameters"></a>Pfad-Parameter

| Name         | Typ   | Beschreibung                                                                         |
|:-------------|:-------|:------------------------------------------------------------------------------------|
| **Element-id**  | string | Der eindeutige Bezeichner für das Element verwiesen wird.                                      |
| **Ziehpunkt-id** | number | Der Index der Miniaturansicht, normalerweise 0 bis 4.                                            |
| **Größe**     | string | Die Größe der Miniaturansicht angefordert. Dies muss einer der standard Größen aufgeführt sein. |


<!-- { "blockType": "response", "@odata.type": "microsoft.graph.thumbnail" } -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "width": 100,
  "height": 100,
  "url": "http://onedrive.com/asd123a/asdjlkasjdkasdjlk.jpg"
}
```

## <a name="retrieve-thumbnail-content"></a>Abrufen von Inhalten Miniaturansicht

Sie können den Inhalt der Miniaturansicht direkt abrufen, durch die **Content** -Eigenschaft der Miniaturansicht anfordern.

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "request", "name":"get-thumbnail-content" } -->
```http
GET /me/drive/items/<item-id>/thumbnails/<thumb-id>/<size>/content
```

## <a name="response"></a>Antwort

Der Webdienst sendet eine Umleitung auf die Miniaturansicht URL.

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 302 Found
Location: https://b0mpua-by3301.files.1drv.com/y23vmagahszhxzlcvhasdhasghasodfi
```

Miniaturansicht URLs sind Cache Safe. Die URL wird geändert, wenn das Element in einer Weise geändert, die eine neue Miniaturansicht wird zu generierenden erforderlich sind.

## <a name="size-values"></a>Der Größenwerte

In dieser Tabelle werden die möglichen Miniaturansichten definiert. Während Sie jede beliebige Größe der Miniaturansicht anfordern können, sind die definierten Werte wahrscheinlich vorhanden und schnell einen Wert zurück:

| Name           | Lösung  | Seitenverhältnis | Beschreibung                                                          |
|:---------------|:------------|:-------------|:---------------------------------------------------------------------|
| `small`        | 96 längsten  | Original     | Kleine, stark komprimierten Miniaturansicht eine quadratische Seitenverhältnis zugeschnitten. |
| `medium`       | Längste 176 | Original     | Der standard Elementgröße für die OneDrive Webansicht zugeschnitten.         |
| `large`        | Längste 800 | Original     | Miniaturansicht mit der längsten Kante, deren Größe auf 800 Pixel.               |


## <a name="remarks"></a>Hinweise

**Hinweis** In OneDrive für Unternehmen und SharePoint:

* Verwenden diese Aufrufe zum Erweitern der Miniaturansichten-Auflistung funktionieren nicht:`GET /drive/root:/{item-path}?expand=children(expand=thumbnails)`
  `GET /drive/items/{item-id}/children?expand=thumbnails`


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get metadata and content for thumbnails of multiple sizes for OneDrive items.",
  "keywords": "thumbnail,content,download,sizes",
  "section": "documentation",
  "tocPath": "OneDrive/Item/List thumbnails"
} -->
