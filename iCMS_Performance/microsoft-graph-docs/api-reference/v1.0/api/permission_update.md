# <a name="update-permission"></a>Update-Berechtigung

Aktualisieren Sie die Eigenschaften eines vorhandenen Permission-Objekts. Nur die Rollen-Eigenschaft kann geändert werden.

## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "ignored" } -->
```http
PATCH /me/drive/root/permissions/<id>
PATCH /me/drive/items/<id>/permissions/<id>
PATCH /groups/<group-id>/drive/items/<item-id>/permissions/<id>
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich.                                                                                                                                                                         |
| If-Match-      | string | Wenn diese Anforderungsheader enthalten und bereitgestellten eTag (oder cTag) nicht das aktuelle Tag für das Element entspricht eine `412 Precondition Failed` Antwort zurückgegeben wird, und das Element wird nicht gelöscht werden. |


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   | Beschreibung                   |
|:-------------|:-------|:------------------------------|
| **Rollen**    | String | Ein Array von Berechtigungen. |


## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierten [Permission](../resources/permission.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_permission"
}-->
```http
PATCH /me/drive/items/<item-id>/permissions/<id>
Content-type: application/json

{
  "roles": [ "read" ]
}
```
##### <a name="response"></a>Antwort

Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "grantedTo": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12"
    }
  },
  "id": "1",
  "roles": [ "read" ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Update permission"
}-->
