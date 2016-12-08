# <a name="list-members"></a>Mitglieder der Liste

Verwenden Sie diese API zum Abrufen der Mitglieder Liste (Benutzer und Gruppen) in eine administrative Einheit.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.Read.All* oder *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*.

## <a name="http-request"></a>HTTP-Anforderung

```http
GET /administrativeUnits/<id>/members
GET /administrativeUnits/<id>/members/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und eine Auflistung von [Benutzer](../resources/user.md) und/oder [Gruppe](../resources/group.md) von Objekten im Antworttext.  Stattdessen, wenn Sie ablegen `$ref` am Ende der Anforderung, die Antwort enthält eine Auflistung von `@odata.id` Links/URLs auf die Mitglieder.

## <a name="examples"></a>Beispiele
##### <a name="list-member-objects"></a>Liste diemember-Objekte
Das folgende Anforderung werden die Member der administrative Einheit, zurückgeben eine Auflistung von Benutzern und/oder Gruppen aufgelistet.

```http
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members
```

Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
 
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "value":[
    {
      "@odata.type":"#microsoft.graph.user",
      "id":"492c5308-59fd-4740-9c83-4b3db07a6d70"
      "accountEnabled":true,
      "businessPhones":[],
      "companyName":null,
      "displayName":"Demo User"
    },
    {
      "@odata.type":"#microsoft.graph.group",
      "id":"07eaa5c7-c9b6-45cf-8ff7-3147d5122caa",
      "description":"This group is the best ever",
      "displayName":"Awesome group"
    }
  ]
}
```

##### <a name="list-member-references"></a>Elementverweise Liste
Die folgende Anforderung wird Auflisten der Memberverweise die administrative Einheit, eine Auflistung von zurückgeben `@odata.id` Verweise auf die Elemente.
```
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members/$ref
```
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
 
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "value":[
    {
      "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/492c5308-59fd-4740-9c83-4b3db07a6d70"
    },
    {
      "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/07eaa5c7-c9b6-45cf-8ff7-3147d5122caa"
    }
  ]
}
```
