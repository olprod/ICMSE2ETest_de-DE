# <a name="message-forward"></a>Meldung: weiterleiten

Weiterleiten einer Nachricht. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.Send*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/forward
POST /users/<id | userPrincipalName>/messages/<id>/forward
POST /me/mailFolders/<id>/messages/<id>/forward
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/forward
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Kommentar|String|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|toRecipients|[Empfänger](../resources/recipient.md) -Auflistung|Die Liste der Empfänger.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "message_forward"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/forward
Content-type: application/json
Content-length: 166

{
  "comment": "comment-value",
  "toRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ]
}
```

##### <a name="response"></a>Antwort
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: forward",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
