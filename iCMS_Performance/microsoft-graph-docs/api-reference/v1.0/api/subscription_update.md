# <a name="update-subscription"></a>Update-Abonnement

Erneuern eines Abonnements durch seine Ablaufzeit erweitern.

Abonnements für Ressourcen mit Ablauf Datumsangaben eingeschränkte durch die einzelne Ressourcentypen zur Verfügung.  Damit kann nicht auf die Benachrichtigung verpassen sollte im Vorfeld ihrem Ablaufdatum Abonnements erneuert werden.  Einzelne Ablaufdatum finden Sie unter [Abonnement](../resources/subscription.md) .
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche**, je nach der Zielressource sind erforderlich, um diese API ausführen: *Mail.Read*, *Calendars.Read*, *Contacts.Read* oder *Group.Read.All* 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /subscriptions/<subscriptionId>
```

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [Abonnement](../resources/subscription.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_subscription"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/subscriptions/<subscriptionId>
Content-type: application/json

{
   "expirationDateTime":"2016-11-22T18:23:45.9356913Z"
}
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
  "expirationDateTime":"2016-11-22T18:23:45.9356913Z"
}
```


<!-- {
  "type": "#page.annotation",
  "description": "Update subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
