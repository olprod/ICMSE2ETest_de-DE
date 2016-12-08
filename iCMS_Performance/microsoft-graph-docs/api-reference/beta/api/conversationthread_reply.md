# <a name="conversationthread-reply"></a>ConversationThread: Antwort

Beantworten Sie ein Thread in einer gruppenunterhaltung, und fügen Sie eine neue Bereitstellung hinzu. Sie können die übergeordnete Unterhaltung in der Anforderung angeben, oder Sie können angeben, dass nur den Thread ohne die Unterhaltung übergeordneten.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/threads/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/reply
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Bereitstellen|[Bereitstellen](../resources/post.md)|Die neue Bereitstellung, die mit beantwortet wird.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `202, Accepted` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "conversationthread_reply"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/threads/<id>/reply
Content-type: application/json
Content-length: 1131

{
  "post": {
    "body": {
      "contentType": "",
      "content": "content-value"
    }
  }
}
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
  "description": "conversationThread: reply",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
