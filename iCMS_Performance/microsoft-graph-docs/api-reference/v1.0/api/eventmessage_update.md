# <a name="update-eventmessage"></a>Eventmessage aktualisieren

Aktualisieren Sie die Eigenschaften des Eventmessage-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id | userPrincipalName>/messages/<id>

PATCH /me/mailFolders/<id>/messages/<id>
PATCH /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |
## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben. Kein Schreibschutz/Updatable-Eigenschaften sind

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Kategorien|String|Die Kategorien, die die Nachricht zugeordnet wird.|
|Bedeutung|String|Die Wichtigkeit der Nachricht. Mögliche Werte sind: `Low`, `Normal`, `High`.|
|isDeliveryReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|
|isRead|Boolean|Gibt an, ob die Nachricht gelesen wurde.|
|isReadReceiptRequested|Boolean|Gibt an, ob eine lesebestätigung für die Nachricht angefordert wird.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [EventMessage](../resources/eventmessage.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_eventmessage"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/messages/<id>
Content-type: application/json
Content-length: 248

{
  "isRead": "true",
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.eventmessage"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 248

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value",
  "meetingMessageType": "meetingMessageType-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update eventmessage",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
