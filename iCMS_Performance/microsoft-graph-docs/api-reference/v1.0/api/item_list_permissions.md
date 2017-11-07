# <a name="list-permissions-on-a-driveitem"></a>Berechtigungen für Listen auf einer driveItem

Auflisten die effektiven Berechtigungen eines Elements an.

Berechtigungen können nicht auf Listen von Elementen oder ein einzelnes Element erweitert werden. Sie müssen die Eigenschaft Berechtigungen direkt zugreifen.

## <a name="access-to-permissions"></a>Access-Berechtigungen

Die Berechtigungen-Auflistung enthält möglicherweise vertraulichen Informationen und möglicherweise nicht für alle Aufrufer verfügbar.

* Für den Besitzer des Elements werden alle Berechtigungen zurückgegeben. Dazu gehören Mitbesitzer.
* Für ein Anrufer nicht-Besitzer werden nur die Berechtigungen, die der Anrufer liegen, zurückgegeben.
* Berechtigungseigenschaften, die Secrets enthalten (z. B. `shareId` und `webUrl`) werden nur für Anrufer, die zum Erstellen der Berechtigung können zurückgegeben.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root/permissions
GET /me/drive/items/<id>/permissions
GET /groups/<id>/drive/items/<id>/permissions
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                     |
|:--------------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                       |
| If-none-match | string | Wenn diese Anfrage-Header enthalten ist und das bereitgestellten Etag das aktuelle Etag für das Element entspricht eine `HTTP 304 Not Modified` Antwort zurückgegeben wird. |


## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und Auflistung von Objekten im Antworttext [Berechtigung](../resources/permission.md) .

Effektive Berechtigungen eines Elements können aus zwei Quellen stammen: entweder Berechtigungen direkt auf das Element selbst oder wurden von früheren Versionen des Elements geerbt.

Anrufer können unterscheiden, wenn die Berechtigung geerbt wird oder nicht, indem Sie die **InheritedFrom** -Eigenschaft überprüfen. Diese Eigenschaft ist eine [**ItemReference**](../resources/itemreference.md) Ressource verweisen auf die Vorgänger, dem die Berechtigung geerbt wird.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_permissions"
}-->
```http
GET /me/drive/items/<id>/permissions
```


##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "1",
      "roles": ["write"],
      "link": {
        "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
        "type": "edit"
      }
    },
    {
      "id": "2",
      "roles": ["write"],
      "grantedTo": {
        "user": {
          "id": "5D33DD65C6932946",
          "displayName": "John Doe"
        }
      },
      "inheritedFrom": {
        "driveId": "1234567890ABD",
        "id": "1234567890ABC!123",
        "path": "/drive/root:/Documents" }
    },
    {
      "id": "3",
      "roles": ["write"],
      "link": {
        "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
        "type": "edit",
        "application": {
          "id": "12345",
          "displayName": "TimeTravelPlus"
        }
      }
    }
  ]
}
```

**Hinweis:** Antwortobjekte werden aus Gründen der Übersichtlichkeit gekürzt. Alle Standard-Eigenschaften werden von den eigentlichen Aufruf zurückgegeben.

Einzelheiten zum Abrufen einer Ressource einzelne Berechtigung finden Sie unter [Berechtigung erhalten möchten](permission_get.md) .


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List permissions",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/List permissions"
}-->
