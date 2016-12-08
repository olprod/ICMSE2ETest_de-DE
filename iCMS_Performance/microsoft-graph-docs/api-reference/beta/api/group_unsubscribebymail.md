# <a name="group-unsubscribebymail"></a>Gruppe: UnsubscribeByMail

Durch Aufrufen dieser Methode wird den aktuellen Benutzer Empfang von e-Mail-Benachrichtigungen für diese Gruppe über neue Beiträge, Ereignisse und die Dateien in dieser Gruppe deaktiviert. Unterstützt nur die Office 365-Gruppen. 
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Group.ReadWrite.All* 
*Group.ReadWrite.All*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/unsubscribeByMail
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "group_unsubscribebymail"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/unsubscribeByMail
```

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
  "description": "group: unsubscribeByMail",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->