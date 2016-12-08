# <a name="create-a-directory-setting-on-groups"></a>Erstellen Sie eine Einstellung für die Verzeichnis auf Gruppen

Verwenden Sie diese API, um eine neue Einstellung Verzeichnis für die Gruppe zu erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/settings
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Verzeichnisberechtigungen](../resources/directorysetting.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Code und [Verzeichnisberechtigungen](../resources/directorysetting.md) Antwortobjekt im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_directorysetting_from_group"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/settings
Content-type: application/json
Content-length: 222

{
  "directorySetting": {
    "displayName": "displayName-value",
    "templateId": "templateId-value",
    "values": [
      {
        "name": "name-value",
        "value": "value-value"
      }
    ]
  }
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Verzeichnisberechtigungen](../resources/directorysetting.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directorySetting"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 244

{
  "directorySetting": {
    "id": "id-value",
    "displayName": "displayName-value",
    "templateId": "templateId-value",
    "values": [
      {
        "name": "name-value",
        "value": "value-value"
      }
    ]
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create directorySetting",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->