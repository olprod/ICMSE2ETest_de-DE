# <a name="group-checkmembergroups"></a>Gruppe: CheckMemberGroups
Überprüfen Sie die Mitgliedschaft in der angegebenen Liste von Gruppen. Gibt aus der Liste diese Gruppen, die die angegebene Gruppe eine direkte oder transitive Mitglied ist. 

Sie können auf ein Maximum von 20 Gruppen pro Anforderung von überprüfen. Diese Funktion unterstützt Office 365 und anderen Arten von Gruppen in Azure Active Directory bereitgestellt werden. Beachten Sie, dass Office 365 Gruppen Gruppen enthalten kann. Die Mitgliedschaft in einer Office 365-Gruppe ist also immer direkten. 

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/checkMemberGroups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|groupIds|String|Ein Array mit Ids der Gruppe|

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt `200, OK` Antwortcode und Zeichenfolge-Auflistungsobjekt in der Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "group_checkmembergroups"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/checkMemberGroups
Content-type: application/json
Content-length: 44

{
  "groupIds": [
    "groupIds-value"
  ]
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
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
  "description": "group: checkMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
