# <a name="get-singlevaluelegacyextendedproperty"></a>Abrufen von singleValueLegacyExtendedProperty

Erste Ressourceninstanzen, die einen einzelner Wert erweiterte Eigenschaft mit enthalten `$expand` oder `$filter`.

Mit dem Abfragezeichenfolgen-Parameter `$expand` können Sie zum Abrufen der angegebenen Instanz mit dem angegebenen erweiterten Eigenschaft erweitert. Dies ist derzeit die einzige Möglichkeit, das [SingleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md) -Objekt abzurufen, das eine erweiterte Eigenschaft darstellt.

Mit dem Abfragezeichenfolgen-Parameter `$filter` können Sie alle Instanzen der angegebenen Ressource abrufen, die eine erweiterte Eigenschaft einen Filter auf die Eigenschaften **-Id** und **Wert** entsprechen. Der Filter wird auf alle Instanzen der Ressource im Postfach des angemeldeten Benutzers angewendet.

Die folgenden Benutzerressourcen werden unterstützt:

- [Nachricht](../resources/message.md)
- [mailFolder](../resources/mailfolder.md)
- [Ereignis](../resources/event.md)
- [Kalender](../resources/calendar.md)
- [Wenden Sie sich an](../resources/contact.md)
- [contactFolder](../resources/contactfolder.md) 

Sowie die folgenden Gruppenressourcen:

- Gruppe- [Ereignis](../resources/event.md)
- Gruppe [Kalender](../resources/calendar.md)
- Gruppe [Buchen](../resources/post.md) 

Weitere Informationen zur Verwendung von Office 365 Daten Extensions oder erweiterten Eigenschaften und zur Angabe der erweiterter Eigenschaften finden Sie unter [Erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) .

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API, abhängig von der Ressource ausführen, den Sie erhalten:

- _Mail.Read_
- _Calendars.Read_
- _Contacts.Read_
- _Group.Read.All_ 

## <a name="http-request"></a>HTTP-Anforderung

