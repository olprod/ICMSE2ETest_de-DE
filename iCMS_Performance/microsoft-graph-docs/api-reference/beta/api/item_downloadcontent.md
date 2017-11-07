# <a name="download-the-contents-of-a-driveitem"></a>Laden Sie den Inhalt einer driveItem

Laden Sie den Inhalt für eine DriveItem. Nur DriveItem mit der **Datei** -Eigenschaft kann heruntergeladen werden.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/{item-id}/content
GET /me/drive/root:/{item-path and filename}:/content
GET /groups/<id>/drive/items/<item-id>/content
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Wert  | Beschreibung                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                |
| If-none-match | String | Wenn diese Kopfzeile der Anforderung enthalten ist und bereitgestellt eTag (oder cTag) das aktuelle Tag für die Datei entspricht ein `HTTP 304 Not Modified` Antwort zurückgegeben wird. |
| Range         | Bereich  | Bereich von Bytes, die in der Antwort zurückgegeben.                                                                                                                 |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.


<!-- { "blockType": "request", "name": "driveitem-download-contents" } -->
```http
GET /me/drive/items/{item-id}/content
```

##### <a name="response"></a>Antwort
Gibt eine `302 Found` Antwort auf eine zuvor authentifizierte Download-URL für die Datei umleiten. Dies ist die gleiche URL verfügbar über die `@content.downloadUrl` Eigenschaft für ein Element.

Um den Inhalt der Datei herunterzuladen Ihrer Anwendung benötigen, führen die `Location` Header in der Antwort.

Vor dem authentifizierten Download URLs sind nur für einen kurzen Zeitraum (einige Minuten) gültig und erfordern kein `Authorization` Header herunterladen.

<!-- { "blockType": "response", "@odata.type": "stream" } -->
```http
HTTP/1.1 302 Found
Location: https://b0mpua-by3301.files.1drv.com/y23vmagahszhxzlcvhasdhasghasodfi
```

## <a name="range-downloads"></a>Bereichs-downloads

Wenn einen partiellen Bereich eines Elements herunterladen möchten, verwenden Sie den Bereich HTTP-Header gemäß [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt). Beachten Sie, dass Sie nach Erhalt den Range-Header an die HTTP-Anforderung anhängen müssen die `302 Found`.

<!-- { "blockType": "request", "name": "driveitem-get-partial-content" } -->
```http
GET https://b0mpua-by3301.files.1drv.com/y23vmag
Range: bytes=0-1023
```

Dadurch wird zurückgegeben, ein `HTTP 206 Partial Content` Antwort im Bereich Anforderung von Bytes aus der Datei. Wenn der Bereich kann nicht generiert werden der Range-Header ignoriert werden und eine `HTTP 200` Antwort mit den gesamten Inhalt der Datei zurückgegeben.

<!-- { "blockType": "response", "@odata.type": "stream" } -->
```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 0-1023/2048

<first 1024 bytes of file>
```

## <a name="notes"></a>Hinweise  

Wenn Sie Inhalt des Elements, dessen/Content anfordert herunterladen-Eigenschaft, müssen Sie den Authorization-Header angeben, um Zugriff auf herunterladen erteilt werden. Zurückgeben der Antwort würde normalerweise eine `302` umleiten, um die URL, in dem die Datei heruntergeladen werden kann. Diese URL erfordert ist vorab authentifiziert und keine den Authorization-Header.


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Download item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Download file"
}-->
