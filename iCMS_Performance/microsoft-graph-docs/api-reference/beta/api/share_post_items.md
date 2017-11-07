# <a name="create-item"></a>Element erstellen

Verwenden Sie diese API, um ein neues Element zu erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen:
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /shares/<id>/items

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Item](../resources/driveitem.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Element](../resources/driveitem.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_driveitem_from_share"
}-->
```http
POST https://graph.microsoft.com/beta/shares/<id>/items
Content-type: application/json
Content-length: 504

{
  "driveItem": {
    "content": "content-value",
    "createdBy": {
      "application": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "device": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "user": {
        "displayName": "displayName-value",
        "id": "id-value"
      }
    },
    "createdDateTime": "datetime-value",
    "cTag": "cTag-value",
    "description": "description-value",
    "eTag": "eTag-value"
  }
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [DriveItem](../resources/driveitem.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 504

{
  "driveItem": {
    "content": "content-value",
    "createdBy": {
      "application": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "device": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "user": {
        "displayName": "displayName-value",
        "id": "id-value"
      }
    },
    "createdDateTime": "datetime-value",
    "cTag": "cTag-value",
    "description": "description-value",
    "eTag": "eTag-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
