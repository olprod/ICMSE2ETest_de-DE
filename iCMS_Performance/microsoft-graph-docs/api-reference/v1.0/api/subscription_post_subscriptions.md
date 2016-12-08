# <a name="create-subscription"></a>Abonnement erstellen

Abonniert Listener-Anwendung zum Empfangen von Benachrichtigungen, wenn Daten auf das Microsoft Graph ändert.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche**, je nach der Zielressource sind erforderlich, um diese API ausführen: *Mail.Read*, *Calendars.Read*, *Contacts.Read* oder *Group.Read.All* 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->

```http
POST /subscriptions

```

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |


## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `201, Created` Antwortcode und ein [Abonnement](../resources/subscription.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung zum Senden einer Benachrichtigung, wenn der Benutzer eine neue e-Mail-Nachrichten empfängt.
<!-- {
  "blockType": "request",
  "name": "create_subscription_from_subscriptions"
}-->
```http
POST https://graph.microsoft.com/v1.0/subscriptions
Content-type: application/json

{
   "changeType": "created,updated",
   "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
   "resource": "me/mailFolders('Inbox')/messages",
   "expirationDateTime":"2016-11-20T18:23:45.9356913Z",
   "clientState": "subscription-identifier"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Abonnement](../resources/subscription.md) -Objekts.
Das Feld *ClientState* ist optional.

##### <a name="resources-examples"></a>Beispiele für Ressourcen
Folgende sind gültige Werte für die Ressourceneigenschaft des Abonnements:

| Ressourcentyp | Beispiele |
|:------ |:----- |
|E-Mails|Me/Mailfolders('inbox')/Nachrichten<br />Me / Nachrichten|
|Kontakte|Me / Kontakte|
|Kalender|Me / Ereignisse|
|Unterhaltungen|Groups('*{ID}*')-Unterhaltungen|

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.subscription"
} -->
```http
HTTP/1.1 201 Created

{
  "id":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/mailFolders('Inbox')/messages",
  "changeType":"created, updated",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "expirationDateTime":"2016-11-20T18:23:45.9356913Z"
}
```
## <a name="subscription-validation"></a>Abonnement-Validierung
Um zur Vermeidung von falschen Abonnements Umleiten von Benachrichtigungen zu beliebigen URLs muss Abonnement Benachrichtigung Endpunkts zum Reagieren auf eine Anforderung zur Überprüfung. Während der Verarbeitung von der `POST` an die `/subscriptions` Endpunkt, die Microsoft Graph sendet eine `POST` zurück zum Anfordern Ihrer `notificationUrl` im folgenden Format: 
```http
POST https://webhook.azurewebsites.net/api/send/myNotifyClient?validationToken=<token>
```
Der Benachrichtigung Endpunkt eine 200 Antwort mit dem Wert des senden muss `<token>` als Textkörper und einem Inhaltstyp des `text/plain`, siehe unten, innerhalb von 10 Sekunden, andernfalls wird die Anforderung zum Erstellen eines verworfen.
```http
HTTP/1.1 200 OK
Content-type: text/plain
Content-length: 7
<token>
```
##### <a name="notification-payload"></a>Benachrichtigung Nutzlast
Wenn sendet die abonnierten Ressource geändert wird, die Webhooks-Funktion eine Benachrichtigung an Ihre Benachrichtigung URL mit der folgenden Nutzlast.  Der Benachrichtigung Endpunkt muss eine Antwort von 200 oder 204 mit keinen Antworttext innerhalb von 30 Sekunden, die andernfalls senden, den der Benachrichtigung Versuch wesentlich höheren Intervallen wiederholt.  Dienste, die konsistent 30 Sekunden oder länger dauern gedrosselt werden können und kargere Benachrichtigung Satz erhalten.

Dienste können auch eine 422 Antwort aus einer Benachrichtigung zurückgeben, in dem Fall das Abonnement automatisch gelöscht und der Stream der Benachrichtigungen wird zum Stillstand kommen.

Je nach den abonnierten Ressource kann eine zusätzliche ResourceData Feld zusätzliche Informationen bereitstellen.

```http
{
   "value":[
      {
         "subscriptionId":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
         "subscriptionExpirationDateTime":"2015-11-20T18:23:45.9356913Z",
         "clientState":"subscription-identifier",
         "changeType":"Created",
         "resource":"Users/ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4/messages/AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA=",
         "resourceData":{
            "@odata.type":"#Microsoft.Graph.Message",
            "@odata.id":"Users/ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4/messages/AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA=",
            "@odata.etag":"W/\"CQAAABYAAACoeN6SYXGLRrvRm+CYrrfQAACvvGdb\"",
            "Id":"AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA="
         }
      }
   ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
