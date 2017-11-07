# <a name="get-a-member"></a>Abrufen eines Elements

Verwenden Sie diese API, um ein bestimmtes Element (Benutzer oder Gruppe) in eine administrative Einheit abzurufen.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.Read.All* oder *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*.

## <a name="http-request"></a>HTTP-Anforderung

```http
GET /administrativeUnits/<id>/members/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und einen [Benutzer](../resources/user.md) oder eine [Gruppe](../resources/group.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members/<id>
```

##### <a name="response"></a>Antwort
Hier ist ein Beispiel für die Respone. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "@odata.type":"#microsoft.graph.user",
  "id":"492c5308-59fd-4740-9c83-4b3db07a6d70"
  "accountEnabled":true,
  "businessPhones":[],
  "companyName":null,
  "displayName":"Demo User"
}
```