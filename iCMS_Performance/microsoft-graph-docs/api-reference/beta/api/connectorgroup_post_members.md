# <a name="add-connector-to-connectorgroup"></a>Hinzufügen von Connectors zu connectorGroup

Verwenden Sie diese API, um eine Verbindung zu einem ConnectorGroup hinzuzufügen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.ReadWrite.All oder Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /connectorGroups/<id>/members/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Beschreibung|
|:---------------|:----------|
| Autorisierung  | Bearer. Erforderlich|


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der eine Verknüpfung zu einem Objekt [Connector](../resources/connector.md) ein.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Connector](../resources/connector.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_connector_from_connectorgroup"
}-->
```http
POST https://graph.microsoft.com/{ver}/connectorGroups/<id>/members/$ref
Content-type: application/json
Content-length: 104

{
  "@odata.id": "https://graph.microsoft.com/{ver}/connector/<id>"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der eine Verknüpfung zu einer [Connector](../resources/connector.md) -Objekt.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.connector"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 124

{
  "id": "id-value",
  "machineName": "machineName-value",
  "externalIp": "externalIp-value",
  "status": "status-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create connector",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
