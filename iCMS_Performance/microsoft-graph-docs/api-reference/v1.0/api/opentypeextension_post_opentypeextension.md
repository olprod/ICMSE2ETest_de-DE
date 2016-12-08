# <a name="create-data-extension"></a>Erstellen von Daten-Erweiterung

Erstellen Sie eine Daten-Erweiterung ([OpenTypeExtension](../resources/openTypeExtension.md) -Objekt) und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource. 

Die Ressource kann eine Meldung angezeigt, Kalenderereignis oder einen Kontakt im Postfach auf Office 365 oder Outlook.com des angemeldeten Benutzers. Alternativ kann ein Ereignis oder eine Post für eine Office 365-Gruppe sein. 


## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist erforderlich, damit diese API, abhängig von der Ressource ausführen, das Sie die Erweiterung im erstellen:

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP-Anforderung
Sie können eine Erweiterung in einer neuen oder vorhandenen Ressourceninstanz erstellen.

Um eine Erweiterung in einer _neuen_ Instanz der Ressource zu erstellen, verwenden Sie die gleiche REST-Anforderung als die Instanz erstellt und enthalten Sie die Eigenschaften für die neue Ressource Instanz _und die Erweiterung_ im Textkörper Anforderung.
Beachten Sie, dass einige Ressourcen in mehr als eine Möglichkeit der Erstellung unterstützt. Weitere Informationen zum Erstellen dieser Ressourceninstanzen finden Sie unter den entsprechenden Themen für die Erstellung einer [Nachricht](../resources/message.md), [Ereignisse](../api/user_post_events.md), [wenden Sie sich an](../api/user_post_contacts.md), [Gruppe](../api/group_post_events.md)und [Gruppe Beitrag](../resources/post.md). 
 
Im folgenden finden die Syntax der Anforderungen. 

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages
POST /users/<id|userPrincipalName>/messages
POST /me/mailFolders/<id>/messages

POST /me/events
POST /users/<id|userPrincipalName>/events

POST /me/contacts
POST /users/<id|userPrincipalName>/contacts

POST /groups/<id>/events

POST /groups/<id>/threads/<id>/posts/<id>/microsoft.graph.reply
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/microsoft.graph.reply
POST /groups/<id>/threads/<id>/microsoft.graph.reply
POST /groups/<id>/conversations/<id>/threads/<id>/microsoft.graph.reply
POST /groups/<id>/threads
POST /groups/<id>/conversations
```

Um eine Erweiterung in einer vorhandenen Ressourceninstanz erstellen möchten, geben Sie die Instanz in der Anforderung und enthalten Sie die Erweiterung im Textkörper Anforderung.

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/extensions
POST /users/<id|userPrincipalName>/messages/<id>/extensions
POST /me/mailFolders/<id>/messages/<id>/extensions

POST /me/events/<id>/extensions
POST /users/<id|userPrincipalName>/events/<id>/extensions

POST /me/contacts/<id>/extensions
POST /users/<id|userPrincipalName>/contacts/<id>/extensions

POST /groups/<id>/events/<id>/extensions

POST /groups/<id>/threads/<id>/posts/<id>/extensions
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions
```


## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Ein eindeutiger Bezeichner für ein Objekt in der entsprechenden Auflistung. Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|
| Inhaltstyp | Application/json |

## <a name="request-body"></a>Anforderungstext

Bieten Sie ein JSON-Hauptteil eines [OpenTypeExtension](../resources/openTypeExtension.md)die folgenden erforderlichen Name / Wert-Paare und zusätzlichen benutzerdefinierten Daten. Die Daten in der JSON-Nutzlast möglich Grundtypen oder Arrays von Grundtypen.

| Name       | Wert |
|:---------------|:----------|
| @odata.type | Microsoft.Graph.OpenTypeExtension |
| .-Kennung Erweiterungsname | Unique_string % |

Geben Sie beim Erstellen einer Erweiterungs in eine _neue_ Instanz der Ressource, zusätzlich zu den neuen **OpenTypeExtension** -Objekts eine JSON-Darstellung der Ressourceninstanz ([Meldung](../resources/message.md), [Ereignis](../resources/event.md), [wenden Sie sich an](../resources/contact.md)oder [Gruppe Post](../resources/post.md) -Objekt).

## <a name="response"></a>Antwort

#### <a name="response-code"></a>Antwortcode
Ein Vorgang erfolgreich bei der Erstellung einer Erweiterungs zurückgegeben, den gleichen Antwortcode als der Vorgang verwendet wird, um nur die Ressourceninstanz ohne die Erweiterung zu erstellen. Je nach den Vorgang kann sein `201 Created` oder `202 Accepted`. Finden Sie in den entsprechenden Themen für die Instanz zu erstellen.

