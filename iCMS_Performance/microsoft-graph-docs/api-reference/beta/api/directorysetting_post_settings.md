# <a name="create-a-directory-setting"></a>Erstellen einer Einstellung directory

Verwenden Sie diese API, um eine neue Einstellung, basierend auf den in DirectorySettingTemplates verfügbaren Vorlagen erstellen. Diese Einstellungen kann auf der Ebene des Mandanten oder auf Objektebene (derzeit nur für Gruppen). Die Anforderung zum Erstellen eines muss EinstellenWerte für alle in der Vorlage definierten Einstellungen angeben. Für die Gruppe-spezifischen Einstellungen kann die Option nur die Einstellung steuern, ob Mitglieder einer Gruppe Gastbenutzer einladen können festgelegt werden. Dies wird dieses Verhalten gesteuert, sobald die Möglichkeit zum Hinzufügen von Gastbenutzern zu einer Gruppe im Allgemeinen verfügbar ist.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /settings
POST /groups/<id>/settings
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Verzeichnisberechtigungen](../resources/directorysetting.md) -Objekts.  Jedoch wird der Anzeigename für die Einstellung basierend auf den Vorlagennamen referenzierten Einstellungen festgelegt werden.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Code und [Verzeichnisberechtigungen](../resources/directorysetting.md) Antwortobjekt im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_directorysetting_from_settings"
}-->
```http
POST https://graph.microsoft.com/beta/settings
Content-type: application/json
Content-length: 222

{
  "templateId": "templateId-value",
  "values": [
    {
      "name": "name-value",
      "value": "value-value"
    }
  ]
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
    "@odata.context": "https://graph.microsoft.com/stagingbeta/$metadata#settings/$entity",
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