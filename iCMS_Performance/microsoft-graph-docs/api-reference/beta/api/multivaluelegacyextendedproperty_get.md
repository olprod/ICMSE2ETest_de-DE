# <a name="get-multivaluelegacyextendedproperty"></a>Abrufen von multiValueLegacyExtendedProperty

Rufen Sie eine Ressourceninstanz, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`.

Mit dem Abfragezeichenfolgen-Parameter `$expand` können Sie zum Abrufen der angegebenen Instanz mit dem angegebenen erweiterten Eigenschaft erweitert. Dies ist derzeit die einzige Möglichkeit zum Abrufen des [MultiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md) -Objekts, das eine erweiterte Eigenschaft darstellt.

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

Rufen Sie eine Ressourceninstanz erweitert mit der erweiterten Eigenschaft, die einen Filter auf die **Id** -Eigenschaft entspricht. Stellen Sie sicher, dass Sie [URL-Codierung](http://www.w3schools.com/tags/ref_urlencode.asp) auf die Leerzeichen in die Filterzeichenfolge anwenden.

Erhalten Sie eine Instanz der **Nachricht** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/mailFolders/<id>/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **MailFolder** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/mailFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Rufen Sie eine Instanz **Ereignis** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **Kalender** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/calendars/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
Erhalten Sie eine Instanz **wenden Sie sich an** :
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/contactFolders/<id>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
Eine **ContactFolder** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
Eine Gruppe **Ereignis** Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Eine Gruppe **Buchen** -Instanz abrufen:
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id_value|String|Die ID der erweiterten Eigenschaft übereinstimmen. Es muss eine der unterstützten Formate folgen. Weitere Informationen finden Sie unter [Outlook erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) . Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode. 

Antworttext enthält ein Objekt, das die angeforderte Ressourceninstanz, erweitert mit übereinstimmenden [MultiValueLegacyExtendedProperty](../resources/multivaluelegacyextendedproperty.md) -Objekt darstellt.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
In diesem Beispiel wird dient zum Abrufen und erweitert das angegebene Ereignis durch das Einbeziehen von einer erweiterten Eigenschaft mit mehreren Werten. Der Filter gibt die erweiterte Eigenschaft mit dessen **Id** die Zeichenfolge entsprechen `StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation` (mit der URL-Codierung entfernt hier zum Vereinfachen des Lesens).

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/me/events('AAMkAGE1M2_bs88AACbuFiiAAA=')?$expand=multiValueExtendedProperties($filter=id%20eq%20'StringArray%20{66f5a359-4659-4830-9070-00050ec6ac6e}%20Name%20Recreation')
```
##### <a name="response"></a>Antwort

Antworttext enthält alle Eigenschaften des angegebenen Ereignisses und erweiterte Eigenschaft aus dem Filter zurückgegeben.

Hinweis: Die hier gezeigte **Event** -Objekts wird der Kürze halber Zahl gekürzt. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/events/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/events('AAMkAGE1M2_bs88AACbuFiiAAA=')",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAm8k15A==\"",
    "id": "AAMkAGE1M2_bs88AACbuFiiAAA=",
    "start": {
        "dateTime": "2015-11-26T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2015-11-30T05:00:00.0000000",
        "timeZone": "UTC"
    },
    "organizer": {
        "emailAddress": {
            "name": "Christine Irwin",
            "address": "christine@contoso.com"
        }
    },
    "multiValueExtendedProperties@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/events('AAMkAGE1M2_bs88AACbuFiiAAA%3D')/multiValueExtendedProperties",
    "multiValueExtendedProperties": [
        {
            "id": "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
            "value": [
                "Food",
                "Hiking",
                "Swimming"
            ]
        }
    ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get multiValueLegacyExtendedProperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->