#### <a name="response-body"></a>Antworttext
Beim Erstellen einer Erweiterungs in eine _neue_ Instanz der Ressource durch einen POST-Vorgang für eine Auflistung der [Meldung](../resources/message.md), [Ereignis](../resources/event.md)oder [Kontaktobjekte](../resources/contact.md) enthält der Antworttext die neue Instanz mit den [OpenTypeExtension](../resources/openTypeExtension.md)erweitert. 

Wenn Sie eine Erweiterung in einer _neuen_ [Gruppe Beitrag](../resources/post.md)erstellen, enthält die Antwort nur einen Antwortcode jedoch keines Antworttexts.

Beim Erstellen einer Erweiterungs in eine _vorhandene_ Instanz der Ressource enthält der Antworttext das **OpenTypeExtension** -Objekt.
 


## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1

Im erste Beispiel erstellt eine Nachricht und die Erweiterung in einem Anruf. Textkörper der Anforderung umfasst Folgendes:

- Der **Betreff**, **Textkörper**und **ToRecipients** Eigenschaften typisch für eine neue Nachricht. 
- Und für die Erweiterung:

  - Bei dem Typ `Microsoft.Graph.OpenTypeExtension`. 
  - Der Name der Erweiterung "Com.Contoso.Referral". 
  - Zusätzliche Daten, die als 3 benutzerdefinierte Eigenschaften in der JSON-Nutzlast gespeichert werden: `companyName`, `expirationDate`, und `dealValue`.  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_1"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages

