# <a name="get-subscription"></a>Erhalten-Abonnement

Abrufen der Eigenschaften und die Beziehungen eines Abonnements.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche**, je nach der Zielressource sind erforderlich, um diese API ausführen: *Mail.Read*, *Calendars.Read*, *Contacts.Read*, *Group.Read.All* oder *Files.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /subscriptions/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [Abonnement](../resources/subscription.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "get_subscription"
}-->
```http
GET https://graph.microsoft.com/beta/subscriptions/<id>
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.subscription"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 252

{
  "id":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/messages",
  "changeType":"created,updated",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "expirationDateTime":"2016-11-20T18:23:45.9356913Z"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
