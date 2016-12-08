# <a name="update-group"></a>Aktualisierungsgruppe

Aktualisieren Sie die Eigenschaften eines Group-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Der **Bereich** ist erforderlich, um diese API ausführen: *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /groups/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|Standard ist **false**. Gibt an, ob externe Mitglieder e-Mail an Gruppe senden können.|
|autoSubscribeNewMembers|Boolean|Standard ist **false**. Gibt an, ob neue Mitglieder der Gruppe hinzugefügt automatisch zum Empfangen von e-Mail-Benachrichtigungen abonniert werden.|
|description|String|Eine optionale Beschreibung für die Gruppe. |
|displayName|String|Der Anzeigename für die Gruppe. Diese Eigenschaft ist erforderlich, wenn eine Gruppe erstellt wird und kann nicht während des Updates deaktiviert werden. Unterstützt $filter und $orderby.|
|groupTypes|String-Auflistung|Gibt den Typ der Gruppe zu erstellen. Mögliche Werte sind **Unified** zum Erstellen einer Gruppe von Office 365 oder **DynamicMembership** für dynamische Gruppen.  Für alle anderen Gruppe Typen, wie Sicherheit-aktivierten Gruppen und e-Mail-aktivierte Sicherheitsgruppen diese Eigenschaft nicht festlegen.|
|visibility|Boolean|Gibt die Sichtbarkeit einer Office 365-Gruppe. Mögliche Werte sind: **Private**, **Public**oder leer (die als **Öffentliche**interpretiert wird).|
|mailEnabled|Boolean|Gibt an, ob die Gruppe e-Mail-aktiviert ist. Wenn auch die **SecurityEnabled** -Eigenschaft **true**ist, ist die Gruppe eine e-Mail-aktivierte Sicherheitsgruppe; Andernfalls ist die Gruppe eine Verteilergruppe Microsoft Exchange.|
|mailNickname|String|Der e-Mail-Alias für die Gruppe. Diese Eigenschaft muss angegeben werden, wenn eine Gruppe erstellt wird. $Filter unterstützt.|
|securityEnabled|Boolean|Gibt an, ob die Gruppe eine Sicherheitsgruppe ist. Wenn auch die **MailEnabled** -Eigenschaft true ist, ist die Gruppe eine e-Mail-aktivierte Sicherheitsgruppe an. Andernfalls handelt es sich um eine Sicherheitsgruppe. **"False"** für Office 365-Gruppen muss sein. $Filter unterstützt.|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [Group](../resources/group.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_group"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/groups/<id>
Content-type: application/json
Content-length: 211

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 211

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->