{
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "You should be proud!"
  },
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com"
      }
    }
  ],
  "extensions": [
    {
      "@odata.type": "Microsoft.Graph.OpenTypeExtension",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```

##### <a name="response-1"></a>Antwort 1

Nachfolgend finden Sie die Antwort für das erste Beispiel. Antworttext enthält Eigenschaften der neuen Nachricht und für die neue Erweiterung Folgendes:

- Die **Id** -Eigenschaft mit der vollständig qualifizierte Name der `Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`. 
- Die Standard-Eigenschaft **.-Kennung Erweiterungsname** in der Anforderung angegeben.
- Die benutzerdefinierten Daten in der Anforderung als 3 benutzerdefinierte Eigenschaften gespeichert angegeben.

Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "id": "AAMkAGEbs88AAB84uLuAAA=",
  "createdDateTime": "2015-10-30T03:03:43Z",
  "lastModifiedDateTime": "2015-10-30T03:03:43Z",
  "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "categories": [ ],
  "receivedDateTime": "2015-10-30T03:03:43Z",
  "sentDateTime": "2015-10-30T03:03:43Z",
  "hasAttachments": false,
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "bodyPreview": "You should be proud!",
  "importance": "Normal",
  "parentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "sender": null,
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com",
        "name": "John Doe"
      }
    }
  ],
  "ccRecipients": [ ],
  "bccRecipients": [ ],
  "replyTo": [ ],
  "conversationId": "AAQkAGEFGugh3SVdMzzc=",
  "isDeliveryReceiptRequested": false,
  "isReadReceiptRequested": false,
  "isRead": true,
  "isDraft": true,
  "webLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "Focused",
  "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages
('AAMkAGEbs88AAB84uLuAAA%3D')/extensions",
  "extensions": [
    {
      "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
      "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
      "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```


****

##### <a name="request-2"></a>Anforderung 2

Im zweite Beispiel erstellt eine Erweiterung in der angegebenen Meldung. Textkörper der Anforderung umfasst folgende für die Erweiterung:

- Der Typ `Microsoft.Graph.OpenTypeExtension`. 
- Der Name der Erweiterung "Com.Contoso.Referral".
- Zusätzliche Daten, die als 3 benutzerdefinierte Eigenschaften in der JSON-Nutzlast gespeichert werden: `companyName`, `dealValue`, und `expirationDate`.  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_2"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions

{ 
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension", 
  "extensionName" : "Com.Contoso.Referral", 
  "companyName" : "Wingtip Toys", 
  "dealValue" : 500050, 
  "expirationDate" : "2015-12-03T10:00:00.000Z" 
} 
```

##### <a name="response-2"></a>Antwort 2

Nachfolgend finden Sie die Antwort für die zweite Beispiel. Der Antworttext umfasst folgende für die neue Erweiterung:

- Die Standard-Eigenschaft **.-Kennung Erweiterungsname**.
- Die **Id** -Eigenschaft mit der vollständig qualifizierte Name der `Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`. 
- Die benutzerdefinierten Daten gespeichert werden.  

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
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
    "expirationDate": "2015-12-03T10:00:00.000Z"
}
```

****

##### <a name="request-3"></a>Anforderung 3

Im dritte Beispiel erstellt eine Erweiterung in der angegebenen Gruppe-Ereignis. Textkörper der Anforderung umfasst folgende für die Erweiterung:

- Der Typ `Microsoft.Graph.OpenTypeExtension`. 
- Der Name der Erweiterung "Com.Contoso.Deal".
- Zusätzliche Daten, die als 3 benutzerdefinierte Eigenschaften in der JSON-Nutzlast gespeichert werden: `companyName`, `dealValue`, und `expirationDate`.  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_3"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl17IsAAA=')/extensions 

{
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension",
  "extensionName" : "Com.Contoso.Deal",
  "companyName" : "Alpine Skis",
  "dealValue" : 1010100,
  "expirationDate" : "2015-07-03T13:04:00.000Z"
}
```

##### <a name="response-3"></a>Antwort 3

Nachfolgend finden Sie die Antwort aus der dritten beispielanforderung.

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
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

##### <a name="request-4"></a>Anfordern von 4

Das vierte Beispiel erstellt eine Erweiterung in einer neuen Gruppe Post, über einen Aufruf der gleichen **Reply** -Aktion zu einer vorhandenen Gruppe Beitrag. Die **Reply** -Aktion erstellt eine neue Bereitstellung und eine neue Erweiterung im Beitrag eingebettet. Textkörper der Anforderung enthält eine **post** -Eigenschaft, die wiederum den **Textkörper** der neuen Beitrag und die folgenden Daten für die neue Erweiterung enthält:

- Der Typ `Microsoft.Graph.OpenTypeExtension`. 
- Der Name der Erweiterung "Com.Contoso.HR".
- Zusätzliche Daten, die als 3 benutzerdefinierte Eigenschaften in der JSON-Nutzlast gespeichert werden: `companyName`, `expirationDate`, und das Array von Zeichenfolgen `topPicks`.

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_4"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAAC1heiSAAA=')/microsoft.graph.reply 

{
  "post": {
    "body": {
      "contentType": "html",
      "content": "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
    },
  "extensions": [
    {
      "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
      "extensionName": "Com.Contoso.HR",
      "companyName": "Contoso",
      "expirationDate": "2015-07-03T13:04:00.000Z",
      "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
      ]
    }
  ]        
  }
}
```

##### <a name="response-4"></a>Antwort 4

Nachfolgend finden Sie die Antwort aus dem vierten Beispiel. Erstellen von erfolgreich eine Erweiterung in einer neuen Gruppe buchen Ergebnisse im nur HTTP 202 Antwortcode.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
Content-type: text/plain
Content-Length: 0
```


****

##### <a name="request-5"></a>Anforderung 5

Das fünfte Beispiel erstellt eine Erweiterung in eine neue Gruppe Bereitstellung mithilfe des gleichen POST-Vorgangs zum Erstellen einer Unterhaltung. POST-Operation einer neuen Unterhaltung, Thread und Post und erstellt eine neue Erweiterung im Beitrag eingebettet. Textkörper der Anforderung enthält das **Thema** und **Threads** Eigenschaften und ein untergeordnetes **post** -Objekt für die neue Unterhaltung. Das **post** -Objekt enthält wiederum im **Textkörper** der neuen Beitrag und die folgenden Daten für die Erweiterung:

- Bei dem Typ `Microsoft.Graph.OpenTypeExtension`. 
- Der Name der Erweiterung "Com.Contoso.HR".
- Zusätzliche Daten, die als 3 benutzerdefinierte Eigenschaften in der JSON-Nutzlast gespeichert werden: `companyName`, `expirationDate`, und das Array von Zeichenfolgen `topPicks`.

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_5"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations

{
  "Topic": "Does anyone have a second?",
  "Threads": [
    {
      "Posts": [
        {
          "Body": {
            "ContentType": "HTML",
            "Content": "This is urgent!"
          },
          "Extensions": [
            {
              "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
              "extensionName": "Com.Contoso.Benefits",
              "companyName": "Contoso",
              "expirationDate": "2016-08-03T11:00:00.000Z",
              "topPicks": [
                "Employees only",
                "Add spouse or guest",
                "Add family"
              ]  
            }  
          ] 
        } 
      ]  
    } 
  ]
}
```

##### <a name="response-5"></a>Antwort 5

Nachfolgend finden Sie die Antwort aus dem fünften Beispiel, das die neue Unterhaltung und eine Thread-ID enthält Diese neue Thread enthält einen automatisch erstellten Post, der wiederum die neue Erweiterung enthält. 

Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.

Die neue Erweiterung, zuerst [erhalten alle Beiträge](../api/conversationthread_list_posts.md) in dieser Thread abrufen und zunächst sollte nur ein. Wenden Sie dann die Post-ID und den Erweiterungsnamen `Com.Contoso.Benefits` zum [Abrufen der Erweiterungs](../api/opentypeextension_get.md).

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversation"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations/$entity",
    "id": "AAQkADJToRlbJ5Mg7TFM7H-j3Y=",
    "threads@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations('AAQkADJToRlbJ5Mg7TFM7H-j3Y%3D')/threads",
    "threads": [
        {
            "id": "AAQkADJDtMUzsf_PdhAAswJOhGVsnkyDtMUzsf_Pdg=="
        }
    ]
}

```


<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create extension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
