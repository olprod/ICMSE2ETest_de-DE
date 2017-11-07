# <a name="group-getmembergroups"></a>Gruppe: GetMemberGroups
Zurückgeben Sie aller Gruppen, denen die angegebene Gruppe ein Mitglied ist. Die Überprüfung ist transitiv, im Gegensatz zum Lesen der [Mitglied](../api/group_list_memberof.md) Navigation-Eigenschaft, die nur die Gruppen zurückgibt, denen die Gruppe ein direktes Mitglied ist.

Diese Funktion unterstützt Office 365 und anderen Arten von Gruppen in Azure Active Directory bereitgestellt werden. Die maximale Anzahl von Gruppen, die jeder Anforderung zurückgeben kann ist 2046. Hinweis: Office 365 Gruppen Gruppen enthalten kann. Die Mitgliedschaft in einer Office 365-Gruppe ist also immer direkt.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/getMemberGroups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|securityEnabledOnly|Boolean|**true,** um anzugeben, dass nur Sicherheitsgruppen, dass die Gruppe ein Mitglied ist zurückgegeben werden soll. **false,** um anzugeben, dass alle Gruppen, denen die Gruppe ein Mitglied ist zurückgegeben werden sollen.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode und Zeichenfolge-Auflistung im Textkörper Antwort, die die IDs der Gruppen enthält, die die Gruppe ein Mitglied ist.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "group_getmembergroups"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/getMemberGroups
Content-type: application/json
Content-length: 33

{
  "securityEnabledOnly": true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "string",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 39

{
  "value": [
    "string-value"
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: getMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
