# <a name="search-for-an-item"></a>Suche nach einem Element

Suchen Sie die Hierarchie der Elemente für Elemente mit eine Abfrage übereinstimmen. Sie können Suchen und/oder Nachrichtensymbol Filterergebnissen der Elemente Ihrer app finden.

Die Suche gibt übereinstimmende Ergebnisse zurück, aus dem Element in die URL und alle untergeordneten Elemente des betreffenden Elements angegeben. Filtern von Works in der Auflistung der Elemente zurückgegeben, kann entweder alle untergeordneten Elemente, bei der Suche oder nur die unmittelbar untergeordneten Elemente verwenden, wenn Sie eine Auflistung verwenden.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```
GET /me/drive/root/search(q='vacation')
GET /me/drive/items/{item-id}/search(q='vacation')
GET /me/drive/root:/{item-path}:/search(q='vacation')
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

#### <a name="function-parameters"></a>Funktionsparameter

| Name | Wert  | Beschreibung                                                                                                                          |
|:-----|:-------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `q`  | string | Der Abfragetext, der für die Suche nach Elementen verwendet wird. Werte möglicherweise über mehrere Felder, einschließlich Dateiname, Metadaten und der Inhalt der Datei abgeglichen wird. |

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.

##### <a name="request"></a>Anforderung

Es folgt ein Beispiel für die Anforderung des angemeldeten Benutzers OneDrive suchen
<!-- {
  "blockType": "request",
  "name": "item_search"
}-->
```http
GET /me/drive/root/search(q='{search-query}')
```

##### <a name="response"></a>Antwort
Diese Methode gibt ein Objekt mit einem Array von [DriveItems](../resources/driveitem.md) , die den Suchkriterien entsprechen. Wenn keine Elemente gefunden wurden, wird ein leeres Array zurückgegeben.

Wenn es sind zu viele Ergebnisse die Antwort ausgelagert werden wird und eine **@odata.nextLink** -Eigenschaft enthält eine URL zu der nächsten Seite der Suchergebnisse. Sie können die `top` Abfrage Parameter, um die Anzahl der Elemente in der Seite angeben.

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
      {
        "id": "0123456789abc!123",
        "name": "Vacation photos",
        "folder": {},
        "searchResult": { "onClickTelemetryUrl": "https://bing.com/0123456789abc!123" }
      },
      {
        "id": "0123456789abc!456",
        "name": "Summer Vacation Rentals.docx",
        "file": {},
        "searchResult": { "onClickTelemetryUrl": "https://bing.com/0123456789abc!456" }
      }
    ],
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/drive/root/search(query='vacation')&skipToken=1asdlnjnkj1nalkm!asd"
}
```

## <a name="remarks"></a>Hinweise

**Hinweis:** In OneDrive für Unternehmen und SharePoint gibt suchen nicht die folgenden Eigenschaften zurück:

* `parentReference`


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item: search",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Items/Search items"
}-->
