# <a name="add-a-member"></a>Hinzufügen eines Mitglieds

Verwenden Sie diese API zum Hinzufügen eines Mitglieds (Benutzer oder Gruppe), um eine administrative Einheit.

`NOTE: Currently it's only possible to add one member at a time to an administrative unit.`

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /administrativeUnits/<id>/members/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung eines [Benutzers](../resources/user.md), [Gruppe](../resources/group.md) oder [DirectoryObject](../resources/directoryObject.md) hinzugefügt werden soll.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es werden keine etwas in der Antworttext zurückgegeben.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
POST https://graph.microsoft.com/beta/administrativeUnits/<id>/members/$ref
Content-type: application/json
Content-length: 109

{
  "@odata.id":"https://graph.microsoft.com/beta/groups/<id>"
}

```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der die `id` des Objekts [Benutzer](../resources/user.md) oder eine [Gruppe](../resources/group.md) hinzufügen möchten.

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
 
```http
HTTP/1.1 204 No Content
```
