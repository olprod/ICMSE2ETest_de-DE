# <a name="working-with-webhooks-in-microsoft-graph"></a>Arbeiten mit Webhooks in Microsoft Graph

Die Microsoft Graph-REST-API verwendet einen Webhook Mechanismus zum Übermitteln von Benachrichtigungen an Clients. Ein Client ist ein Webdienst, der den eigenen URL Erhalt von Benachrichtigungen konfiguriert. Client-apps verwenden Benachrichtigungen, um deren Status nach Änderungen zu aktualisieren.

Verwenden die Microsoft Graph-REST-API, kann eine app Änderungen auf die folgenden Ressourcen abonnieren:

* Meldungen
* Ereignisse
* Kontakte
* Gruppe Unterhaltungen

Nachdem Microsoft Graph die Abonnement-Anforderung annimmt, legt es Benachrichtigungen im Abonnement angegebenen URL. Die app führt dann die entsprechende Aktion entsprechend der Geschäftslogik. Angenommen, ruft es weitere Daten, Updates Cache und Ansichten usw. ab.

Apps sollten ihren Abonnements erneuern, bevor diese ablaufen. Sie können auch jederzeit So beenden Sie die erste Benachrichtigungen melden Sie sich ab.

Finden Sie die folgenden Codebeispiele in GitHub ein.

