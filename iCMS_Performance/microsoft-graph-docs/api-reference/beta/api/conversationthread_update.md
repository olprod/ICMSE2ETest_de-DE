# <a name="update-conversationthread"></a>Conversationthread aktualisieren

Sperren oder Entsperren von einem Thread, um zuzulassen, oder an den Thread weiter buchen zu vermeiden.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /groups/<id>/threads/<id>
PATCH /groups/<id>/conversations/<id>/threads/<id>

```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|isLocked|Boolean|Gibt an, ob der Thread gesperrt ist. Legen Sie auf `true` So verweigern Sie buchen.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [ConversationThread](../resources/conversationthread.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_conversationthread"
}-->
```http
PATCH https://graph.microsoft.com/beta/groups/<id>/threads/<id>
Content-type: application/json
Content-length: 419

{
  "@odata.type":"#Microsoft.OutlookServices.ConversationThread",
  "isLocked": true
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversationThread"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 419

{
  "toRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ],
  "topic": "topic-value",
  "hasAttachments": true,
  "lastDeliveredDateTime": "datetime-value",
  "uniqueSenders": [
    "uniqueSenders-value"
  ],
  "ccRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ],
  "isLocked": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update conversationthread",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
