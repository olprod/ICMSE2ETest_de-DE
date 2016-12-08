# <a name="create-rejectedsender"></a>RejectedSender erstellen

Fügen Sie einen neuen Benutzer oder eine Gruppe zur Liste RejectedSender.

Geben Sie den Benutzer oder eine Gruppe `@odata.id` im Textkörper Anforderung. Benutzer in der Absenderliste abgelehnte können nicht in Unterhaltungen der Gruppe (in der POST-Anforderung URL gekennzeichnet) bereitstellen. Stellen Sie sicher, Sie keinen der Benutzer oder die Gruppe in der abgelehnten akzeptierte Listen und Absender, andernfalls erhalten Sie eine Fehlermeldung.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/rejectedSenders/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Id eines Benutzers oder der Gruppe-Objekts.


## <a name="response"></a>Antwort
Diese Methode gibt `204, No Content` Antwortcode und keinen Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_directoryobject_from_group"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/rejectedSenders/$ref
Content-type: application/json
Content-length: 30

{
  "@odata.id":"https://graph.microsoft.com/v1.0/users/alexd@contoso.com"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create rejectedSender",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
