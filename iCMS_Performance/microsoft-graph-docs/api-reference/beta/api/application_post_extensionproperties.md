# <a name="create-extensionproperty"></a>ExtensionProperty erstellen

Verwenden Sie diese API, um eine neue ExtensionProperty erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /applications/<id>/extensionProperties

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ExtensionProperty](../resources/extensionproperty.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [ExtensionProperty](../resources/extensionproperty.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_extensionproperty_from_application"
}-->
```http
POST https://graph.microsoft.com/beta/applications/<id>/extensionProperties
Content-type: application/json
Content-length: 231

{
  "extensionProperty": {
    "appDisplayName": "appDisplayName-value",
    "name": "name-value",
    "dataType": "dataType-value",
    "isSyncedFromOnPremises": true,
    "targetObjects": [
      "targetObjects-value"
    ]
  }
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [ExtensionProperty](../resources/extensionproperty.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.extensionproperty"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 253

{
  "extensionProperty": {
    "appDisplayName": "appDisplayName-value",
    "name": "name-value",
    "dataType": "dataType-value",
    "isSyncedFromOnPremises": true,
    "targetObjects": [
      "targetObjects-value"
    ],
    "id": "id-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create extensionProperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->