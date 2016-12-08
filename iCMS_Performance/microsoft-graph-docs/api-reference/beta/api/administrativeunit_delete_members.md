# <a name="remove-a-member"></a>Entfernen eines Mitglieds

Verwenden Sie diese API zum Entfernen eines Mitglieds (Benutzer oder Gruppe) über eine administrative Einheit.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /administrativeUnits/<id>/members/<id>/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung. Im nachfolgenden Beispiel id1 stellt den Bezeichner für die administrative Einheit Ziel und id2 stellt den eindeutigen Bezeichner für die Member Benutzer oder eine Gruppe aus der gerichteter administrative Einheit entfernt werden soll. 

```http
DELETE https://graph.microsoft.com/beta/administrativeUnits/<id1>/members/<id2>/$ref
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
 
```http
HTTP/1.1 204 No Content
```
