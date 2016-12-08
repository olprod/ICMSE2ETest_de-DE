# <a name="get-data-extension"></a>Abrufen von Daten-Erweiterung

Rufen Sie eine Daten-Erweiterung ([OpenTypeExtension](../resources/openTypeExtension.md) -Objekt) durch den Namen oder den vollqualifizierten Namen identifiziert.

Ressourcen, die open-Typ Office 365 Daten Extensions unterstützen gehören einer Nachricht, Kalenderereignis oder Kontakt der des angemeldeten Benutzers auf Office 365 oder Outlook.com. Alternativ kann ein Ereignis oder eine Post für eine Office 365-Gruppe sein.
Je nach dem Ressourcentyp stehen verschiedene Möglichkeiten zum Abrufen von Daten der Erweiterung.

|**BESCHREIBUNG**|**Unterstützte Ressourcen**|**Antworttext**|
|:-----|:-----|:-----|
|Abrufen einer bestimmten Erweiterungs in einer Ressourceninstanz einer bekannten.|Meldung, Ereignis, Kontakt, Gruppe Ereignis, Gruppe Beitrag | Erweiterung nur Daten.|
|Rufen Sie eine bekannte Ressourceninstanz erweitert mit einer bestimmten Erweiterung.|Meldung, Ereignis, Kontakt, Gruppe-Ereignis|Eine Ressourceninstanz erweitert mit der Erweiterung Daten verwendet werden.|
|Suchen und Ressourceninstanzen mit einer bestimmten Erweiterung erweitern. |Meldung, Ereignis, Kontakt, Gruppe-Ereignis|Ressourceninstanzen erweitert, mit der Erweiterung Daten.|


## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist, diese API, abhängig von der Ressource auszuführen, Sie die Erweiterung von erhalten, erforderlich:

- _Mail.Read_
- _Calendars.Read_
- _Contacts.Read_
- _Group.Read.All_
 
## <a name="http-request"></a>HTTP-Anforderung


Zum Abrufen einer bestimmten Erweiterungs in einer Ressourceninstanz der bekannten:
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/messages/<Id>/extensions/<extensionId>
GET /me/mailFolders/<Id>/messages/<Id>/extensions/<extensionId>

GET /me/events/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/events/<Id>/extensions/<extensionId>

GET /me/contacts/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/contacts/<Id>/extensions/<extensionId>

GET /groups/<Id>/events/<Id>/extensions/<extensionId>

GET /groups/<Id>/threads/<Id>/posts/<Id>/extensions/<extensionId>
GET /groups/<Id>/conversations/<Id>/threads/<Id>/posts/<Id>/extensions/<extensionId>
```

So rufen Sie eine bekannte Ressourceninstanz erweitert mit einer Erweiterung, die einen Filter in der **Id** -Eigenschaft entspricht:
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /me/mailFolders/<Id>/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /me/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /me/contacts/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/contacts/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /groups/<Id>/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')
```

Zum Filtern von Resource-Instanzen, die diese Instanzen abgerufen oder enthalten eine Erweiterung einem Filter auf die **Id** -Eigenschaft erweitert, mit der Erweiterung:
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /me/mailFolders/<Id>/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /me/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /me/contacts?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/contacts?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /groups/<Id>/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
```


## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|ID|string|Platzhalter für einen eindeutigen Bezeichner für ein Objekt in der entsprechenden Auflistung wie Nachrichten, Ereignisse, Kontakte. Erforderlich. Wird nicht mit dem **Id** -Eigenschaft für ein **OpenTypeExtension**verwechselt werden.|
|extensionID geändert|string|Platzhalter für eine Erweiterung der ist eine eindeutige ID einer Erweiterung oder einen voll gekennzeichneten Namen, der den Erweiterungstyp und eindeutige Text-ID verkettet. Wenn Sie die Erweiterung Erstellen der vollständig qualifizierte Namen in der **Id** -Eigenschaft zurückgegeben. Erforderlich.|


## <a name="optional-query-parameters"></a>Optional Abfrageparameter

Stellen Sie sicher, dass Sie auf die Leerzeichen in [URL-Codierung](http://www.w3schools.com/tags/ref_urlencode.asp) anwenden, die `$filter` Zeichenfolge.

|**Name**|**Wert**|**Beschreibung**|
|:---------------|:--------|:-------|
|$filter|Zeichenfolge|Gibt eine Erweiterung mit der **Id** entsprechenden die `extensionId` Wert des Parameters.|
|$filter mit **any** -operator|string|Gibt Instanzen einer Ressource-Auflistung, die eine Erweiterung mit der **Id** entsprechenden enthalten die `extensionId` Wert des Parameters.| 
|$Erweitern|Zeichenfolge|Erweitert eine Ressourceninstanz um eine Erweiterung einzuschließen. |


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortobjekt Code und [OpenTypeExtension](../resources/opentypeextension.md) im Antworttext.
Je nach Abfrage GET unterscheidet sich der genauen Antworttext.
## <a name="example"></a>Beispiel

#### <a name="request-1"></a>Anforderung 1

Im ersten Beispiel 2 Möglichkeiten verweisen auf eine Erweiterung und ruft die Erweiterung in der angegebenen Nachricht ab. Die Antwort ist gleich, unabhängig von der Möglichkeit verwendet, um die Erweiterung verweisen.

Erstens anhand des Namens: 

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_1"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

Zweitens durch seine ID (vollqualifizierter Name):

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

#### <a name="response-1"></a>Antwort 1
Nachfolgend finden Sie die Antwort für das erste Beispiel.
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00Z"
}
```

