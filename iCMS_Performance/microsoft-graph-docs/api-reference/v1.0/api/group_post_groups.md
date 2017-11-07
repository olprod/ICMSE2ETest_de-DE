# <a name="create-group"></a>Gruppe erstellen

Verwenden Sie diese API, um eine neue Gruppe im Textkörper Anforderung gemäß erstellen. Sie können eine der 3 Arten von Gruppen erstellen:
* Office 365-Gruppe (auch bekannt als unified Gruppe)
* Dynamische Gruppe
* Sicherheitsgruppe

Zumindest müssen Sie angeben, die Eigenschaften für den von Ihnen erstellten Gruppe erforderlich. Dazu gehören:

| Art der Gruppe | **GroupTypes** -Eigenschaft | **SecurityEnabled** -Eigenschaft |
|:--------------|:------------------------|:-----------------------------|
| Office 365 | "Unified" | falsch |
| Dynamik | "DynamicMembership" | falsch |
| Sicherheit | Legen Sie nicht. | wahr |

Andere schreibbaren Eigenschaften wie nötig, wie **MailEnabled** für e-Mail-aktivierte Gruppen angeben. Weitere Informationen finden Sie unter den Eigenschaften des [Group](../resources/group.md) -Ressource.
## <a name="prerequisites"></a>Voraussetzungen
Der **Bereich** ist erforderlich, um diese API ausführen: _Group.ReadWrite.All_ 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der [Group](../resources/group.md) -Objekt.

In der folgenden Tabelle werden die Eigenschaften gezeigt, die erforderlich sind, wenn Sie eine Gruppe erstellen.

| Parameter | Typ | Beschreibung|
|:---------------|:--------|:----------|
| displayName | string | Der Name im Adressbuch für die Gruppe angezeigt. |
| mailEnabled | boolean | Legen Sie auf **"true"** für e-Mail-aktivierte Gruppen. |
| mailNickname | string | Der e-Mail-Alias für die Gruppe. |
| securityEnabled | boolean | Festgelegt auf **true** für Sicherheit-aktivierte Gruppen. Auf **false** festgelegt, wenn eine Office 365-Gruppe zu erstellen. |

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Gruppe](../resources/group.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_group_from_groups"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der [Group](../resources/group.md) -Objekt.
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
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
