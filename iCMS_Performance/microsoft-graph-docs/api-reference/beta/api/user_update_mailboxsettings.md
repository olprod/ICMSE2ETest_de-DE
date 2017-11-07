# <a name="update-user-mailbox-settings"></a>Aktualisieren von Postfach-benutzereinstellungen

Aktualisieren Sie eine oder mehrere Einstellungen für das Postfach des Benutzers. Einschließlich der Einstellungen für automatische Antworten (benachrichtigen Personen automatisch beim Empfang von e-Mails), Locale oder Zeitzone.

Sie können aktivieren, konfigurieren oder deaktivieren eine oder mehrere der folgenden Einstellungen als Teil des [MailboxSettings](../resources/mailboxsettings.md).

**Hinweis** Erstellen oder löschen eine beliebige Einstellung Postfach.

## <a name="prerequisites"></a>Voraussetzungen
Der **Bereich** ist erforderlich, um diese API ausführen: *Mailboxsettings.ReadWrite*  
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/mailboxSettings
PATCH /users/<id|userPrincipalName>/mailboxSettings
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die relevanten Eigenschaften, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben. Im folgenden sind die schreibbare/aktualisierbare Eigenschaften:

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|automaticRepliesSetting|[automaticRepliesSetting](../resources/automaticrepliessetting.md)|Konfigurationseinstellungen für den Absender einer eingehenden e-Mail mit einer Nachricht vom angemeldeten Benutzer automatisch zu benachrichtigen.|
|language|[localeInfo](../resources/localeinfo.md)|Die Gebietsschemainformationen für den Benutzer, einschließlich der bevorzugten Sprache und Land/Region.|
|Zeitzone|string|Die Standardzeitzone für das Postfach des Benutzers.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortobjekt Code und [MailboxSettings](../resources/mailboxSettings.md) im Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Das folgende Beispiel aktiviert die automatische Antworten für einen Datumsbereich durch Festlegen der folgenden Eigenschaften der Eigenschaft **AutomaticRepliesSetting** : **Status**, **ScheduledStartDateTime** und **ScheduledEndDateTime**.

<!-- {
  "blockType": "request",
  "name": "update_mailboxsettings"
}-->
```http
PATCH https://graph.microsoft.com/api/beta/me/mailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/api/beta/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "Scheduled",
        "scheduledStartDateTime": {
          "dateTime": "2016-03-20T18:00:00.0000000",
          "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
          "dateTime": "2016-03-28T18:00:00.0000000",
          "timeZone": "UTC"
        }
    }
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.mailboxSettings"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/api/beta/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "scheduled",
        "externalAudience": "none",
        "scheduledStartDateTime": {
            "dateTime": "2016-03-20T02:00:00.0000000",
            "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
            "dateTime": "2016-03-28T02:00:00.0000000",
            "timeZone": "UTC"
        },
    "internalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "externalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "timeZone":"UTC",
    "language":{
      "locale":"en-US",
      "displayName":"English (United States)"
    }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get automatic reply settings",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->