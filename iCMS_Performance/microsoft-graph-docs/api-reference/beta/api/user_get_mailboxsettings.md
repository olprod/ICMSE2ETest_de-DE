# <a name="get-automatic-reply-settings"></a>Abrufen von Einstellungen für automatische Antworten

Rufen Sie die Einstellungen für das Postfach des Benutzers. Einschließlich der Einstellungen für automatische Antworten (benachrichtigen Personen automatisch beim Empfang von e-Mails), Gebietsschema (Sprache und Land/Region) und zur Zeitzone.

Sie können alle postfacheinstellungen anzeigen oder, spezielle Einstellungen erhalten möchten.

## <a name="prerequisites"></a>Voraussetzungen
Der **Bereich** ist erforderlich, um diese API ausführen: *Mailboxsettings.ReadWrite*  

## <a name="http-request"></a>HTTP-Anforderung
Um alle postfacheinstellungen abzurufen, die Einstellungen für automatische Antworten enthalten.
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailboxSettings
GET /users/<id|userPrincipalName>/mailboxSettings
```

Zum Abrufen von bestimmter Einstellungen - antwortet nur die automatische beispielsweise über Einstellungen, Gebietsschema und Zeitzone.
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailboxSettings/automaticRepliesSetting
GET /users/<id|userPrincipalName>/mailboxSettings/automaticRepliesSetting

GET /me/mailboxSettings/language
GET /users/<id|userPrincipalName>/mailboxSettings/language

GET /me/mailboxSettings/timeZone
GET /users/<id|userPrincipalName>/mailboxSettings/timeZone
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
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und eine der folgenden angeforderten Objekte im Antworttext:

- [MailboxSettings](../resources/mailboxsettings.md) -Objekts
- [AutomaticRepliesSetting](../resources/automaticRepliesSetting.md) -Objekts
- [LocaleInfo](../resources/localeinfo.md) -Objekts
- String (für **TimeZone**)

## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1
Im erste Beispiel ruft alle postfacheinstellungen des Postfachs des angemeldeten Benutzers, die Einstellungen für automatische Antworten, Zeitzone und spracheinstellungen umfassen.
<!-- {
  "blockType": "request",
  "name": "get_mailboxsettings_1"
}-->
```http
GET https://graph.microsoft.com/beta/me/mailboxSettings
```
##### <a name="response-1"></a>Antwort 1
Die Antwort enthält alle postfacheinstellungen. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.mailboxSettings"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "Scheduled",
        "externalAudience": "All",
        "scheduledStartDateTime": {
            "dateTime": "2016-03-14T07:00:00.0000000",
            "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
            "dateTime": "2016-03-28T07:00:00.0000000",
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

##### <a name="request-2"></a>Anfordern von 2
Im zweiten Beispiel wird insbesondere die Einstellungen für automatische Antworten des Postfachs des angemeldeten Benutzers.
<!-- {
  "blockType": "request",
  "name": "get_mailboxsettings_2"
}-->
```http
GET https://graph.microsoft.com/beta/me/mailboxSettings/automaticRepliesSetting
```
##### <a name="response-2"></a>Antwort 2
Die Antwort enthält nur die Einstellungen für automatische Antworten. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.automaticRepliesSetting"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/api/beta/$metadata#Me/mailboxSettings/automaticRepliesSetting",
    "status": "alwaysEnabled",
    "externalAudience": "None",
    "scheduledStartDateTime": {
        "dateTime": "2016-03-19T02:00:00.0000000",
        "timeZone": "UTC"
    },
    "scheduledEndDateTime": {
        "dateTime": "2016-03-20T02:00:00.0000000",
        "timeZone": "UTC"
    },
    "internalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "externalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
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