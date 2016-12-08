# <a name="message-send"></a>Meldung: Senden

Senden Sie eine Nachricht im Ordner "Entwürfe". Die Entwurf einer Nachricht kann eine neue Nachricht Entwurf, Antwort Entwurf, allen Antworten-Entwurf oder eine forward Entwurf sein. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Mail.Send*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/send
POST /users/<id | userPrincipalName>/messages/<id>/send
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es werden keine etwas in der Antworttext zurückgegeben.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "message_send"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/<id>/send
```

##### <a name="response"></a>Antwort

Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: send",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