#### <a name="get-a-resource-instance-using-expand"></a>ABRUFEN einer Ressource Instanz verwenden.`$expand`
Rufen Sie eine Ressourceninstanz erweitert mit der erweiterten Eigenschaft, die einen Filter auf die **Id** -Eigenschaft entspricht. Stellen Sie sicher, dass Sie [URL-Codierung](http://www.w3schools.com/tags/ref_urlencode.asp) auf die Leerzeichen in die Filterzeichenfolge anwenden.

Erhalten Sie eine Instanz der **Nachricht** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /me/mailFolders/<id>/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **MailFolder** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/mailFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

Rufen Sie eine Instanz **Ereignis** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **Kalender** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/calendars/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
Erhalten Sie eine Instanz **wenden Sie sich an** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /me/contactFolders/<id>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **ContactFolder** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
Eine Gruppe **Ereignis** Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

Eine Gruppe **Buchen** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

#### <a name="get-resource-instances-using-filter"></a>Mit Ressourceninstanzen ABGERUFEN`$filter`

Rufen Sie Instanzen einer unterstützten Ressource, die die erweiterte Eigenschaft einen Filter auf die Eigenschaften **-Id** und **Wert** entsprechen. Stellen Sie sicher, dass Sie die folgenden Zeichen in der Filterzeichenfolge - Schrägstrich und Speicherplatz [URL-Codierung](http://www.w3schools.com/tags/ref_urlencode.asp) anwenden.


**Nachricht** Instanzen abgerufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /me/mailFolders/<id>/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
Rufen Sie **MailFolder** Instanzen ab:
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/mailFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

**Ereignis** -Instanzen abzurufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
**Kalender** -Instanzen abzurufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/calendars?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
**Wenden Sie sich an** Instanzen abgerufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /me/contactFolders/<id>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
Rufen Sie **ContactFolder** Instanzen ab:
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contactFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
Gruppe **Ereignis** Instanzen abgerufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

Gruppe **Buchen** Instanzen abgerufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id_value|String|Die ID der erweiterten Eigenschaft übereinstimmen. Es muss eine der unterstützten Formate folgen. Weitere Informationen finden Sie unter [Outlook erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) . Erforderlich.|
|property_value|String|Der Wert der erweiterten Eigenschaft übereinstimmen. Erforderlich sind, in denen Abschnitt **HTTP-Anforderung** .|

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode.

#### <a name="get-resource-instance-using-expand"></a>GET-Ressource Instanz verwenden`$expand`
Der Antworttext enthält ein Objekt, das die angeforderte Ressourceninstanz erweitert mit übereinstimmenden [SingleValueLegacyExtendedProperty](../resources/singlevaluelegacyextendedproperty.md) -Objekt darstellt.
  
#### <a name="get-resource-instances-using-filter"></a>Mit Ressourceninstanzen ABGERUFEN`$filter`
Der Antworttext enthält ein oder mehrere Objekte, die die Ressourceninstanzen, die die übereinstimmende erweiterte Eigenschaft enthalten darstellen. Der Antworttext umfasst nicht die erweiterte Eigenschaft.

## <a name="example"></a>Beispiel
#### <a name="request-1"></a>Anforderung 1

Im ersten Beispiel dient zum Abrufen und die angegebene Nachricht durch das Einbeziehen von einer erweiterten Eigenschaft einwertig erweitert. Der Filter gibt die erweiterte Eigenschaft mit dessen **Id** die Zeichenfolge entsprechen `String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color` (mit der URL-Codierung entfernt hier zum Vereinfachen des Lesens).

<!-- {
  "blockType": "request",
  "name": "get_singlevaluelegacyextendedproperty_1"
}-->
```http
GET https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')?$expand=singleValueExtendedProperties($filter=id%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color')
```
##### <a name="response-1"></a>Antwort 1
Der Antworttext enthält alle Eigenschaften der angegebenen Nachricht und erweiterte Eigenschaft aus dem Filter zurückgegeben.

Hinweis: Das hier gezeigte **Message** -Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H\"",
    "id": "AAMkAGE1M2_bs88AACHsLqWAAA=",
    "subject": "RE: Talk about emergency prep",
    "sender": {
        "emailAddress": {
            "name": "Christine Irwin",
            "address": "christine@contoso.com"
        }
    },
    "from": null,
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Christine Irwin",
                "address": "christine@contoso.com"
            }
        }
    ],
    "singleValueExtendedProperties@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2_bs88AACHsLqWAAA%3D')/singleValueExtendedProperties",
    "singleValueExtendedProperties": [
        {
            "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
            "value": "Green"
        }
    ]
}
```

****

#### <a name="request-2"></a>Anfordern von 2

Im zweiten Beispiel wird die Nachrichten, die den erweiterte Eigenschaft im Filter angegebenen Single-Wert sein. Der Filter gibt die erweiterte Eigenschaft mit zurück:
- Seine **Id** die Zeichenfolge übereinstimmende `String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color` (mit der URL-Codierung entfernt hier zum Vereinfachen des Lesens).
- Der **Wert** wird `Green`.

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/api/beta/Me/messages?$filter=singleValueExtendedProperties%2FAny(ep%3A%20ep%2Fid%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color'%20and%20ep%2Fvalue%20eq%20'Green')
```

##### <a name="response-2"></a>Antwort 2

Eine erfolgreiche Antwort wird angegeben, indem eine `HTTP 200 OK` Antwortcode und der Antworttext enthält die Eigenschaften der Nachrichten mit der erweiterten Eigenschaft, die dem Filter entsprechen. Der Antworttext ist ähnlich wie die Antwort aus [eine Nachricht-Auflistung abrufen](../api/user_list_messages.md). Die Antwort enthält keinen übereinstimmende erweiterte Eigenschaft.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get singleValueLegacyExtendedProperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->