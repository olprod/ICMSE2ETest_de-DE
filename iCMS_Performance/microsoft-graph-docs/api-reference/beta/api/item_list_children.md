# <a name="list-children-of-a-driveitem"></a>Untergeordnete Objekte auflisten von einer driveItem

Elemente mit der Ordnereigenschaft können untergeordnete Elemente enthalten. Diese API Listet den Inhalt einer **DriveItem des** `children` Auflistung mit dem Stamm DriveItem, DriveItem-ID oder Pfad.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
```http
GET /me/drive/root/children
GET /me/drive/items/{item-id}/children
GET /me/drive/root:/{item-path}:/children
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer {Token}. Erforderlich.                                                                                                                                |
| If-none-match | String | Wenn diese Kopfzeile der Anforderung enthalten ist und bereitgestellt eTag (oder cTag) das aktuelle Tag für die Datei entspricht ein `HTTP 304 Not Modified` Antwort zurückgegeben wird. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.

##### <a name="request"></a>Anforderung
Es folgt eine Beispiel für eine Anforderung der DriveItems am Stamm der angemeldeten Benutzer OneDrive zurückgegeben.

<!-- {
  "blockType": "request",
  "name": "get_children"
}-->
```http
GET /me/drive/root/children
```

## <a name="response"></a>Antwort

Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {"name": "myfile.jpg", "size": 2048, "file": {} },
    {"name": "Documents", "folder": { "childCount": 4} },
    {"name": "Photos", "folder": { "childCount": 203} },
    {"name": "my sheet(1).xlsx", "size": 197 }
  ],
  "@odata.nextLink": "https://..."
}
```

**Hinweis:** Wenn eine Auflistung die standardmäßigen Seitengröße (200 Elemente) überschreitet die **@odata.nextLink** -Eigenschaft ist in der Antwort an, dass weitere Elemente verfügbar sind, und geben Sie die Anforderung-URL für die nächste Seite Elemente zurückgegeben wurde.

Sie können das Seitenformat über [optionale Abfragezeichenfolge-Parametern](https://dev.onedrive.com/odata/optional-query-parameters.htm)steuern.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List the children of an item.",
  "keywords": "list,children,collection",
  "section": "documentation",
  "tocPath": "OneDrive/DriveItem/List children"
} -->
