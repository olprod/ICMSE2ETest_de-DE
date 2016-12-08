# <a name="list-workingwith"></a>Liste arbeiten

Berechnete Insight für die Liste der Benutzer, denen ein Benutzer mit gearbeitet hat.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Users.Read.All*

## <a name="http-request"></a>HTTP-Anforderung
```http
GET /me/workingWith
GET /users/<id | userPrincipalName>/workingWith
GET /drive/root/createdByUser/workingWith
GET /drive/root/lastModifiedByUser/workingWith
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile         | Wert                      |
|:---------------|:---------------------------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp   | Application/json           |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Bei erfolgreicher gibt diese Methode einen 200 OK-Antwortcode und eine Auflistung von [Benutzerobjekten](../resources/user.md) in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
```http
GET https://graph.microsoft.com/beta/me/workingWith
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 98

{
  "id": "id-value",
  "preferredName": "preferredName-value",
  "Email": "Email-value",
}
```