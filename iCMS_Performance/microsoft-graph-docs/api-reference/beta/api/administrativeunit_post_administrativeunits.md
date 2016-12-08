# <a name="create-administrativeunit"></a>Erstellen von administrativeUnit

Verwenden Sie diese API, um eine neue [AdministrativeUnit](../resources/administrativeunit.md)erstellen.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /administrativeUnits

```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|
## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [AdministrativeUnit](../resources/administrativeunit.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [AdministrativeUnit](../resources/administrativeunit.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_administrativeunit_from_administrativeunits"
}-->
```http
POST https://graph.microsoft.com/beta/administrativeUnits
Content-type: application/json
Content-length: 150

{
  "administrativeUnit": {
    "displayName": "displayName-value",
    "description": "description-value",
    "visibility": "visibility-value"
  }
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [AdministrativeUnit](../resources/administrativeunit.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.administrativeunit"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 172

{
  "administrativeUnit": {
    "displayName": "displayName-value",
    "description": "description-value",
    "visibility": "visibility-value",
    "id": "id-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create administrativeUnit",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->