****


#### <a name="request-2"></a>Anforderung 2

Im zweite Beispiel verweist auf eine Erweiterung anhand des Namens und ruft die Erweiterung im Ereignis angegebenen Gruppe ab.

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_2"
}-->
```http
GET https://graph.microsoft.com/v1.0/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl17IsAAA=')/extensions('Com.Contoso.Deal') 
```

#### <a name="response-2"></a>Antwort 2

Nachfolgend finden Sie die Antwort aus dem zweiten Beispiel.

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl7IsAAA%3D')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Deal",
    "extensionName": "Com.Contoso.Deal",
    "companyName": "Alpine Skis",
    "dealValue": 1010100,
    "expirationDate": "2015-07-03T13:04:00Z"
}
```

****

#### <a name="request-3"></a>Anforderung 3

Im dritte Beispiel dient zum Abrufen und erweitert die angegebene Nachricht durch das Einbeziehen von der Erweiterungs von einem Filter zurückgegeben. Der Filter gibt die Erweiterung mit dessen **Id** übereinstimmenden einen voll gekennzeichneten Namen zurück.

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_3"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')?$expand=extensions($filter=id%20eq%20'Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```


#### <a name="response-3"></a>Antwort 3

Und Hier wird die Antwort im dritten Beispiel. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages/$entity",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "categories": [
    ],
    "createDateTime": "2015-06-19T02:03:31Z",
    "lastModifiedDateTime": "2015-08-13T02:28:00Z",
    "subject": "Attached is the requested info",
    "bodyPreview": "See the images attached.",
    "body": {
        "contentType": "HTML",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "importance": "Normal",
    "hasAttachments": true,
    "parentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "from": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "sender": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "address": "wendy@contoso.com",
                "name": "Wendy Molina"
            }
        }
    ],
    "ccRecipients": [
    ],
    "bccRecipients": [
    ],
    "replyTo": [
    ],
    "conversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "receivedDateTime": "2015-06-19T02:05:04Z",
    "sentDateTime": "2015-06-19T02:04:59Z",
    "isDeliveryReceiptRequested": false,
    "isReadReceiptRequested": false,
    "isDraft": false,
    "isRead": true,
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "Focused",
    "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('desmond40contoso.com')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions", 
    "extensions": [ 
      { 
        "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
        "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "extensionName": "Com.Contoso.Referral",
        "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "companyName": "Wingtip Toys",
        "dealValue": 500050,
        "expirationDate": "2015-12-03T10:00:00Z"
      }
     ]
}
```

****

#### <a name="request-4"></a>Anfordern von 4

Im vierte Beispiel verweist auf eine Erweiterung durch den vollqualifizierten Namen und ruft die Erweiterung im Beitrag angegebene Gruppe ab.

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_4"
}-->
```http
GET https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate') 
```

#### <a name="response-4"></a>Antwort 4

Nachfolgend finden Sie die Antwort aus dem vierten Beispiel. 

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2015-07-03T13:04:00Z",
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```


#### <a name="request-5"></a>Anforderung 5

Alle Nachrichten im Postfach des angemeldeten Benutzers Einträge gesucht, die enthalten eine Erweiterung einem Filter und erweitern sie durch die Erweiterung einschließlich sieht das fünfte Beispiel. Der Filter gibt Erweiterungen, die die **Id** -Eigenschaft entsprechen den Erweiterungsnamen `Com.Contoso.Referral`.

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_5"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=Extensions/any(f:f/id%20eq%20'Com.Contoso.Referral')&$expand=Extensions($filter=id%20eq%20'Com.Contoso.Referral')
```


####<a name="response-5"></a>Antwort 5

In dieser Antwort für das fünfte Beispiel, besteht nur eine Nachricht in das Postfach des Benutzers mit der Erweiterung mit der **Id** gleich `Com.Contoso.Referral`.

Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages",
  "value": [
  {

    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "categories": [
    ],
    "createDateTime": "2015-06-19T02:03:31Z",
    "lastModifiedDateTime": "2015-08-13T02:28:00Z",
    "subject": "Attached is the requested info",
    "bodyPreview": "See the images attached.",
    "body": {
        "contentType": "HTML",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "importance": "Normal",
    "hasAttachments": true,
    "parentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "from": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "sender": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "address": "wendy@contoso.com",
                "name": "Wendy Molina"
            }
        }
    ],
    "ccRecipients": [
    ],
    "bccRecipients": [
    ],
    "replyTo": [
    ],
    "conversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "receivedDateTime": "2015-06-19T02:05:04Z",
    "sentDateTime": "2015-06-19T02:04:59Z",
    "isDeliveryReceiptRequested": false,
    "isReadReceiptRequested": false,
    "isDraft": false,
    "isRead": true,
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "Focused",
    "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('desmond40contoso.com')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions", 
    "extensions": [ 
      { 
        "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
        "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "extensionName": "Com.Contoso.Referral",
        "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "companyName": "Wingtip Toys",
        "dealValue": 500050,
        "expirationDate": "2015-12-03T10:00:00Z"
      }
     ]
  }
  ]
}

```



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get openTypeExtension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
