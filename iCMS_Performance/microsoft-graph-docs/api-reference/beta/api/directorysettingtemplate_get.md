# <a name="get-a-directory-setting-template"></a>Eine Verzeichnis Einstellung Vorlage abrufen

Verzeichnis Einstellung Vorlage stellt eine Vorlage der Einstellungen aus denen Einstellungen innerhalb einer mandantenstruktur erstellt werden können. Dieser Vorgang ermöglicht das Abrufen der Eigenschaften des DirectorySettingTemplate-Objekts, einschließlich der verfügbaren Einstellungen und Standardwerte.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.Read.All* oder *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /directorySettingTemplates/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [DirectorySettingTemplate](../resources/directorysettingtemplate.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_directorysettingtemplate"
}-->
```http
GET https://graph.microsoft.com/beta/directorySettingTemplates/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directorySettingTemplate"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 270

{
  "id": "id-value",
  "displayName": "displayName-value",
  "description": "description-value",
  "values": [
    {
      "name": "name-value",
      "type": "type-value",
      "defaultValue": "defaultValue-value",
      "description": "description-value"
    }
  ],
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get directorySettingTemplate",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->