* [Microsoft Graph Webhooks Beispiel für Node.js](https://github.com/OfficeDev/Microsoft-Graph-Nodejs-Webhooks)
* [Microsoft Graph Webhooks Beispiel für ASP.NET](https://github.com/OfficeDev/Microsoft-Graph-ASPNET-Webhooks)

Betrachten wir nun die Abonnementprozess.

# <a name="creating-a-subscription"></a>Erstellen eines Abonnements

Erstellen eines Abonnements ist der erste Schritt zum Empfangen von Benachrichtigungen für eine Ressource zu starten. Der Anmeldevorgang lautet wie folgt:

1. Der Client sendet eine Anforderung Abonnement (POST) für eine bestimmte Ressource.
2. Microsoft Graph überprüft, ob die Anforderung.
  * Wenn die Anforderung gültig ist, sendet Microsoft Graph ein Token Validation an die URL für die Benachrichtigung.
  * Wenn die Anforderung ungültig ist, sendet Microsoft Graph eine Fehlerantwort mit Code und Details.
3. Der Client sendet das Token Validation an Microsoft Graph zurück.

Client muss die Abonnement-ID zum Korrelieren einer benachrichtigungs mit dem entsprechenden Abonnement speichern.

## <a name="characteristics-of-subscriptions"></a>Merkmale von Abonnements

Sie können Abonnements für Ressourcen wie Nachrichten, Ereignisse und Kontakte erstellen.

Sie können ein Abonnement für einen bestimmten Ordner erstellen:`https://graph.microsoft.com/v1.0/me/mailfolders('inbox')/messages`

Oder auf eine Ressource auf höchster Ebene:`https://graph.microsoft.com/v1.0/me/messages`

Erstellen eines Abonnements erfordert lesen Bereich auf die Ressource. Beispielsweise abzurufenden Benachrichtigungen Nachrichten, Ihre app-Anforderungen der `mail.read` Berechtigung.

Abonnements laufen ab. Die aktuellen längste Ablaufzeit ist drei Tage minus 9-0 Minuten ab dem Zeitpunkt der Erstellung. Apps müssen vor der Ablaufzeit ihren Abonnements erneuern. Andernfalls müssen sie ein neues Abonnement zu erstellen.

## <a name="notification-url-validation"></a>Benachrichtigung URL-Überprüfung

Microsoft Graph überprüft die URL der Benachrichtigung in einer Abonnement-Anforderung, bevor Sie das Abonnement erstellen. Bei der Prüfung läuft wie folgt ab:

1. Microsoft Graph sendet eine POST-Anforderung an die benachrichtigungs-URL:

  ```
  POST https://{notificationUrl}?validationToken={TokenDefinedByMicrosoftGraph}
  ClientState: {Data sent in ClientState value in subscription request (if any)}
  ```
 
2. Der Client muss die folgenden Merkmale eine Antwort innerhalb von 10 Sekunden bereitstellen:

  * Ein 200 (OK) Statuscode.
  * Der Inhaltstyp muss für nur-Text. 
  * Im Textkörper muss das Microsoft Graph Validierung Token enthalten.

Der Client sollte das Token Validation verwerfen, nach der in der Antwort bereitstellen.

## <a name="subscription-request-example"></a>Abonnement anforderungsbeispiel

```
POST https://graph.microsoft.com/v1.0/subscriptions
Content-Type: application/json
{
  "changeType": "created,updated",
  "notificationUrl": "https://webhook.azurewebsites.net/notificationClient",
  "resource": "/me/mailfolders('inbox')/messages",
  "expirationDateTime": "2016-03-20T11:00:00.0000000Z",
  "clientState": "SecretClientState"
}
```

Die Eigenschaften ChangeType, NotificationUrl, Ressourcen- und ExpirationDateTime sind erforderlich. Finden Sie unter [Ressourcentyp Abonnement](subscription.md) für die Eigenschaftsdefinitionen und Werte. Obwohl ClientState nicht erforderlich ist, müssen Sie ihn zur Einhaltung der unseren empfohlenen Benachrichtigung Abwicklung einfügen.

Wenn erfolgreich ist, Microsoft Graph gibt ein `200 OK` Code und ein [Abonnement](subscription.md) -Objekt im Text.

# <a name="renewing-a-subscription"></a>Erneuern eines Abonnements

Der Client kann ein Abonnement mit einem bestimmten Ablaufdatum von bis zu drei Tagen ab dem Zeitpunkt der Anforderung erneuern. Die ExpirationDateTime-Eigenschaft ist erforderlich.

## <a name="subscription-renewal-example"></a>Abonnement Erneuerung Beispiel

```
PATCH https://graph.microsoft.com/v1.0/subscriptions/<id>;
Content-Type: application/json
{
  "expirationDateTime": "2016-03-22T11:00:00.0000000Z"
}
```

Wenn erfolgreich ist, Microsoft Graph gibt ein `200 OK` Code und ein [Abonnement](subscription.md) -Objekt im Text. Das Abonnementobjekt enthält den neuen ExpirationDateTime-Wert. 

# <a name="deleting-a-subscription"></a>Löschen eines Abonnements

Anhalten des Client kann Empfang von Benachrichtigungen, indem Sie das Abonnement, dessen ID mit löschen

```
DELETE https://graph.microsoft.com/v1.0/subscriptions/<id>
```

Wenn erfolgreich ist, Microsoft Graph gibt ein `204 No Content` Code.

# <a name="notifications"></a>Benachrichtigungen

Der Client gestartet wird, Empfangen von Benachrichtigungen nach dem Erstellen des Abonnements. Microsoft Graph sendet eine POST-Anforderung an die URL der Benachrichtigung, wenn Änderungen auf die Ressource erfolgen. Der Client ruft nur Benachrichtigungen entsprechend dem angegebenen Änderungstyp beispielsweise *erstellt*.

## <a name="notification-properties"></a>Benachrichtigungseigenschaften

Das Notification-Objekt besitzt folgenden Eigenschaften:

* ID - die ID für das Abonnement zu dem diese Benachrichtigung gehört.
* ExpirationDateTime - die Ablaufzeit für das Abonnement.
* ClientState - die ClientState-Eigenschaft im Abonnement für die Anforderung angegeben.
* ChangeType - den Ereignistyp, die die Benachrichtigung ausgelöst hat. Beispielsweise empfangen auf e-Mail *erstellt* oder *aktualisiert* auf Markierens einer Nachricht lesen.
* Ressource – der URI der Ressource relativ zum `https://graph.microsoft.com`. 
* ResourceData - Objekts hängt von der Ressource wird abonniert.  Zum Beispiel für Outlook-Ressourcen:
  * @odata.type-Der OData-Entitätstyp in Microsoft Graph, die das dargestellte Objekt beschreibt.
  * @odata.id-Der OData-Bezeichner des Objekts.
  * @odata.etag-Der HTTP-Entität-Tag, das eine Version des Objekts darstellt.
  * ID: der Bezeichner des Objekts.


> Hinweis: ResourceData gemäß der Id-Wert gilt zum Zeitpunkt die Benachrichtigung in die Warteschlange gestellt wurde. Eine Ressource-Id geändert wird möglicherweise einige Aktionen wie Verschieben einer Nachricht in einen anderen Ordner. 

## <a name="notification-example"></a>Beispiel für Benachrichtigung

Wenn der Benutzer eine e-Mail-Nachricht empfängt, sendet Microsoft Graph eine Benachrichtigung folgendermaßen aus:

```
{
  "value":[
  {
    "id":"<subscription_guid>",
    "expirationDateTime":"\"2016-03-19T22:11:09.952Z\"",
    "clientState":"SecretClientState",
    "changeType":"Created",
    "resource":"Users/<user_guid>@<tenant_guid>/Messages/<long_id_string>",
    "resourceData":
    {
      "@odata.type":"#Microsoft.Graph.Message",
      "@odata.id":"Users/<user_guid>@<tenant_guid>/Messages/<long_id_string>",
      "@odata.etag":"W/\"CQAAABYAAADkrWGo7bouTKlsgTZMr9KwAAAUWRHf\"",
      "Id":"<long_id_string>"
    }
  }
  ]
}
```

Beachten Sie, dass das Value-Objekt eine Liste enthält. Wenn viele in der Warteschlange Benachrichtigungen vorhanden sind, werden Sie von Microsoft Graph in einer einzelnen Anforderung sendet.

## <a name="processing-the-notification"></a>Verarbeitung der benachrichtigungs

Nach dem Starten der Anwendung empfangen von Benachrichtigungen müssen sie die Verarbeitung. Im folgenden sind die minimalen Vorgänge, die Ihre app ausführen müssen, um eine Benachrichtigung zu verarbeiten:

1. Überprüfen der `clientState` Eigenschaft. Die ClientState-Eigenschaft in der Benachrichtigung muss die auswertet, die mit der Abonnement-Anforderung übereinstimmen.
  > Hinweis: Wenn dies nicht erfüllt ist, sollte nicht Sie dies eine Benachrichtigung über eine gültige berücksichtigen. Sie sollten auch untersuchen, in dem die Benachrichtigung stammen und entsprechende Aktion.

2. Aktualisieren Sie Ihre Anwendung basierend auf Ihrer Geschäftslogik.
3. Senden einer `202 - Accepted` Statuscode in Ihre Antwort zu Microsoft Graph. Wenn Microsoft Graph einen 2xx-Klassencode nicht angezeigt wird, wird es Erneutes Senden der Benachrichtigung eine Anzahl von Malen wiederholen.
  > Sie sollten senden eine `202 - Accepted` Status code, auch wenn die ClientState-Eigenschaft eine auswertet, die mit der Abonnement-Anforderung übereinstimmt.

Wiederholen Sie für andere Benachrichtigungen, in der Anforderung.

# <a name="additional-resources"></a>Weitere Ressourcen

* [Ressourcentyp Abonnement](subscription.md)
* [Erhalten-Abonnement](../api/subscription_get.md)
* [Abonnement erstellen](../api/subscription_post_subscriptions.md)
* [Microsoft Graph Webhooks Beispiel für Node.js](https://github.com/OfficeDev/Microsoft-Graph-Nodejs-Webhooks)
* [Microsoft Graph Webhooks Beispiel für ASP.NET](https://github.com/OfficeDev/Microsoft-Graph-ASPNET-Webhooks)
