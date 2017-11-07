# <a name="create-application"></a>Anwendung erstellen

Verwenden Sie diese API, um eine neue Anwendung erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /applications
```

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer {Token}. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Application](../resources/application.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Anwendung](../resources/application.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_application_from_applications"
}-->
```http
POST https://graph.microsoft.com/beta/applications
Content-type: application/json
Content-length: 717

{
  "addIns": [
      {
        "id": "id-value",
        "type": "type-value",
        "properties": [
          {
            "key": "key-value",
            "value": "value-value"
          }
        ]
      }
    ],
    "appRoles": [
      {
        "allowedMemberTypes": [
          "allowedMemberTypes-value"
        ],
        "description": "description-value",
        "displayName": "displayName-value",
        "id": "id-value",
        "isEnabled": true,
        "origin": "origin-value",
        "value": "value-value"
      }
    ],
    "availableToOtherOrganizations": true,
    "displayName": "displayName-value",
    "errorUrl": "errorUrl-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Application](../resources/application.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.application"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 717

{
  "application": {
    "addIns": [
      {
        "id": "id-value",
        "type": "type-value",
        "properties": [
          {
            "key": "key-value",
            "value": "value-value"
          }
        ]
      }
    ],
    "appId": "appId-value",
    "appRoles": [
      {
        "allowedMemberTypes": [
          "allowedMemberTypes-value"
        ],
        "description": "description-value",
        "displayName": "displayName-value",
        "id": "id-value",
        "isEnabled": true,
        "origin": "origin-value",
        "value": "value-value"
      }
    ],
    "availableToOtherOrganizations": true,
    "displayName": "displayName-value",
    "errorUrl": "errorUrl-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Application",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
