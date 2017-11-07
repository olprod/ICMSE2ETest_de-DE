# <a name="get-a-driveitem-resource"></a>Abrufen einer Ressource driveItem

Rufen Sie die Metadaten für eine DriveItem in ein Laufwerk mithilfe Dateisystempfads oder eindeutige Id ab.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/<item-id>
GET /me/drive/root:/<item-path>
GET /groups/<group-id>/drive/items/<item-id>
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Wert  | Beschreibung                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                |
| If-none-match | String | Wenn diese Anforderungsheader enthalten ist und bereitgestellt eTag (oder cTag) das aktuelle Tag auf die Datei entspricht ein `HTTP 304 Not Modified` Antwort zurückgegeben wird. |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [Element](../resources/driveitem.md) in der Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_item"
}-->
```
GET /me/drive/items/{item-id}
```

##### <a name="response"></a>Antwort
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
  "createdBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "createdDateTime": "2016-03-21T20:01:37Z",
  "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
  "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
  "file": {  },
  "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
  "lastModifiedBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "lastModifiedDateTime": "2016-03-21T20:01:37Z",
  "name": "OneDrive Graph API.docx",
  "parentReference": {
      "driveId": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "id": "01NKDM7HN6Y2GOVW7725BZO354PWSELRRZ",
      "path": "/drive/root:"
  },
  "size": 31679,
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/OneDrive%20Graph%20API.docx"
}
```

## <a name="notes"></a>Hinweise

Sie können die [`expand`](https://dev.onedrive.com/odata/optional-query-parameters.htm#expanding-collections) Abfragen Zeichenfolgenparameter, um die untergeordneten Elemente eines Elements in einem Anruf als beim Abrufen der Metadaten eines Elements enthalten.

## <a name="head-requests"></a>HEAD-Anfragen

In den meisten Fällen verhält sich eine HEAD-Anforderung die gleiche Weise wie eine GET-Anforderung. Es gibt einige Unterschiede:

1. HEAD-Anfragen werden nur Kopfzeilen der entsprechenden GET-Anforderung zurück. Dies ist üblicherweise für eine HEAD-Antwort.
2. HEAD-Anfragen werden nicht automatisch auf einen [Ordner mit Sonderfunktion](../resources/specialfolder.md)bereit.
   Stattdessen, wenn Sie ein Ordner mit Sonderfunktion nicht vorhanden ist, ist ein `404` Fehlermeldung zurückgegeben.

In diesem Beispiel können Sie sehen, dass Anfordern eines Laufwerks der Stammressource mit einfach antwortet `200 OK`.

## <a name="http-request"></a>HTTP-Anforderung

<!-- {"blockType": "request", "name": "head-root"} -->
```
HEAD /me/drive/root
Accept: application/json
```

## <a name="response"></a>Antwort

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true} -->
```
HTTP/1.1 200 OK
Content-Type: application/json
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Get item"
}-->
