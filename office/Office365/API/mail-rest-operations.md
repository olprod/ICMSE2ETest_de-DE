---
ms.Toctitle: Outlook Mail REST API reference
title: Outlook-Mail REST API-Referenz
description: "Verweisen auf die Interaktion mit der e-Mail-REST-API und Client Bibliotheks-APIs, die Zugriff auf den Ordner, e-Mail-Nachrichten und e-Mail-Anlagen zu ermöglichen."
ms.ContentId: aaf0a812-2ddb-4a63-969f-88916c96ab01
ms.date: October 5, 2016
ms.openlocfilehash: ba5f1561f54ca0067098ef93336a84df0a621647
ms.sourcegitcommit: 4648ef0fb81b465cef7e8ccad197fe9b9edabc33
translationtype: MT
---
[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="outlook-mail-rest-api-reference"></a>Outlook-Mail-REST-API-Referenz

[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2default.html)]

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<p class="previewnote">In dieser Dokumentation werden die API für behandelt @-mentions, Abmeldung Nachrichten, schnell Antworten und Verweis Anlagen, die alle gegenwärtig in der Vorschau enthalten sind. Preview-Features können vor dem Abschluss des Vorgangs geändert werden, und Code, der diese Elemente verwendet werden, können beschädigt. Aus diesem Grund sollten Sie nur eine Produktionsversion einer API im Allgemeinen in Ihrem Produktionscode verwenden. Falls verfügbar, ist v2. 0 aktuell die bevorzugten Version.</p>

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


 _**Gilt für:** Exchange Online | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

Die Outlook-Mail-API können Sie lesen, erstellen und Senden von Nachrichten und Anlagen, und reagieren auf Ereignisnachrichten, Ordner anzeigen und verwalten, die von Azure Active Directory in Office 365 gesichert werden. Es bietet auch die gleiche Funktionalität in Microsoft-Konten ausdrücklich in diese Domänen: Hotmail.com, Live.com, MSN-, Outlook.com und Passport.com.


<!-- Can add the following sentence back once the client libraries have been updated for converged auth and outlook.com

You can access the Mail API by calling the corresponding REST APIs directly in your apps, or by using the Office 365 client libraries and SDKs.
-->

**Hinweis** Zur Vereinfachung des Verweises verwendet der Rest des Artikels **"Outlook.com" Diese Microsoft Kontendomänen enthalten**.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**In der Beta-Version der API nicht interessiert?** Verwenden Sie in der oberen rechten Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**Nicht interessiert v2. 0 der API?** Verwenden Sie in der rechten oberen Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

**Nicht in v1. 0 der API interessiert?** Verwenden Sie in der rechten oberen Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



## <a name="all-mail-api-operations"></a>Alle Mail API-Vorgänge

**Message-Vorgänge** Nachrichten werden in Postfachordner, gespeichert, sodass Nachricht Endpunkte oft den Ordner umfassen, der die Nachricht enthält.
Ein Ordner ist entweder durch ID oder durch einen der folgenden bekannten Ordnernamen angegeben: `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems`.

[Nachrichten abrufen](#GetMessages) | [Synchronisieren Nachrichten](#SynchronizeMessagesAPI) | [Erstellen und Senden von Nachrichten](#SendMessages) | [Antworten oder allen Antworten Nachrichten](#ReplyToMessages) | 
[neue oder abgeschrägten Weiterleiten von Nachrichten](#ForwardMessages) | [Nachrichten aktualisieren](#UpdateMessages) | [Löschen von Nachrichten](#DeleteMessages) | [verschieben oder Kopieren von Nachrichten](#MoveCopyMessages) |  
[Experten Posteingang verwalten](#ManageFocusedInbox) | [verwalten @-Mentions ](#ManageMentions) (Preview) | [Melden Sie sich ab](#Unsubscribe) (Vorschau) | [Abrufen von Einstellungen für automatische Antworten](#GetAutoReplySettings)  |  [Aktualisieren Automatische Antworten für](#UpdateAutoReplySettings) | 
[Erste e-Mail-Infos](#GetMailTips) (Preview) | [Abrufen von Anlagen](#GetAttachments)  | 
 [Erstellen Anlagen](#CreateAttachments) | [Anlagen löschen](#DeleteAttachments)


**Ordner Vorgänge** Postfachordner können Nachrichten und andere Ordner enthalten. Sie können erhalten möchten, erstellen Sie, ändern, löschen und Ordner verwalten.
Sie können die folgenden bekannten Ordnernamen statt der ID verwenden, an den entsprechenden Ordner: `Inbox`, `SentItems`, `Drafts`, oder `DeletedItems`.

[Abrufen von Ordnern](#GetFolders) | [Ordner synchronisieren](#SynchronizeFolders) | [Erstellen von Ordnern](#CreateFolders) | [Ordner aktualisieren](#UpdateFolders) | [Löschen von Ordnern](#DeleteFolders) | [verschieben oder Kopieren von Ordnern](#MoveCopyFolders)

Siehe auch:

[REST-API Nachricht Resource](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) | [REST API Folder-Ressource](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)

<a name="Overview"> </a>
## <a name="use-the-mail-rest-api"></a>Verwenden Sie die E-Mail-REST-API

###<a name="authentication"></a>Authentifizierung

Wie andere [Outlook-REST-API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)für jede Anforderung an die E-Mail-API sollten Sie eine gültige Zugriffstoken einbeziehen. Erste ein Zugriffstoken benötigen Sie registriert haben, Ihre app identifiziert und die entsprechende Autorisierung abgerufen. Sie können [Hier erfahren Sie mehr](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow) über einige optimierte Registrierung und Autorisierungsoptionen für die für Sie.
Beachten Sie dies, wie Sie mit der bestimmte Vorgänge in der Mail-API fortzufahren.

<a name="SupportedVersions"> </a>

###<a name="version-of-api"></a>Version der API

Die E-Mail-REST-API wird in allen Versionen von Outlook-REST-API unterstützt. Die Funktionalität kann je nach der bestimmten Version abweichen.

###<a name="target-user"></a>Zielbenutzer

Alle Mail-API-Anfragen werden im Namen des angemeldeten Benutzers ausgeführt, sofern nicht angegeben. Einige API-Teilmengen wie praxisorientierte Posteingang API können auf die angemeldeten Benutzer oder eine vom Benutzer angegebene einer Benutzer-ID, die entsprechenden Berechtigungen erteilt ausgeführt werden.

Weitere Informationen für alle Untermengen der Outlook-REST-API finden Sie unter [Verwendung der Outlook-REST-API](..\api\use-outlook-rest-api.md) .

****


<a name="GetMessages"> </a>
##<a name="get-messages"></a>Abrufen von Nachrichten

Sie können eine Nachricht-Auflistung oder eine einzelne Nachricht aus einem Postfachordner abrufen.

Jede Nachricht in der Antwort enthält mehrere Eigenschaften einschließlich [Body](..\api\complex-types-for-mail-contacts-calendar.md#MessageBody) -Eigenschaft. Nachrichtentext kann HTML oder Text sein. Wenn der Textkörper HTML, in der Standardeinstellung ist, würde vor potenziell unsicheren HTML-Code (beispielsweise JavaScript) in die **Body** -Eigenschaft eingebettet vor der Textkörperinhalt eine REST-Antwort zurückgegeben wird entfernt. Um die gesamte, ursprünglichen HTML Inhalte erhalten möchten, gehören Sie folgende HTTP-Anforderungsheaders:
```
Prefer: outlook.allow-unsafe-html
```

REST-API: [Abrufen einer Nachricht-Auflistung (REST)](#GetMessageCollection) | [eine Meldung (REST)](#GetMessage)

Client-Bibliotheken: [Abrufen einer Nachricht-Auflistung (Client)](#GetMessagesClient) | [Meldung (Client)](#GetMessageClient)

<a name="GetMessageCollection"> </a>
###<a name="get-a-message-collection-rest"></a>Abrufen einer Nachricht-Auflistung (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_ 
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

**Hinweis** Das Verhalten der Vorgänge in diesem Abschnitt variieren je nach Version. Erfahren Sie mehr durch Auswahl einer Version in der oberen rechten Ecke der Seite.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Abrufen einer Nachricht-Auflistung aus dem gesamten Postfach des (mit Ausnahme der Ordner Gelöschte Objekte und Unübersichtlichkeit) angemeldeten Benutzers.

```no-highlight
GET https://outlook.office.com/api/beta/me/messages
```

Sie können auch Geben Sie einen Ordner im Postfach des Benutzers und rufen Sie die Nachricht-Auflistung aus diesem Ordner.

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie Nachrichten aus einem bestimmten Ordner optimal nutzen.|

**Hinweis** Jede Nachricht in der Antwort enthält standardmäßig alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** soll nur die Eigenschaften **Absender** und **Betreff** jeder Nachricht in der Antwort zurückgegeben. Finden Sie in der Beispielantwort in [eine Meldung (REST)](#GetMessage) für eine vollständige Liste der Eigenschaften, die für eine Nachricht zurückgegeben wird, wenn Sie **$select**nicht verwenden.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/MailFolders/sentitems/messages/?$select=Sender,Subject
```

**Beispielantwort**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders('sentitems')/Messages(Sender,Subject)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIzAAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqS\"",
            "Id": "AAMkAGI2TIzAAAA=",
            "Subject": "Meeting Notes",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy-AAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
            "Id": "AAMkAGI2TIy-AAA=",
            "Subject": "Contract Signing",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy9AAA=')",
            "@odata.etag": "W/\"CwAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqJ\"",
            "Id": "AAMkAGI2TIy9AAA=",
            "Subject": "Rob:Alex 1:1",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Abrufen einer Nachricht-Auflistung aus dem gesamten Postfach des (mit Ausnahme der Ordner Gelöschte Objekte und Unübersichtlichkeit) angemeldeten Benutzers.

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages
```

Sie können auch Geben Sie einen Ordner im Postfach des Benutzers und rufen Sie die Nachricht-Auflistung aus diesem Ordner.

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/messages
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie Nachrichten aus einem bestimmten Ordner optimal nutzen.|

**Hinweis** Jede Nachricht in der Antwort enthält standardmäßig alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgende Beispiel veranschaulicht mit **$select** zurückgeben nur der **Absender** und **Betreff** Eigenschaften der einzelnen Nachrichten in der Antwort angegeben. Finden Sie in der Beispielantwort in [eine Meldung (REST)](#GetMessage) für eine vollständige Liste der Eigenschaften, die für eine Nachricht zurückgegeben wird, wenn Sie **$select**nicht verwenden.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders/sentitems/messages/?$select=Sender,Subject
```

**Beispielantwort**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('sentitems')/Messages(Sender,Subject)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIzAAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqS\"",
            "Id": "AAMkAGI2TIzAAAA=",
            "Subject": "Meeting Notes",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy-AAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
            "Id": "AAMkAGI2TIy-AAA=",
            "Subject": "Contract Signing",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy9AAA=')",
            "@odata.etag": "W/\"CwAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqJ\"",
            "Id": "AAMkAGI2TIy9AAA=",
            "Subject": "Rob:Alex 1:1",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Abrufen einer Nachricht-Auflistung aus dem Posteingang. 

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages
```

Sie können auch Geben Sie einen Ordner im Postfach des Benutzers und rufen Sie die Nachricht-Auflistung aus diesem Ordner.

```no-highlight
GET https://outlook.office.com/api/v1.0/me/MailFolders/{folder_id}/messages
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie Nachrichten aus einem bestimmten Ordner optimal nutzen.|

**Hinweis** Jede Nachricht in der Antwort enthält standardmäßig alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** zurückgeben nur der **Absender** und **Subject** -Eigenschaften jeder Nachricht in der Antwort angeben. Finden Sie in der Beispielantwort in [eine Meldung (REST)](#GetMessage) für eine vollständige Liste der Eigenschaften, die für eine Nachricht zurückgegeben wird, wenn Sie **$select**nicht verwenden.

[!code-REST-i[mail_api_get_message_collection](./_data/mail_api_get_message_collection.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) -Auflistung. 


****

<a name="GetMessage"> </a>
###<a name="get-a-message-rest"></a>Die Meldung (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Die Meldung nach ID.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=
```

**Beispielantwort**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz\"",
    "Id": "AAMkAGI2THVSAAA=",
    "CreatedDateTime": "2014-10-20T00:41:57Z",
    "LastModifiedDateTime": "2014-10-20T00:41:57Z",
    "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz",
    "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
    "Categories": [],
    "ReceivedDateTime": "2014-10-20T00:41:57Z",
    "SentDateTime": "2014-10-20T00:41:53Z",
    "HasAttachments": true,
    "Subject": "Re: Meeting Notes",
    "Body": {
        "ContentType": "Text",
        "Content": "\n________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP\n"
    },
    "BodyPreview": "________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP",
    "Importance": "Normal",
    "ParentFolderId": "AAMkAGI2AAEMAAA=",
    "Sender": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Alex D",
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
            }
        }
    ],
    "CcRecipients": [],
    "BccRecipients": [],
    "ReplyTo": [],
    "ConversationId": "AAQkAGI2yEto=",
    "ConversationIndex": "AQHRh3zqrkAcds2kw==",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": false,
    "IsDraft": false,
    "WebLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGI2THVSAAA%3D&exvsurl=1&viewmodel=ReadMessageItem"
}
```

 **Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der angegebenen Nachricht. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** nur die Eigenschaften **Absender** und den **Betreff** der Nachricht in der Antwort zurückgeben soll.

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1I5MTAAA=?$select=Sender,Subject
```



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=
```

**Beispielantwort**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz\"",
    "Id": "AAMkAGI2THVSAAA=",
    "CreatedDateTime": "2014-10-20T00:41:57Z",
    "LastModifiedDateTime": "2014-10-20T00:41:57Z",
    "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz",
    "Categories": [],
    "ReceivedDateTime": "2014-10-20T00:41:57Z",
    "SentDateTime": "2014-10-20T00:41:53Z",
    "HasAttachments": true,
    "Subject": "Re: Meeting Notes",
    "Body": {
        "ContentType": "Text",
        "Content": "\n________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP\n"
    },
    "BodyPreview": "________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP",
    "Importance": "Normal",
    "ParentFolderId": "AAMkAGI2AAEMAAA=",
    "Sender": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Alex D",
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
            }
        }
    ],
    "CcRecipients": [],
    "BccRecipients": [],
    "ReplyTo": [],
    "ConversationId": "AAQkAGI2yEto=",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": false,
    "IsDraft": false,
    "WebLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGI2THVSAAA%3D&exvsurl=1&viewmodel=ReadMessageItem"
}
```

 **Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der angegebenen Nachricht. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** soll nur die Eigenschaften **Absender** und den **Betreff** der Nachricht in der Antwort zurückgegeben.

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGE1I5MTAAA=?$select=Sender,Subject
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|

[!code-REST-i[mail_api_get_message_by_id](./_data/mail_api_get_message_by_id.json)]


 **Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der angegebenen Nachricht. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** nur die Eigenschaften **Absender** und den **Betreff** der Nachricht in der Antwort zurückgeben soll.

```
GET https://outlook.office.com/api/v1.0/me/messages/AAMkAGEI5MTAAA=?$select=Sender,Subject
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="GetMessagesClient"> </a>
###<a name="get-a-message-collection-client"></a>Abrufen einer Nachricht Auflistung (Client)

Abrufen von Nachrichten im Posteingang unter Verwendung der `Me.Messages` Kontextmenü-Eigenschaft. Verwenden Sie den Ordner **Nachrichten** -Eigenschaft, um die Nachrichten aus einem anderen Ordner erhalten möchten.
Sie können die folgenden bekannten Ordnernamen statt der ID verwenden, für den entsprechenden Ordner: `Inbox`; `SentItems`; `Drafts`; `DeletedItems`.

Beispiel:`outlookClient.Me.Folders["SentItems"].Messages.ExecuteAsync()`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


**Hinweis** Nachricht Websitesammlungen unterstützen Abfrageausdrücke wie **Wählen**, **OrderBy**und **Übernehmen**.

In diesem Beispiel wird die-Methode aufgerufen, [den Outlook-Client erstellt](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets"  data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
    var messages = await outlookClient.Me.Folders["Inbox"].Messages
      .OrderByDescending(m => m.DateTimeReceived)
      .Take(10)
      .ExecuteAsync();

foreach(var message in messages.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Message '{0}' received at '{1}'.",
    message.Subject,
    message.DateTimeReceived.ToString());
}

```
```javascript-i
outlookClient.me.folders.getFolder('Inbox').messages.getMessages().orderBy('DateTimeReceived desc').fetchAll(10).then(function (result) {
    result.forEach(function (message) {
        console.log('Message "' + message.subject + '" received at "' + message.dateTimeReceived.toString() + '"');
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="GetMessageClient"> </a>
###<a name="get-a-message-client"></a>Die Meldung (Client)

Um eine bestimmte Nachricht erhalten möchten, geben Sie die Nachrichten-ID als den Index der Auflistung **Nachrichten** oder verwenden Sie **GetById** -Methode.

****

<a name="SynchronizeMessagesAPI"></a>
##<a name="synchronize-messages"></a>Synchronisieren von Nachrichten

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Sie können Ihre lokalen Datenspeicher mit der Nachrichten auf dem Server synchronisieren. Synchronisierung der Nachricht ist ein pro Ordner Vorgang, beispielsweise können Sie Synchronisieren aller Nachrichten im Posteingang. Zum Synchronisieren von Nachrichten in einer Ordnerhierarchie müssen Sie jeden Ordner einzeln zu synchronisieren.

Die API unterstützt sowohl auf vollständige Synchronisierung starten, der alle Nachrichten in einem Ordner abruft und inkrementelle Synchronisierung, das alle Nachrichten werden abgerufen, die seit der letzten vollständigen Synchronisierung geändert haben.

Synchronisieren von einem e-Mail-Ordner in der Regel erfordert zwei oder mehr GET-Anforderungen. Sie stellen die GET anfordern viel wie die Sie [Nachrichten erhalten möchten](#GetMessages), außer dass Sie bestimmte Anforderungsheader und eine _DeltaToken_ oder _SkipToken_ bei Bedarf enthalten.

**Anforderungsheader**

- Sie müssen angeben, die _bevorzugen: odata.track Änderungen_ Kopfzeile in allen Synchronisierungsanfragen ausgenommen solche, die enthalten eine `skipToken` zurückgegeben wird, aus einer früheren Sync-Anforderung. Suchen Sie in der ersten Antwort, nach der _Einstellung angewendet: odata.track Änderungen_ Header zu bestätigen, dass die Ressource unterstützt synchronisieren, bevor Sie fortfahren.

- Geben Sie die _bevorzugen: odata.maxpagesize={x}_ Header So legen Sie die maximale Anzahl von Nachrichten fest, die in einer Anforderung zurückgegeben.

Hier ist eine typische Rundung der Synchronisierung von Nachrichten aus:

1. Erstellen die anfängliche GET-Anforderung mit der obligatorisch _bevorzugen: odata.track Änderungen_ Kopfzeile. Die erste Antwort auf eine Anforderung Sync gibt immer einen _DeltaToken_zurück. (Die zweiten und nachfolgenden GET-Anfragen unterscheiden sich von der ersten GET-Anforderung, einschließlich einer _DeltaToken_ oder einer _SkipToken_ in einer vorherigen Antwort erhalten.)

2. Wenn die erste Antwort zurückgibt der _Einstellung angewendet: odata.track Änderungen_ Kopfzeile, können Sie mit der Synchronisierung des Ordners fortfahren.

  - Stellen Sie eine zweite GET-Anforderung. Angeben der _bevorzugen: odata.track Änderungen_ Kopf- und der _DeltaToken_ von der ersten GET zu ermitteln, ob es keine weiteren Nachrichten sind zurückgegeben. Wenn weitere Nachrichten zur Verfügung stehen oder eine _DeltaToken_ vorhanden sind, wenn die letzte Nachricht in diesem Fall können Sie die Übertragung synchronisiert wurde, wird die zweite Anforderung zusätzliche Nachrichten und eine _SkipToken_ zurückgegeben.

  - Weiterhin synchronisieren durch das Senden eines Anrufs GET und einschließlich einer _SkipToken_ , die vom vorherigen Aufruf zurückgegeben wird. Beendet, wenn Sie eine endgültige Antwort erhalten, die enthält ein _@odata.deltaLink_ Kopfzeile mit einem _DeltaToken_ erneut, womit die Synchronisierung abgeschlossen ist.


### <a name="to-sync-messages-in-a-specific-folder"></a>Nachrichten in einen bestimmten Ordner synchronisieren

**Anfängliche Anforderung**

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages
```

**Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung**

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages/?$deltaToken={delta_token}
```

**Dritte oder nachfolgenden Anforderung in der gleichen runde**

Fahren Sie mit die nächste Sync-Anforderung senden, wenn die vorherige Antwort enthält eine `skipToken`. Beendet, wenn Sie eine Antwort erhalten, die enthält ein `@odata.deltaLink` Header mit einer `deltaToken` erneut.

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages/?$skipToken={skip_token}
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen|OData.Track Änderungen|Gibt an, dass die Anforderung einer synchronisierungsanforderung ist. Für die ersten 2 GET-Anfragen in einer Runde erforderlich.|
|Bevorzugen|OData.MaxPageSize|Legt die Anzahl der Nachrichten in der Antwort zurückgegeben werden soll. Optional|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen zu synchronisieren. Erforderlich.|
|deltaToken|String|Das Token, das die letzte Synchronisierung Anforderung für diesen Ordner identifiziert. Er wird zurückgegeben, im Rahmen des Werts für @odata.deltaLink in vorherigen Sync Antwort. Erforderlich für die zweite GET-Anforderung.|
|skipToken|String|Das Token, das angibt, dass weitere Nachrichten heruntergeladen werden. Erforderlich, wenn es als Teil des Werts für zurückgegeben wird @odata.nextLink in der vorherigen Antwort synchronisieren.|


Standardmäßig gibt die Synchronisierung alle Eigenschaften und alle Nachrichten in einem Ordner. Verwenden von einem Abfrageausdruck $select nur die Eigenschaften angeben, die die Notwendigkeit für eine optimale Leistung. Die _Id_ -Eigenschaft wird immer zurückgegeben. 

Synchronisierung unterstützt die Abfrageausdrücke $select, $top, $erweitern. Es ist eingeschränkter Unterstützung für $filter $orderby und keine Unterstützung für $search ein.

* Die einzige unterstützte $filter Expresssions sind "$filter = ReceivedDateTime + ge + {Wert}" oder "$filter = ReceivedDateTime + Gt + {Wert}".
* Ist der einzige unterstützte $orderby Ausdruck "$orderby = ReceivedDateTime + Desc". Wenn Sie einen $orderby Ausdruck nicht verwenden, wird die Rückgabereihenfolge nicht garantiert werden.
  
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Eine Auflistung mit der angeforderten Nachrichten und einem _DeltaToken_ oder _SkipToken_ , mit denen Sie zusätzliche Seiten aller Nachrichten vom Server für eine inkrementelle Synchronisierung anfordern. 




**Beispiel**

Das folgende Beispiel zeigt eine Reihe von Anforderungen an einen bestimmten Ordner synchronisieren, der Nachrichten 7 enthält. Gibt an, die erste Synchronisierung Anforderung zurückgeben 2 Nachrichten zu einem Zeitpunkt (_odata.maxpagesize_ ist 2), und nur die **Absender** und **Subject** -Eigenschaften für jede Nachricht.

- Die erste Antwort 2 Nachrichten gibt eine `deltaLink` und `deltaToken`. 
- Die zweite Anforderung verwendet, die `deltaToken`. Die zweite Antwort 2 Nachrichten gibt eine `nextLink` und `skipToken`.
- Verwenden Sie zur Durchführung der Synchronisierung die dritten und vierten Anforderungen der `skipToken` aus der vorherigen Sync-Anforderung zurückgegeben werden, bis die vierte Sync-Antwort zurückgegeben wird eine `deltaLink` und `deltaToken`, in diesem Fall dieses Round Synchronisierung abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung. 

**Beispiel für eine anfängliche Anforderung**

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages?$select=Subject,Sender HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```


**Erste Antwort-Beispieldaten**

Die erste Antwort enthält eine `Preference-Applied: odata.track-changes` Kopfzeile, was bedeutet, dass dieser Ordner unterstützt die Synchronisierung. Die Antwort enthält außerdem zwei Nachrichten und ein `deltaToken`.

```
Preference-Applied: odata.track-changes

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADPAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9+\"",
      "Id":"AAMkAGI5MAAAwXADPAAA=",
      "Subject":"Updates from All Company",
      "Sender":{
        "EmailAddress":{
          "Name":"Contoso Demo on Yammer",
          "Address":"noreply@yammer.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADVAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+E\"",
      "Id":"AAMkAGI5MAAAwXADVAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Alex Darrow",
          "Address":"AlexD@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA"
}
```

**Beispiel für eine zweite Anforderung**

Gibt an, die zweite Anforderung der `deltaToken` aus der vorherigen Antwort zurückgegeben.

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```

**Zweite Antwort-Beispieldaten**

Die zweite Antwort enthält zwei weitere Nachrichten und eine `skipToken`, der angibt, es sind weitere Nachrichten in den Ordner synchronisieren.

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADQAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9/\"",
      "Id":"AAMkAGI5MAAAwXADQAAA=",
      "Subject":"International Launch Planning for XT2000",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADUAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+D\"",
      "Id":"AAMkAGI5MAAAwXADUAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Anne Wallace",
          "Address":"AnneW@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA"
}
```

**Beispiel für eine dritte Anforderung**

Die Thirs anfordern, enthält der `skipToken` aus der vorherigen Antwort zurückgegeben.

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**Dritte Antwort-Beispieldaten**

Die dritte Antwort zurückgegeben, zwei weitere Nachrichten und ein weiteres `skipToken`, dennoch im Ordner synchronisieren Nachrichten vorhanden sind, der angibt.

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADTAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+C\"",
      "Id":"AAMkAGI5MAAAwXADTAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Pavel Bansky",
          "Address":"PavelB@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADSAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+B\"",
      "Id":"AAMkAGI5MAAAwXADSAAA=",
      "Subject":"Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA"
}
```

**Beispiel 4 Anforderung**

Die vierte Anforderung enthält den `skipToken` aus der vorherigen Antwort.

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**Vierte und letzte Antwort-Beispieldaten**

Die vierte Antwort die einzige verbleibende Nachricht in den Ordner zurückgegeben und einer `deltaToken` womit Synchronisierung für diesen Ordner abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung für diesen Ordner.

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADRAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+A\"",
      "Id":"AAMkAGI5MAAAwXADRAAA=",
      "Subject":"Data sheets for the XT2000 ",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink": "https://outlook.office365.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24deltaToken=0_zCBD5nm2dcGAFGk5qypL1PSyEAADBb9RkEAAAA"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Sie können Ihre lokalen Datenspeicher mit der Nachrichten auf dem Server synchronisieren. Synchronisierung der Nachricht ist ein pro Ordner Vorgang, beispielsweise können Sie Synchronisieren aller Nachrichten im Posteingang. Zum Synchronisieren von Nachrichten in einer Ordnerhierarchie müssen Sie jeden Ordner einzeln zu synchronisieren.

Die API unterstützt sowohl auf vollständige Synchronisierung starten, der alle Nachrichten in einem Ordner abruft und inkrementelle Synchronisierung, das alle Nachrichten werden abgerufen, die seit der letzten vollständigen Synchronisierung geändert haben.

Synchronisieren von einem e-Mail-Ordner in der Regel erfordert zwei oder mehr GET-Anforderungen. Sie stellen die GET anfordern viel wie die Sie [Nachrichten erhalten möchten](#GetMessages), außer dass Sie bestimmte Anforderungsheader und eine _DeltaToken_ oder _SkipToken_ bei Bedarf enthalten.

**Anforderungsheader**

- Geben Sie die _bevorzugen: odata.track Änderungen_ Kopfzeile in alle Synchronisierungsanfragen, ausgenommen solche, die enthalten eine `skipToken` aus einer früheren Sync-Anforderung zurückgegeben wird. Suchen Sie in der ersten Antwort, nach der _Einstellung angewendet: odata.track Änderungen_ Header zu bestätigen, dass die Ressource unterstützt synchronisieren, bevor Sie fortfahren.

- Geben Sie die _bevorzugen: odata.maxpagesize={x}_ Header So legen Sie die maximale Anzahl von Nachrichten fest, die in einer Anforderung zurückgegeben.

Hier ist eine typische Rundung der Synchronisierung von Nachrichten aus:

1. Erstellen die anfängliche GET-Anforderung mit der obligatorisch _bevorzugen: odata.track Änderungen_ Kopfzeile. Die erste Antwort auf eine Anforderung Sync gibt immer einen _DeltaToken_zurück. (Die zweiten und nachfolgenden GET-Anfragen unterscheiden sich von der ersten GET-Anforderung, einschließlich einer _DeltaToken_ oder einer _SkipToken_ in einer vorherigen Antwort erhalten.)

2. Wenn die erste Antwort zurückgibt der _Einstellung angewendet: odata.track Änderungen_ Kopfzeile, können Sie mit der Synchronisierung des Ordners fortfahren.

  - Stellen Sie eine zweite GET-Anforderung. Angeben der _bevorzugen: odata.track Änderungen_ Kopf- und der _DeltaToken_ von der ersten GET zu ermitteln, ob es keine weiteren Nachrichten sind zurückgegeben. Wenn weitere Nachrichten zur Verfügung stehen oder eine _DeltaToken_ vorhanden sind, wenn die letzte Nachricht in diesem Fall können Sie die Übertragung synchronisiert wurde, wird die zweite Anforderung zusätzliche Nachrichten und eine _SkipToken_ zurückgegeben.

  - Weiterhin synchronisieren durch das Senden eines Anrufs GET und einschließlich einer _SkipToken_ , die vom vorherigen Aufruf zurückgegeben wird. Beendet, wenn Sie eine endgültige Antwort erhalten, die enthält ein _@odata.deltaLink_ Kopfzeile mit einem _DeltaToken_ erneut, womit die Synchronisierung abgeschlossen ist.


### <a name="to-sync-messages-in-a-specific-folder"></a>Nachrichten in einen bestimmten Ordner synchronisieren

**Anfängliche Anforderung**

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages
```

**Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung**

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages/?$deltaToken={delta_token}
```

**Dritte oder nachfolgenden Anforderung in der gleichen runde**

Fahren Sie mit die nächste Sync-Anforderung senden, wenn die vorherige Antwort enthält eine `skipToken`. Beendet, wenn Sie eine Antwort erhalten, die enthält ein `@odata.deltaLink` Header mit einer `deltaToken` erneut.

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages/?$skipToken={skip_token}
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen|OData.Track Änderungen|Gibt an, dass die Anforderung einer synchronisierungsanforderung ist. Für die ersten 2 GET-Anfragen in einer Runde erforderlich.|
|Lieber|OData.MaxPageSize|Legt die Anzahl der Nachrichten in der Antwort zurückgegeben werden soll. Optional|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen zu synchronisieren. Erforderlich.|
|deltaToken|String|Das Token, das die letzte Synchronisierung Anforderung für diesen Ordner identifiziert. Es wird als Teil des Werts für zurückgegeben @odata.deltaLink in vorherigen Sync Antwort. Erforderlich für die zweite GET-Anforderung.|
|skipToken|String|Das Token, das angibt, dass es weitere Nachrichten sind heruntergeladen. Erforderlich, wenn es als Teil des Werts für zurückgegeben wird @odata.nextLink in der vorherigen Antwort synchronisieren.|


Standardmäßig gibt die Synchronisierung alle Eigenschaften und alle Nachrichten in einem Ordner. Verwenden Sie einen $select Abfrageausdruck nur die Eigenschaften angeben, die Notwendigkeit für eine optimale Leistung. Die _Id_ -Eigenschaft wird immer zurückgegeben. 

Synchronisierung unterstützt die Abfrageausdrücke $select, $top, $erweitern. Es ist eingeschränkter Unterstützung für $filter $orderby und keine Unterstützung für $search ein.

* Die einzige unterstützte $filter Expresssions sind "$filter = ReceivedDateTime + ge + {Wert}" oder "$filter = ReceivedDateTime + Gt + {Wert}".
* Ist der einzige unterstützte $orderby Ausdruck "$orderby = ReceivedDateTime + Desc". Wenn Sie einen $orderby Ausdruck nicht verwenden, wird die Rückgabereihenfolge nicht garantiert werden.
  
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Eine Auflistung mit der angeforderten Nachrichten und einem _DeltaToken_ oder _SkipToken_ , mit denen Sie zusätzliche Seiten aller Nachrichten vom Server für eine inkrementelle Synchronisierung anfordern. 




**Beispiel**

Das folgende Beispiel zeigt eine Reihe von Anforderungen an einen bestimmten Ordner synchronisieren, der Nachrichten 7 enthält. Gibt an, die erste Synchronisierung Anforderung zurückgeben 2 Nachrichten zu einem Zeitpunkt (_odata.maxpagesize_ ist 2), und nur die **Absender** und **Subject** -Eigenschaften für jede Nachricht.

- Die erste Antwort 2 Nachrichten gibt eine `deltaLink` und `deltaToken`. 
- Die zweite Anforderung verwendet, die `deltaToken`. Die zweite Antwort 2 Nachrichten gibt eine `nextLink` und `skipToken`.
- Verwenden Sie zur Durchführung der Synchronisierung die dritten und vierten Anforderungen der `skipToken` aus der vorherigen Sync-Anforderung zurückgegeben werden, bis die vierte Sync-Antwort zurückgegeben wird eine `deltaLink` und `deltaToken`, in diesem Fall dieses Round Synchronisierung abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung. 

**Beispiel für eine anfängliche Anforderung**

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages?$select=Subject,Sender HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```


**Erste Antwort-Beispieldaten**

Die erste Antwort enthält eine `Preference-Applied: odata.track-changes` Header, was bedeutet, dass dieser Ordner unterstützt die Synchronisierung. Die Antwort enthält außerdem zwei Nachrichten und ein `deltaToken`.

```
Preference-Applied: odata.track-changes

{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADPAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9+\"",
      "Id":"AAMkAGI5MAAAwXADPAAA=",
      "Subject":"Updates from All Company",
      "Sender":{
        "EmailAddress":{
          "Name":"Contoso Demo on Yammer",
          "Address":"noreply@yammer.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADVAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+E\"",
      "Id":"AAMkAGI5MAAAwXADVAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Alex Darrow",
          "Address":"AlexD@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA"
}
```

**Beispiel für eine zweite Anforderung**

Gibt an, die zweite Anforderung der `deltaToken` aus der vorherigen Antwort zurückgegeben.

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```

**Zweite Antwort-Beispieldaten**

Die zweite Antwort enthält zwei weitere Nachrichten und ein `skipToken`, der angibt, es sind weitere Nachrichten im Ordner synchronisieren.

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADQAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9/\"",
      "Id":"AAMkAGI5MAAAwXADQAAA=",
      "Subject":"International Launch Planning for XT2000",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADUAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+D\"",
      "Id":"AAMkAGI5MAAAwXADUAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Anne Wallace",
          "Address":"AnneW@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA"
}
```

**Beispiel für eine dritte Anforderung**

Die Thirs anfordern, enthält der `skipToken` aus der vorherigen Antwort zurückgegeben.

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**Dritte Antwort-Beispieldaten**

Die dritte Antwort zurückgegeben, zwei weitere Nachrichten und ein weiteres `skipToken`, dennoch im Ordner synchronisieren Nachrichten vorhanden sind, der angibt.

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADTAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+C\"",
      "Id":"AAMkAGI5MAAAwXADTAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Pavel Bansky",
          "Address":"PavelB@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADSAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+B\"",
      "Id":"AAMkAGI5MAAAwXADSAAA=",
      "Subject":"Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA"
}
```

**Beispiel 4 Anforderung**

Die vierte Anforderung enthält den `skipToken` aus der vorherigen Antwort.

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**Vierte und letzte Antwort-Beispieldaten**

Die vierte Antwort die einzige verbleibende Nachricht in den Ordner zurückgegeben und einer `deltaToken` womit Synchronisierung für diesen Ordner abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung für diesen Ordner.

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADRAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+A\"",
      "Id":"AAMkAGI5MAAAwXADRAAA=",
      "Subject":"Data sheets for the XT2000 ",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink": "https://outlook.office365.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24deltaToken=0_zCBD5nm2dcGAFGk5qypL1PSyEAADBb9RkEAAAA"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in V2. 0 und der Beta-Version verfügbar. Weitere Informationen erhalten, verwenden Sie das Steuerelement in der oberen rechten Ecke des Artikels aus, und wählen Sie eine der beiden Versionen.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="SendMessages"> </a>
##<a name="create-and-send-messages"></a>Erstellen und Senden von Nachrichten

Senden Sie eine neue Nachricht im laufenden Betrieb, oder erstellen den Entwurf einer Nachricht, und senden Sie sie. Sie können in jedem Ordner Entwürfe erstellen.

REST-API: [Senden einer neuen Nachricht, die dynamisch (REST)](#SendMessageOnTheFly) | [Erstellen den Entwurf einer Nachricht (REST)](#CreateNewDraft) | [Senden Sie den Entwurf einer Nachricht (REST)](#SendDraftMessages)

Client-Bibliotheken: [senden eine neue Nachricht, die dynamisch (Client)](#SendMessageOnTheFlyClient) | [Erstellen den Entwurf einer Nachricht (Client)](#CreateDraftClient) | [Senden Sie den Entwurf einer Nachricht (Client)](#SendDraftClient)


<a name="SendMessageOnTheFly"> </a>
###<a name="send-a-new-message-on-the-fly-rest"></a>Senden Sie eine neue Nachricht, die dynamisch (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

Sendet die Nachricht im Textkörper Anforderung mithilfe der **SendMail** -Methode angegeben. Sie können einen oder enthalten weitere Anlagen in die gleiche Aktion aufrufen, indem sie in der **Attachments** -Auflistung-Eigenschaft angeben. Sie können auch die Nachricht im Ordner "Gesendete Elemente" speichern.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/sendmail
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Textkörper-Parameter_|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Die zu sendende Nachricht.|
|SavetoSentItems|boolean|Gibt an, ob die Nachricht in gesendete Objekte gespeichert. Der Standardwert ist **true**.|

Geben Sie den Parameter **Nachricht** , mit der erforderlichen **ToRecipients** -Eigenschaft und alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.
Der Parameter **SaveToSentItems** ist erforderlich, wenn **false**.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/sendmail
Content-Type: application/json

{
  "Message": {
    "Subject": "Meet for lunch?",
    "Body": {
      "ContentType": "Text",
      "Content": "The new cafeteria is open."
    },
    "ToRecipients": [
      {
        "EmailAddress": {
          "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "Name": "menu.md",
        "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "SaveToSentItems": "false"
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/sendmail
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Textkörper-Parameter_|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Die zu sendende Nachricht.|
|SavetoSentItems|boolean|Gibt an, ob die Nachricht in gesendete Objekte gespeichert. Der Standardwert ist **true**.|

Geben Sie den Parameter **Nachricht** , mit der erforderlichen **ToRecipients** -Eigenschaft und alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.
Der Parameter **SaveToSentItems** ist erforderlich, wenn **false**.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/sendmail

{
  "Message": {
    "Subject": "Meet for lunch?",
    "Body": {
      "ContentType": "Text",
      "Content": "The new cafeteria is open."
    },
    "ToRecipients": [
      {
        "EmailAddress": {
          "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "Name": "menu.md",
        "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "SaveToSentItems": "false"
}

```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/sendmail
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Textkörper-Parameter_|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Die zu sendende Nachricht.|
|SavetoSentItems|boolean|Gibt an, ob die Nachricht in gesendete Objekte gespeichert. Der Standardwert ist **true**.|

Geben Sie den Parameter **Nachricht** , mit der erforderlichen **ToRecipients** -Eigenschaft und alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.
Der Parameter **SaveToSentItems** ist erforderlich, wenn **false**.

[!code-REST-i[mail_api_sendmail](./_data/mail_api_sendmail.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="CreateNewDraft"> </a>
###<a name="create-a-draft-message-rest"></a>Erstellen Sie den Entwurf einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Erstellen Sie einen Entwurf für eine neue Nachricht. Entwürfe können in alle Ordner und optional vor dem [Senden](#SendDraftMessages) [aktualisiert](#UpdateMessages) erstellt werden.
Verwenden Sie zum Ordner "Entwürfe" speichern, die `/me/messages` Verknüpfung.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die Ziel-Ordner-ID oder die `Inbox` oder `Drafts` bekannte Ordnername.|

Geben Sie alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/MailFolders/inbox/messages
Content-Type: application/json

{
  "Subject": "Did you see last night's game?",
  "Importance": "Low",
  "Body": {
    "ContentType": "HTML",
    "Content": "They were <b>awesome</b>!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k0AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5\"",
  "Id": "AAMkAGE0Mz7k0AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5",
  "Categories": [],
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "CreatedDateTime": "2014-10-18T20:06:51Z",
  "LastModifiedDateTime": "2014-10-18T20:06:51Z",
  "Subject": "Did you see last night's game?",
  "BodyPreview": "They were awesome!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nThey were <b>awesome</b>!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Low",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mpv2hisc=",
  "ConversationIndex": "AQHRf4zqrkAcds2kw==",
  "ReceivedDateTime": "2014-10-18T20:06:51Z",
  "SentDateTime": "2014-10-18T20:06:51Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/messages
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die Ziel-Ordner-ID oder die `Inbox` oder `Drafts` bekannte Ordnername.|

Geben Sie alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/inbox/messages
Content-Type: application/json

{
  "Subject": "Did you see last night's game?",
  "Importance": "Low",
  "Body": {
    "ContentType": "HTML",
    "Content": "They were <b>awesome</b>!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k0AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5\"",
  "Id": "AAMkAGE0Mz7k0AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T20:06:51Z",
  "LastModifiedDateTime": "2014-10-18T20:06:51Z",
  "Subject": "Did you see last night's game?",
  "BodyPreview": "They were awesome!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nThey were <b>awesome</b>!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Low",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mpv2hisc=",
  "ReceivedDateTime": "2014-10-18T20:06:51Z",
  "SentDateTime": "2014-10-18T20:06:51Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/messages
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die Ziel-Ordner-ID oder die `Inbox` oder `Drafts` bekannte Ordnername.|

Geben Sie alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

[!code-REST-i[mail_api_create_message_in_folder](./_data/mail_api_create_message_in_folder.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **Antworttyp**

Der Entwurf einer [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

****

<a name="SendDraftMessages"> </a>
###<a name="send-a-draft-message-rest"></a>Senden Sie den Entwurf einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

Senden Sie einen [Entwurf für neue Nachricht](#CreateNewDraft), eine [Antwort Entwurf](#CreateReplyDraft), [allen Empfängern antworten möchten Entwurf](#CreateReplyAllDraft)oder [Forward Entwurf](#CreateForwardDraft) mithilfe der Methode zum **Senden** .
Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/send
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID des den Entwurf einer Nachricht zu senden.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz7k0AAA=/send
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/send
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID des den Entwurf einer Nachricht zu senden.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz7k0AAA=/send
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/send
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID des den Entwurf einer Nachricht zu senden.|

[!code-REST-i[mail_api_send_message_by_id](./_data/mail_api_send_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="SendMessageOnTheFlyClient"> </a>
###<a name="send-a-new-message-on-the-fly-client"></a>Senden Sie eine neue Nachricht im laufenden Betrieb (Client)

Erstellen Sie eine Nachricht ein, und geben Sie ihn an die **SendMailAsync** -Methode.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
ItemBody body = new ItemBody
{
    Content = "It was <b>awesome</b>!",
    ContentType = BodyType.HTML
};
List<Recipient> toRecipients = new List<Recipient>();
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"
    }
});
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "pavelb@a830edad9050849NDA1.onmicrosoft.com"
    }
});
Message newMessage = new Message
{
    Subject = "Did you see last night's game?",
    Body = body,
    ToRecipients = toRecipients
};

// To send a message without saving to Sent Items, specify false for  
// the SavetoSentItems parameter.
await outlookClient.Me.SendMailAsync(newMessage, true);
```

<!-- ENDSECTION -->

****

<a name="CreateDraftClient"> </a>
###<a name="create-a-draft-message-client"></a>Erstellen Sie den Entwurf einer Nachricht (Client)

Erstellen Sie den Entwurf einer Nachricht, und übergeben sie an die **AddMessageAsync** -Methode. Dann können Sie [den Entwurf zu aktualisieren](#UpdateMessagesClient) und [Senden](#SendDraftClient).


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
ItemBody body = new ItemBody
{
    Content = "I'm coming out a week later.",
    ContentType = BodyType.HTML
};
List<Recipient> toRecipients = new List<Recipient>();
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"
    }
});
Message draftMessage = new Message
{
    Subject = "Changed my travel plans",
    Body = body,
    ToRecipients = toRecipients,
    Importance = Importance.High
};

// Save the draft message. Saving to Me.Messages saves the message in the Drafts folder.
await outlookClient.Me.Messages.AddMessageAsync(draftMessage);

// Get the ID of the message.
string messageId = draftMessage.Id;
```

<!-- ENDSECTION -->

Hinzufügen einer Nachricht zur **Me.Messages** -Auflistung speichert den Entwurf im Ordner "Entwürfe", aber Sie können einen Entwurf speichern, in der **Nachrichten** -Auflistung eines beliebigen Ordners.

Beispiel:`outlookClient.Me.Folders["AAMkADE3N..."].Messages.AddMessageAsync(newMessage)`

****

<a name="SendDraftClient"> </a>
###<a name="send-a-draft-message-client"></a>Senden Sie den Entwurf einer Nachricht (Client)

Senden Sie den Entwurf einer Nachricht, indem **SendAsync**aufrufen. Sie können einen Entwurf eines neuen, Antworten, allen Antworten senden oder Weiterleiten der Nachricht.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
await outlookClient.Me.Messages[messageId].SendAsync();
```

<!-- ENDSECTION -->

****

<a name="ReplyToMessages"> </a>
##<a name="reply-or-reply-all-to-messages"></a>Antworten oder allen Antworten auf Nachrichten

**Hinweis** Das Verhalten der Vorgänge in diesem Abschnitt variieren je nach Version. Erfahren Sie mehr durch Auswahl einer Version in der oberen rechten Ecke der Seite.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Antworten auf eine Nachricht, fügen Sie einen Kommentar hinzu, oder aktualisieren Nachrichteneigenschaften, die alle in einem einzigen Aufruf, oder Sie zuerst ein Update Nachrichteneigenschaften in einem anrufen, und klicken Sie dann senden und Antwort Entwurf erstellen können.

Sie können nur dem Absender der Nachricht oder eine Antwort an alle Empfänger gleichzeitig Antworten.


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Sie können mit einem Kommentar-Hauptfensters auf die Antworten, oder Sie können zuerst erstellen Sie einen Entwurf Antwort, und klicken Sie dann aktualisieren, und senden Sie den Entwurf.
Sie können nur dem Absender der Nachricht oder eine Antwort an alle Empfänger gleichzeitig Antworten.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Sie können mit einem Kommentar-Hauptfensters auf die Antworten, oder Sie können zuerst erstellen Sie einen Entwurf Antwort, und klicken Sie dann aktualisieren, und senden Sie den Entwurf.
Sie können nur dem Absender der Nachricht oder eine Antwort an alle Empfänger gleichzeitig Antworten.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


REST-API: [Antwort an den Absender, die dynamisch (REST)](#ReplyToSender) | [Antwort auf die dynamisch (REST)](#ReplyAll) | [erstellen eine Antwortnachricht Entwurf (REST)](#CreateReplyDraft) | [Entwurf allen Antworten - Nachricht (REST) erstellen](#CreateReplyAllDraft)

Client-Bibliotheken: [Antworten oder Antworten auf die dynamisch (Client)](#ReplyOnTheFlyClient) | [erstellen eine Antwort Entwurf oder Entwurf allen Antworten - Nachricht (Client)](#CreateDraftReplyClient)

<a name="ReplyToSender"> </a>
###<a name="reply-to-sender-on-the-fly-rest"></a>Absender, die dynamisch (REST) Antworten

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Antwort an den Absender einer Nachricht, Hinzufügen eines Kommentars oder [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) alle in einem einzigen Aufruf der **Antwort** zu ändern. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ können Sie zunächst [den Entwurf einer Antwortnachricht erstellen](#CreateReplyDraft) zum Einschließen eines Kommentars oder aktualisieren Sie alle Eigenschaften der Nachricht, und die Antwort zu [Senden](#SendDraftMessages) .


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/reply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften, die in der Antwortnachricht aktualisiert. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Wenn **ReplyTo** angegeben wird, in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)), sollten Sie die Antwort an den Empfänger in **ReplyTo** und nicht den Empfänger in **aus**senden. 


**Beispiel für eine Anforderung**

Das folgende Beispiel enthält einen Kommentar und Antwortnachricht einen Empfänger hinzugefügt.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/reply
Content-Type: application/json

{
  "Message":{  
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"fannyd@contoso.onmicrosoft.com",
          "Name":"Fanny Downs"
        }
      },
      {
        "EmailAddress":{
          "Address":"randiw@contoso.onmicrosoft.com",
          "Name":"Randi Welch"
        }
      }
     ]
  },
  "Comment": "Fanny, Randi, would you name the group please?" 
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Antworten Sie an den Absender einer Nachricht, durch die Angabe eines Kommentars und die **Reply** -Methode verwenden. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Auch wenn Sie [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) zur Beantwortung ändern müssen, können Sie zunächst [den Entwurf einer Antwortnachricht erstellen](#CreateReplyDraft), [Aktualisieren Sie](#UpdateMessages) die Nachricht Eigenschaften, und [Senden](#SendDraftMessages) Sie die Antwort.

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/reply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/reply
Content-Type: application/json

{
  "Comment": "Sounds great! See you tomorrow."
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Antworten Sie an den Absender einer Nachricht, durch die Angabe eines Kommentars und die **Reply** -Methode verwenden. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Auch wenn Sie [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) zur Beantwortung ändern müssen, können Sie zunächst [den Entwurf einer Antwortnachricht erstellen](#CreateReplyDraft), [Aktualisieren Sie](#UpdateMessages) die Nachricht Eigenschaften, und [Senden](#SendDraftMessages) Sie die Antwort.

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/reply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

[!code-REST-i[mail_api_send_reply_by_id](./_data/mail_api_send_reply_by_id.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="ReplyAll"> </a>
###<a name="reply-all-on-the-fly-rest"></a>Antworten Sie auf die dynamisch (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Antworten Sie an alle Empfänger einer Nachricht durch einen Kommentar angeben, und ändern beliebige [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) für die Antwort alle mithilfe der **ReplyAll** -Methode. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ können Sie zunächst [den Entwurf einer allen Antworten - Nachricht zu erstellen](#CreateReplyAllDraft) , um einen Kommentar enthalten und aktualisieren alle Eigenschaften der Nachricht, und [Senden](#SendDraftMessages) Sie die Antwort.


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/replyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften, in die allen Antworten-Nachricht zu aktualisieren. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Wenn **ReplyTo** angegeben wird, in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)), sollte Sie die Antwort auf die Empfänger in **ReplyTo** und **ToRecipients**und nicht die Empfänger in **aus** und **ToRecipients**senden. 


**Beispiel für eine Anforderung**

Im folgende Beispiel enthält einen Kommentar und fügt eine Anlage, die allen Antworten-Nachricht.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/ReplyAll
Content-Type: application/json

{
    "Message":{
      "Attachments": [ 
        { 
          "@odata.type": "#Microsoft.OutlookServices.FileAttachment", 
          "Name": "guidelines.md", 
          "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "Comment": "Please take a look at the attached guidelines before you decide on the name." 
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Antworten Sie an alle Empfänger einer Nachricht durch Angeben eines Kommentars und die **ReplyAll** -Methode. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Auch wenn Sie alle [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) zur Beantwortung ändern müssen, können Sie zunächst [den Entwurf einer allen Antworten - Nachricht zu erstellen](#CreateReplyAllDraft), [Aktualisieren Sie](#UpdateMessages) die Nachricht Eigenschaften, und die Antwort zu [Senden](#SendDraftMessages) .

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/replyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0MSz8DmAAA=/replyall
Content-Type: application/json

{
  "Comment": "Thanks for the heads up."
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Antworten Sie an alle Empfänger einer Nachricht durch Angeben eines Kommentars und die **ReplyAll** -Methode. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ müssen Sie alle [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) für die Antwort zu ändern, können Sie zunächst [den Entwurf allen Antworten - Nachricht erstellen](#CreateReplyAllDraft), [Aktualisieren](#UpdateMessages) die Nachricht Eigenschaften, und die Antwort zu [Senden](#SendDraftMessages) .


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/replyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

[!code-REST-i[mail_api_send_reply_all_by_id](./_data/mail_api_send_reply_all_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="CreateReplyDraft"> </a>
###<a name="create-a-draft-reply-message-rest"></a>Erstellen Sie eine Antwortnachricht Entwurf (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Erstellen Sie einen Entwurf für die Antwortnachricht eingeschlossen einen Kommentar oder aktualisieren Sie die [Eigenschaften der Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) in einem einzigen Aufruf von **CreateReply** . Anschließend können Sie den Entwurf einer Nachricht [Senden](#SendDraftMessages) .


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/createreply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften, die in der Antwortnachricht aktualisiert. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Wenn **ReplyTo** angegeben wird, in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)), sollten Sie die Antwort an Empfänger in **ReplyTo**und nicht die Empfänger in **aus**senden. 


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird einen Antwort Entwurf erstellt, fügt einen Kommentar und einem Empfänger im Textkörper Anforderung.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Message":{  
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"fannyd@contoso.onmicrosoft.com",
          "Name":"Fanny Downs"
        }
      },
      {
        "EmailAddress":{
          "Address":"randiw@contoso.onmicrosoft.com",
          "Name":"Randi Welch"
        }
      }
     ]
  },
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBHStBQ=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Erstellen Sie ein Entwurfs oder eine Antwortnachricht durch Aufrufen von **CreateReply** einen Kommentar hinzufügen. Anschließend können Sie das [Aktualisieren](#UpdateMessages) der [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) und [Senden](#SendDraftMessages) der Entwurf.

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createreply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [ ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Erstellen Sie ein Entwurfs oder eine Antwortnachricht durch Aufrufen von **CreateReply** einen Kommentar hinzufügen. Anschließend können Sie das [Aktualisieren](#UpdateMessages) der [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) und [Senden](#SendDraftMessages) der Entwurf.

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createreply
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu antworten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [ ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




 **Antworttyp**

Der Entwurf Reply- [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) mit der **ToRecipient**, **IsDraft**und anderen geeigneten Eigenschaften vorausgefüllt.

****


<a name="CreateReplyAllDraft"> </a>
###<a name="create-a-draft-reply-all-message-rest"></a>Erstellen Sie eine Entwurf allen Antworten-Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Erstellen Sie ein Entwurfs oder allen Antworten-Nachricht enthalten einen Kommentar oder aktualisieren Sie die [Eigenschaften der Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties), alle in einem **CreateReplyAll** Aufruf an. Anschließend können Sie den Entwurf einer Nachricht [Senden](#SendDraftMessages) .


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/createreplyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der zu allen Antworten-Nachricht an.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften, in die allen Antworten-Nachricht zu aktualisieren. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Wenn **ReplyTo** in der ursprünglichen Nachricht pro Internet-Nachrichtenformat ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)) angegeben wird, sollten Sie die Antwort an den Empfänger in den **ReplyTo** und **ToRecipients** -Eigenschaften und nicht die Empfänger in den Eigenschaften **von** und **ToRecipients** senden. 


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird einen Entwurf, wenn Sie alle Antworten erstellt und fügt eine Anlage und Kommentar alle in einem **CreateReplyAll** Aufruf.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/createreplyall
Content-Type: application/json

{
    "Message":{
      "Attachments": [ 
        { 
          "@odata.type": "#Microsoft.OutlookServices.FileAttachment", 
          "Name": "guidelines.md", 
          "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "Comment": "if the project gets approved, please take a look at the attached guidelines before you decide on the name." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKpAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DP\"",
  "Id": "AAMkADA1MTAAAH5JKpAAA=",
  "CreatedDateTime": "2016-03-15T08:37:34Z",
  "LastModifiedDateTime": "2016-03-15T08:37:34Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:37:34Z",
  "SentDateTime": "2016-03-15T08:37:34Z",
  "HasAttachments": true,
  "InternetMessageId": "<DM2PR00MB005732BE05BD669AC7CE056EF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body dir=\"ltr\">\r\nif the project gets approved, please take a look at the attached guidelines before you decide on the name.\r\n<b>From:</b> Admin<br>\r\n<b>Sent:</b> Tuesday, March 15, 2016 6:36:32 AM<br>\r\n<b>To:</b> Fanny Downs; Randi Welch<br>\r\n<b>Subject:</b> RE: Let's start a group\r\n<div>Fanny, Randi, would you name the group please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "if the project gets approved, please take a look at the attached guidelines before you decide on the name.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:36:32 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubj",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBGx9qGAACHRQA==",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKpAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Erstellen Sie ein Entwurfs oder eine allen Antworten-Nachricht durch Aufrufen von **CreateReplyAll** einen Kommentar hinzufügen. Sie können dann [Aktualisieren](#UpdateMessages) [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) und den Entwurf zu [Senden](#SendDraftMessages) .

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createreplyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der zu allen Antworten-Nachricht an.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createreplyall
Content-Type: application/json

{
    "Comment": "If the project gets approved, please decide on the name." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k5AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF\"",
  "Id": "AAMkAGE0Mz7k5AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T21:21:06Z",
  "LastModifiedDateTime": "2014-10-18T21:21:06Z",
  "Subject": "RE: Check out the new Office 365 APIs",
  "BodyPreview": "If the project gets approved, please decide on the name.\r\n_________________________________\r\nFrom: Alex D\r\nSent: Saturday, October 18, 2014 9:18:18 PM\r\nTo: Katie Jordan; Garth Fort\r\nSubj",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2014-10-18T21:21:06Z",
  "SentDateTime": "2014-10-18T21:21:06Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createreplyall
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der zu allen Antworten-Nachricht an.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createreplyall
Content-Type: application/json

{
    "Comment": "If the project gets approved, please decide on the name." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k5AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF\"",
  "Id": "AAMkAGE0Mz7k5AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T21:21:06Z",
  "LastModifiedDateTime": "2014-10-18T21:21:06Z",
  "Subject": "RE: Check out the new Office 365 APIs",
  "BodyPreview": "If the project gets approved, please decide on the name.\r\n_________________________________\r\nFrom: Alex D\r\nSent: Saturday, October 18, 2014 9:18:18 PM\r\nTo: Katie Jordan; Garth Fort\r\nSubj",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2014-10-18T21:21:06Z",
  "SentDateTime": "2014-10-18T21:21:06Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **Antworttyp**

Der Entwurf allen Antworten- [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) mit der **ToRecipient**, **IsDraft**und anderen geeigneten Eigenschaften vorausgefüllt.

****

<a name="ReplyOnTheFlyClient"></a>
###<a name="reply-or-reply-all-on-the-fly-client"></a>Antworten oder Antworten auf die dynamisch (Client)

Antworten Sie direkt an den Absender der Nachricht oder allen Empfängern durch Aufrufen von **ReplyAsync** oder **ReplyAllAsync** und in einem Kommentar übergeben.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
await outlookClient.Me.Messages[messageId].ReplyAsync("Count me in.");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
await outlookClient.Me.Messages[messageId].ReplyAllAsync("Count me in.");
```

<!-- ENDSECTION -->

<a name="CreateDraftReplyClient"> </a>
###Erstellen Sie eine Entwurf Antworten oder allen Antworten-Nachricht für die Entwurf (Client)

Erstellen Sie einen Entwurf Antworten oder ReplyAll Nachricht durch Aufrufen von **CreateReplyAsync** oder **CreateReplyAllAsync**. Dann können Sie [den Entwurf zu aktualisieren](#UpdateMessagesClient) und [Senden](#SendDraftClient).


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage replyDraft = await outlookClient.Me.Messages[messageId].CreateReplyAsync();

// Get the ID of the draft Reply message.
string replyMessageId = replyDraft.Id;
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IMessage replyAllDraft = await outlookClient.Me.Messages[messageId].CreateReplyAllAsync();

// Get the ID of the draft Reply All message.
string replyAllMessageId = replyAllDraft.Id;
```

<!-- ENDSECTION -->

**CreateReplyAsync** und **CreateReplyAllAsync** erstellen den Entwurf einer Nachricht mit der **ToRecipients**, **IsDraft**und anderen geeigneten Eigenschaften vorausgefüllt.


****


<a name="ForwardMessages"> </a>
##<a name="forward-new-or-drafted-messages"></a>Neue oder abgeschrägten Weiterleiten von Nachrichten

**Hinweis** Das Verhalten der Vorgänge in diesem Abschnitt variieren je nach Version. Erfahren Sie mehr durch Auswahl einer Version in der oberen rechten Ecke der Seite.
 
<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Sie können Weiterleiten einer Nachricht, einen Kommentar hinzufügen oder aktualisieren Nachrichteneigenschaften, die alle in einem einzigen Aufruf, oder Sie zuerst einen Entwurf und Update Nachrichteneigenschaften in einem aufrufen, und klicken Sie dann den Entwurf senden erstellen können.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Weiterleiten einer Nachricht können Sie direkt oder den Entwurf Weiterleiten einer Nachricht erstellen, aktualisieren und senden Sie sie.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Weiterleiten einer Nachricht können Sie direkt oder den Entwurf Weiterleiten einer Nachricht erstellen, aktualisieren und senden Sie sie.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



REST-API: [Weiterleiten einer Nachricht direkt (REST)](#ForwardDirectly) | [Erstellen Sie eine Forward-Nachricht (REST)](#CreateForwardDraft)

Client-Bibliotheken: [Weiterleiten einer Nachricht direkt (Client)](#ForwardDirectlyClient) | [Erstellen den Entwurf Weiterleiten einer Nachricht (Client)](#CreateDraftForwardClient)

<a name="ForwardDirectly"></a>
###<a name="forward-a-message-directly-rest"></a>Weiterleiten einer Nachricht direkt (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Weiterleiten einer Nachricht, einen Kommentar hinzufügen oder ändern [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) alle in **Vorwärts** durch Aufrufen. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Alternativ können Sie zunächst [den Entwurf Weiterleiten einer Nachricht erstellen](#CreateForwardDraft) zum Einschließen eines Kommentars oder aktualisieren Sie alle Nachrichteneigenschaften, und [Senden Sie](#SendDraftMessages) den Entwurf einer Nachricht.


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/forward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften in der Antwortnachricht zu aktualisieren. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Geben Sie entweder die `ToRecipients` Parameter oder der **ToRecipients** -Eigenschaft des den `Message` Parameter. Beide angeben oder zum Angeben von weder gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird die **IsDeliveryReceiptRequested** -Eigenschaft auf True festgelegt, wird ein Kommentar hinzugefügt und leitet die Nachricht weiter.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/forward
Content-Type: application/json

{
  "Message":{  
    "IsDeliveryReceiptRequested": true,
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"danas@contoso.onmicrosoft.com",
          "Name":"Dana Swope"
        }
      }
     ]
  },
  "Comment": "Dana, just want to make sure you get this." 
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Weiterleiten einer Nachricht durch Verwendung der **Forward** -Methode und optional einen Kommentar. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Auch wenn Sie ändern [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) in die Nachricht weitergeleitet werden müssen, können Sie zunächst [den Entwurf Weiterleiten einer Nachricht erstellen](#CreateForwardDraft), [Aktualisieren Sie](#UpdateMessages) die Nachricht Eigenschaften, und [Senden](#SendDraftMessages) Sie die Antwort.


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/forward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|

Geben Sie den **Kommentar** und **ToRecipients** -Parameter im Textkörper Anforderung.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/forward
Content-Type: application/json

{
  "Comment": "FYI",
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**Beispielantwort**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Weiterleiten einer Nachricht durch Verwendung der **Forward** -Methode und optional einen Kommentar. Die Nachricht wird im Ordner "Gesendete Elemente" gespeichert.

Auch wenn Sie ändern [aktualisierbare Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) in die Nachricht weitergeleitet werden müssen, können Sie zunächst [den Entwurf Weiterleiten einer Nachricht erstellen](#CreateForwardDraft), [Aktualisieren Sie](#UpdateMessages) die Nachricht Eigenschaften, und [Senden](#SendDraftMessages) Sie die Antwort.


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/forward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|

Geben Sie den **Kommentar** und **ToRecipients** -Parameter im Textkörper Anforderung.

[!code-REST-i[mail_api_send_forward_message_by_id](./_data/mail_api_send_forward_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->





****

<a name="CreateForwardDraft"> </a>
###<a name="create-a-draft-forward-message-rest"></a>Erstellen Sie den Entwurf Weiterleiten einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Erstellen Sie den Entwurf Weiterleiten einer Nachricht enthalten einen Kommentar oder Aktualisieren von [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) alle in einem einzigen Aufruf von **CreateForward** . Anschließend können Sie den Entwurf einer Nachricht [Senden](#SendDraftMessages) .


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createforward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Alle schreibbaren Eigenschaften, die in der Antwortnachricht aktualisiert. |

**Hinweis**

- Sie können einen Kommentar oder die **Body** -Eigenschaft des angeben die `Message` Parameter. Angeben beider gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.
- Geben Sie entweder die `ToRecipients` Parameter oder der **ToRecipients** -Eigenschaft des den `Message` Parameter. Beide angeben oder zum Angeben von weder gibt einen HTTP-400 Ungültige Anforderung Fehler zurück.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/createforward
Content-Type: application/json

{
  "Message":{  
    "IsDeliveryReceiptRequested": true,
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"danas@contoso.onmicrosoft.com",
          "Name":"Dana Swope"
        }
      }
     ]
  },
  "Comment": "Dana, just want to make sure you get this; you'll need this if the project gets approved." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKqAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DQ\"",
  "Id": "AAMkADA1MTAAAH5JKqAAA=",
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DQ",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "HasAttachments": true,
  "InternetMessageId": "<DM2PR00MB0057E0EBC90EF37FC9233941F7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "FW: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>\r\nDana, just want to make sure you get this; you'll need this if the project gets approved.\r\n<b>From:</b> Admin<br>\r\n<b>Sent:</b> Tuesday, March 15, 2016 6:47:54 AM<br>\r\n<b>To:</b> Fanny Downs; Randi Welch<br>\r\n<b>Subject:</b> RE: Let's start a group</body>\r\n</html>\r\n"
  },
  "BodyPreview": "Dana, just want to make sure you get this; you'll need this if the project gets approved.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Dana Swope",
        "Address": "danas@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBGx9qGAAAMtlIAAH+3c",
  "IsDeliveryReceiptRequested": true,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKqAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Erstellen Sie ein Entwurfs oder die Nachricht weiterleiten an einen Kommentar oder Empfänger durch Aufrufen von **CreateForward** hinzufügen. Anschließend können Sie das [Aktualisieren](#UpdateMessages) der [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) und [Senden](#SendDraftMessages) der Entwurf.


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createforward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createforward
Content-Type: application/json

{
  "ToRecipients":[
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
   ],
  "Comment": "Dana, just want to make sure you get this." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k6AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG\"",
  "Id": "AAMkAGE0Mz7k6AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG",
  "Categories": [],
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "Subject": "FW: Let's start a group",
  "BodyPreview": "Dana, just want to make sure you get this.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "'alexd@contoso.onmicrosoft.com'",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [   
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Erstellen Sie einen Entwurf für die Nachricht weiterleiten an einen Kommentar oder Empfänger durch Aufrufen von **CreateForward** hinzufügen. Anschließend können Sie das [Aktualisieren](#UpdateMessages) der [Nachrichteneigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties) und [Senden](#SendDraftMessages) der Entwurf.

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createforward
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zum Weiterleiten.|
|_Textkörper-Parameter_|
|Kommentar|string|Ein Kommentar hinzugefügt. Eine leere Zeichenfolge kann sein.|
|ToRecipients|Auflistung ([Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes))|Die Liste der Empfänger.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createforward
Content-Type: application/json

{
  "ToRecipients":[
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
   ],
  "Comment": "Dana, just want to make sure you get this." 
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k6AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG\"",
  "Id": "AAMkAGE0Mz7k6AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG",
  "Categories": [],
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "Subject": "FW: Let's start a group",
  "BodyPreview": "Dana, just want to make sure you get this.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "'alexd@contoso.onmicrosoft.com'",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [   
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **Antworttyp**

Der Entwurf weiterleiten [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) mit **IsDraft** und die entsprechenden Eigenschaften vorausgefüllt.

****


<a name="ForwardDirectlyClient"></a>
###<a name="forward-a-message-directly-client"></a>Weiterleiten einer Nachricht direkt (Client)

Weiterleiten einer Nachricht direkt durch Aufrufen von **ForwardAsync** und einen Kommentar und die Empfänger übergeben.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
List<Recipient> recipients = new List<Recipient>();
recipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com"
    }
});
await outlookClient.Me.Messages[messageId].ForwardAsync("Interested?", recipients);
```

<!-- ENDSECTION -->

<a name="CreateDraftForwardClient"> </a>
###Erstellen Sie den Entwurf Weiterleiten einer Nachricht (Client)

Erstellen Sie den Entwurf Weiterleiten einer Nachricht, indem Sie **CreateForwardAsync**aufrufen. Dann können Sie [den Entwurf zu aktualisieren](#UpdateMessagesClient) und [Senden](#SendDraftClient).


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage forwardDraft = await outlookClient.Me.Messages[messageId].CreateForwardAsync();

// Get the ID of the draft Forward message.
string forwardMessageId = forwardDraft.Id;
```

<!-- ENDSECTION -->

**CreateForward** erstellt den Entwurf einer Nachricht mit der **IsDraft** und anderen geeigneten Eigenschaften vorausgefüllt.

****

<a name="UpdateMessages"> </a>
##<a name="update-messages"></a>Aktualisieren von Nachrichten

Ändern Sie schreibbare Eigenschaften für eine Nachricht ein, und Speichern der Änderungen.

REST-API: [Aktualisieren einer Nachricht (REST)](#UpdateAMessage)

Client-Bibliotheken: [Aktualisierungsnachricht (Client)](#UpdateAMessageClient)

<a name="UpdateAMessage"></a>
###<a name="update-a-message-rest"></a>Aktualisieren Sie eine Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_


Ändern Sie die schreibbare Eigenschaften für einen Entwurf oder eine vorhandene [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource). Nur die Eigenschaften, die Sie angeben, werden geändert.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu aktualisieren.|

Geben Sie eine oder mehrere schreibbare [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8S-AAA=
Content-Type: application/json

{
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "IsRead": true
}
```

**Beispielantwort**

```
Status code: 200


{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8S-AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP\"",
  "Id": "AAMkAGE0Mz8S-AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "CreatedDateTime": "2014-10-17T17:12:15Z",
  "LastModifiedDateTime": "2014-10-19T03:24:35Z",
  "Subject": "Meeting notes from today",
  "BodyPreview": "See attached",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": true,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mip-qvhs=",
  "ConversationIndex": "AQHRh5tqrkAcds2kw==",
  "ReceivedDateTime": "2014-10-17T17:12:15Z",
  "SentDateTime": "2014-10-17T17:12:12Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu aktualisieren.|

Geben Sie eine oder mehrere schreibbare [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8S-AAA=
Content-Type: application/json

{
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "IsRead": true
}
```

**Beispielantwort**

```
Status code: 200


{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8S-AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP\"",
  "Id": "AAMkAGE0Mz8S-AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP",
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "CreatedDateTime": "2014-10-17T17:12:15Z",
  "LastModifiedDateTime": "2014-10-19T03:24:35Z",
  "Subject": "Meeting notes from today",
  "BodyPreview": "See attached",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": true,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mip-qvhs=",
  "ReceivedDateTime": "2014-10-17T17:12:15Z",
  "SentDateTime": "2014-10-17T17:12:12Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu aktualisieren.|

Geben Sie eine oder mehrere schreibbare [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

[!code-REST-i[mail_api_update_message_by_id](./_data/mail_api_update_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Die aktualisierte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

****

<a name="UpdateAMessageClient"> </a>
###<a name="update-a-message-client"></a>Aktualisieren Sie eine Nachricht (Client)

Ändern Sie der schreibbare Eigenschaften für eine Nachricht ein, und rufen Sie **UpdateAsync** , um die Änderungen zu speichern.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
message.Body = new ItemBody
{
        Content = "I'm coming out a week earlier."
};
message.ToRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com"
    }
});
await message.UpdateAsync();
```

<!-- ENDSECTION -->

Sie können mehrere Updates mithilfe der clientseitigen definieren und senden die Anforderungen alle gleichzeitig (diese batch) mit dem folgenden Muster:
1. Rufen Sie `UpdateAsync(true)` für jede Entität, die Sie aktualisieren möchten. Angeben von `true` registriert die Updates lokal auf dem Client, jedoch nicht auf dem Server bereitstellen.
2. Rufen Sie `outlookClient.Context.SaveChangesAsync()` lokal für die Bereitstellung aller Updates, die registriert sind.



****


<a name="DeleteMessages"> </a>
##<a name="delete-messages"></a>Löschen von Nachrichten

Löschen einer Nachricht.

**Hinweis** Seien Sie vorsichtig, wenn Sie Nachrichten löschen. Gelöschte Inhalt können nicht wiederhergestellt werden.
Weitere Informationen finden Sie unter [Elemente werden](http://msdn.microsoft.com/library/c81e3160-e12b-47e0-b3d6-4be28537f301%28Office.15%29.aspx).

REST API: [Löschen Sie eine Nachricht (REST)](#DeleteAMessage)

Client-Bibliotheken: [Löschen einer Nachricht (Client)](#DeleteMessagesClient)

<a name="DeleteAMessage"></a>
###<a name="delete-a-message-rest"></a>Löschen einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]



```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu löschen.|

**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8TBAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu löschen.|

**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8TBAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]


```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/messages/{message_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu löschen.|

[!code-REST-i[mail_api_delete_message_by_id](./_data/mail_api_delete_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="DeleteMessagesClient"> </a>
###<a name="delete-a-message-client"></a>Löschen einer Nachricht (Client)

Löschen Sie eine Nachricht durch Aufrufen von **"deleteasync"**.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await message.DeleteAsync();
```

<!-- ENDSECTION -->

****


<a name="MoveCopyMessages"> </a>
##<a name="move-or-copy-messages"></a>Verschieben oder Kopieren von Nachrichten

Sie können verschieben oder Kopieren einer Nachricht in einen Ordner.

REST-API: [Verschieben einer Nachricht (REST)](#MoveMessage) | [Kopieren einer Nachricht (REST)](#CopyMessage)

Client-Bibliotheken: [verschieben oder Kopieren einer Nachricht (Client)](#MoveMessagesClient)

<a name="MoveMessage"> </a>
###<a name="move-a-message-rest"></a>Verschieben einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Verschieben von Nachrichten in einen Ordner. Dadurch wird eine neue Kopie der Nachricht im Zielordner erstellt.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu verschieben.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGI2TIy-AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGI2AAEJAAA="
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0MGz_vSAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
  "Id": "AAMkAGI2shBhAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGI2AAEJAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGWgitxag=",
  "ConversationIndex": "AQHRh6etrkAcds2kw==",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu verschieben.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2TIy-AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGI2AAEJAAA="
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0MGz_vSAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
  "Id": "AAMkAGI2shBhAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGI2AAEJAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGWgitxag=",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu verschieben.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|

[!code-REST-i[mail_api_move_message_by_id](./_data/mail_api_move_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Die [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) , die verschoben wurde.

****


<a name="CopyMessage"> </a>
###<a name="copy-a-message-rest"></a>Kopieren einer Nachricht (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Kopieren einer Nachricht in einen Ordner.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu kopieren.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGI2TIy-AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8TDAAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIS\"",
  "Id": "AAMkAGI2T8DtAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQAQAKjRc0YJSUBJpofjWgitxag=",
  "ConversationIndex": "AQHRh6sdrkAcds2kw==",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu kopieren.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2TIy-AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8TDAAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIS\"",
  "Id": "AAMkAGI2T8DtAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQAQAKjRc0YJSUBJpofjWgitxag=",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Nachricht zu kopieren.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


[!code-REST-i[mail_api_copy_message_by_id](./_data/mail_api_copy_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


**Antworttyp**

Die neue Kopie der [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

****

<a name="MoveMessagesClient"> </a>
### <a name="move-or-copy-a-message-client"></a>Verschieben oder Kopieren einer Nachricht (Client)

Verschieben Sie ein oder Kopieren einer Nachricht durch die ID der Zielordner der **MoveAsync** oder **CopyAsync** Methode übergeben.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook-Client hat](..\api\use-outlook-rest-api.md#GetClient), [haben Sie die Nachrichten-ID](#GetMessagesClient)und [haben Sie die ID Desination](#GetFoldersClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage messageToMove = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await messageToMove.MoveAsync("AAMkADE3N...");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IMessage messageToCopy = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await messageToCopy.CopyAsync("Inbox");
```

<!-- ENDSECTION -->

****

<a name="ManageFocusedInbox"></a>
##<a name="manage-focused-inbox"></a>Verwalten von zielgerichteten Posteingang

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Fokussierte Posteingang können Sie wichtige Nachrichten in Anzeigen der `Focused` auf der Registerkarte Posteingang und dem Rest der Posteingangsnachrichten in der `Other` Registerkarte. Das Klassifizierungssystem organisiert anfänglich Nachrichten im Posteingang in einer standardmäßigen Weise. Können Sie beheben und das System über einen Zeitraum über die Benutzeroberfläche oder programmgesteuert Schulen. Je mehr Sie verwenden, das System kann die eingehende Nachricht als wichtig besser ableiten.

Ebene der programmgesteuerten praxisorientierte Posteingang REST-API für den angegebenen Benutzer Nachrichten funktioniert und unterstützt eine **InferenceClassification** -Eigenschaft für jede Nachricht. Die möglichen Werte sind `Focused` und `Other`; die angeben, ob der Benutzer die Nachricht als, jeweils wichtiger und weniger wichtig betrachtet. Um zu beheben und das Klassifizierung Nachrichtensystem Schulen, verwenden Sie die [PATCH-Vorgangs in der **InferenceClassification** -Eigenschaft](#UpdateMessageClassificationBeta) auf Nachrichtenebene. 

Der Schwerpunkt Posteingang REST-API können Sie außerdem Außerkraftsetzungen erstellen. Jede außer Kraft setzen, dargestellt durch eine Instanz des [InferenceClassificationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassificationOverrideResource) ist eine Anweisung für das Klassifizierungssystem Nachrichten von einem bestimmten Absender immer einheitlich (d. h., immer als "Spezifische Darstellung" oder als "Andere" immer), unabhängig davon alle zuvor Gelernte Ansatz festlegt. Können Sie auf [Erstellen](#CreateOverrideBeta), [Abrufen](#GetAllSenderOverridesBeta), [Aktualisieren](#UpdateOverrideBeta) und [Löschen](#DeleteOverrideBeta) für den angegebenen Benutzer außer Kraft gesetzt. Dieses Benutzers Außerkraftsetzungen, werden sofern zutreffend, zugegriffen in einer **InferenceClassification** Navigation-Eigenschaft, die eine Sammlung von **InferenceClassificationOverride** ist. Außerkraftsetzungen können ein Benutzer mehr Kontrolle über die Klassifizierung eingehender Nachrichten und Erstellen von größer Vertrauenswürdigkeit des Systems Klassifikation.

Beachten Sie, dass das Klassifizierungssystem lernen und Klassifizierung nur eingehende Nachrichten im Posteingang betrifft. Nachrichten in anderen Ordnern sind standardmäßig "Spezifische Darstellung". Einrichten einer Überschreibung betrifft zukünftige Nachrichten im Posteingang eingeht. die Überschreibung ändern nicht die **InferenceClassification** -Eigenschaft in vorhandenen Nachrichten in einem Ordner Posteingang einschließlich.


**Das Nachrichtensystem Klassifizierung Schulung**

[Aktualisieren Sie die Nachrichtenklassifikation](#UpdateMessageClassificationBeta)


**Mithilfe von Außerkraftsetzungen ständig pro Absender klassifizieren**

[Erstellen einer Außerkraftsetzung für eine Absender](#CreateOverrideBeta) | [Abrufen aller Benutzer Außerkraftsetzungen](#GetAllSenderOverridesBeta) | [Aktualisieren Sie eine Außerkraftsetzung für einen Absender](#UpdateOverrideBeta) | [eine Absender Überschreibung löschen](#DeleteOverrideBeta) 


<a name="UpdateMessageClassificationBeta"></a>
###<a name="update-message-classification"></a>Aktualisieren Sie die Nachrichtenklassifikation

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Ändern Sie die **InferenceClassification** -Eigenschaft der angegebenen Nachricht. Wenn die Nachricht im Posteingang ist, sieht der Benutzer die Nachricht unter den entsprechenden `Focused` oder `Other` Registerkarte. Diese Art von Korrektur Schulung auch das Klassifizierung Nachrichtensystem zum Anpassen von zukünftigen Klassifikation für den angegebenen Benutzer. 

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages('{message_id}')

PATCH https://outlook.office.com/api/beta/Users('{user_id}')/messages('{message_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der Entwurfsnachricht zu senden.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Die aktualisierte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Beispiel für eine Anforderung**

Dieses Beispiel ändert die **InferenceClassification** -Eigenschaft auf `Other` für die angegebenen Nachricht der des angemeldeten Benutzers.
```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkADA1MTQBAAA=')

{
    "InferenceClassification": "Other"
}
```

**Beispielantwort**

Das hier gezeigte Response-Objekt zeigt die aktualisierte **InferenceClassification** -Eigenschaft und der Kürze halber abgeschnitten. Eine tatsächliche PATCH-Anforderung gibt alle Eigenschaften der Nachricht zurück.
```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTQBAAA=')",
    "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAffAsD\"",
    "Id": "AAMkADA1MTQBAAA=",
    "Importance": "Normal",
    "Sender": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Admin",
                "Address": "admin@adatum.onmicrosoft.com"
            }
        }
    ],
    "InferenceClassification": "Other"
}
```


<a name="CreateOverrideBeta"></a>
###<a name="create-an-override-for-a-sender"></a>Erstellen einer Außerkraftsetzung für eine Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Erstellen einer Außerkraftsetzung für eine SMTP-Adresse identifizierten Absender. Nachrichten von diesem SMTP-Adresse konsistent eingestuft wird wie in die Außerkraftsetzung angegeben.

<a name="CreateOverrideNoteBeta"></a>

**Hinweis**

- Wenn bereits eine Überschreibung mit der gleichen SMTP-Adresse vorhanden ist, werden die **Felder der die Außerkraftsetzung** und **ClassifyAs** mit den angegebenen Werten aktualisiert.
- Die maximale Anzahl von Außerkraftsetzungen unterstützt für ein Postfach ist 1000, basierend auf eindeutige Absenderadressen SMTP.
- POST-Operation unterstützt nur eine Außerkraftsetzung zu einem Zeitpunkt erstellen. Wenn mehrere Außerkraftsetzungen erstellen möchten, können Sie mehrere POST-Anforderungen oder [Batch](..\api\batch-outlook-rest-requests.md) senden sie.


```no-highlight
POST https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

POST https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|USER_ID|string|E-Mail-Adresse des Benutzers. |

**Antworttyp**

Die neu erstellte [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)oder aktualisierte **InferenceClassicationOverride** -Instanz, wenn eine mit dem gleichen bereits SMTP-Adresse vorhanden ist.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

{
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```

**Beispielantwort**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```


<a name="GetAllSenderOverridesBeta"></a>
###<a name="get-all-user-overrides"></a>Abrufen Sie aller Benutzer Außerkraftsetzungen

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie die überschreibt, die ein Benutzer zum Klassifizieren von Nachrichten von bestimmten Absendern immer spezifisch festgelegt hat.

Überschreiben jeweils entspricht einer SMTP-Adresse des Absenders. Ein Benutzer muss zunächst keine Außerkraftsetzungen.

```no-highlight
GET https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

GET https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Eine Auflistung von [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) Instanzen.
Eine leere Auflistung wird zurückgegeben, wenn der Benutzer keine Außerkraftsetzungen einrichten.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/InferenceClassification/Overrides
```

**Beispielantwort**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
            "ClassifyAs": "Focused",
            "SenderEmailAddress": {
                "Name": "Fanny Downs",
                "Address": "fannyd@adatum.onmicrosoft.com"
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
            "ClassifyAs": "Other",
            "SenderEmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@adatum.onmicrosoft.com"
            }
        }
    ]
}
```


<a name="UpdateOverrideBeta"></a>
###<a name="update-an-override-for-a-sender"></a>Aktualisieren Sie eine Außerkraftsetzung für ein Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Ändern einer Außerkraftsetzung gemäß **ClassifyAs** Feld. 

Sie können keine PATCH verwenden, um alle anderen Felder in einer Instanz des [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) ändern. 

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen Anzeigenamen ändert, können Sie die [POST, um eine Aktualisierung in das Feld Name in der vorhandenen Überschreibung erzwingen verwenden](#CreateOverrideNoteBeta).

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen SMTP-Adresse, [Löschen](#DeleteOverrideBeta) der vorhandenen außer Kraft setzen und [Erstellen von ändert](#CreateOverrideBeta) ist eine neue mit der neuen SMTP-Adresse die einzige Möglichkeit, der die Außerkraftsetzung für diesen Absender "Aktualisieren".


```no-highlight
PATCH https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('{override_id}')

PATCH https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|override_id|string|Die ID der die Außerkraftsetzung zu aktualisieren.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Die aktualisierte [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) -Instanz.


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird eine Außerkraftsetzung für die angemeldeten Benutzers. Die Überschreibung mit der SMTP-Adresse des Absenders ist randiw@adatum.onmicrosoft.com, von geändert `Other` auf `Focused`.
```
PATCH https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')

{
    "ClassifyAs": "Focused"
}

```

**Beispielantwort**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@adatum.onmicrosoft.com"
    }
}
```


<a name="DeleteOverrideBeta"></a>
###<a name="delete-a-sender-override"></a>Löschen Sie eine Überschreibung Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Löschen Sie eine durch seine ID angegebene Überschreibung


```no-highlight
DELETE https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('{override_id}')

DELETE https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|override_id|string|Die ID des den Entwurf einer Nachricht zu senden.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')
```

**Beispielantwort**

```
Status code: 204 No Content
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Fokussierte Posteingang können Sie wichtige Nachrichten in Anzeigen der `Focused` auf der Registerkarte Posteingang und dem Rest der Posteingangsnachrichten in der `Other` Registerkarte. Das Klassifizierungssystem organisiert anfänglich Nachrichten im Posteingang in einer standardmäßigen Weise. Können Sie beheben und das System über einen Zeitraum über die Benutzeroberfläche oder programmgesteuert Schulen. Je mehr Sie verwenden, das System kann die eingehende Nachricht als wichtig besser ableiten.

Ebene der programmgesteuerten praxisorientierte Posteingang REST-API für den angegebenen Benutzer Nachrichten funktioniert und unterstützt eine **InferenceClassification** -Eigenschaft für jede Nachricht. Die möglichen Werte sind `Focused` und `Other`; die angeben, ob der Benutzer die Nachricht als, jeweils wichtiger und weniger wichtig betrachtet. Um zu beheben und das Klassifizierung Nachrichtensystem Schulen, verwenden Sie die [PATCH-Vorgangs in der **InferenceClassification** -Eigenschaft](#UpdateMessageClassificationV2) auf Nachrichtenebene. 

Der Schwerpunkt Posteingang REST-API können Sie außerdem Außerkraftsetzungen erstellen. Jede außer Kraft setzen, dargestellt durch eine Instanz des [InferenceClassificationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassificationOverrideResource) ist eine Anweisung für das Klassifizierungssystem Nachrichten von einem bestimmten Absender immer einheitlich (d. h., immer als "Spezifische Darstellung" oder als "Andere" immer), unabhängig davon alle zuvor Gelernte Ansatz festlegt. Können Sie auf [Erstellen](#CreateOverrideV2), [Abrufen](#GetAllSenderOverridesV2), [Aktualisieren](#UpdateOverrideV2) und [Löschen](#DeleteOverrideV2) für den angegebenen Benutzer außer Kraft gesetzt. Außerkraftsetzungen des Benutzers, werden sofern zutreffend, in zugegriffen eine Navigationseigenschaft **InferenceClassification** , eine Sammlung von **InferenceClassificationOverride** Instanzen. Außerkraftsetzungen können ein Benutzer mehr Kontrolle über die Klassifizierung eingehender Nachrichten und Erstellen von größer Vertrauenswürdigkeit des Systems Klassifikation.

Beachten Sie, dass das Klassifizierungssystem lernen und Klassifizierung nur eingehende Nachrichten im Posteingang betrifft. Nachrichten in anderen Ordnern sind standardmäßig "Spezifische Darstellung". Einrichten einer Überschreibung betrifft zukünftige Nachrichten im Posteingang eingeht. die Überschreibung ändern nicht die **InferenceClassification** -Eigenschaft in vorhandenen Nachrichten in einem Ordner Posteingang einschließlich.


**Das Klassifizierung Nachrichtensystem Schulung**

[Aktualisieren Sie die Nachrichtenklassifikation](#UpdateMessageClassificationV2)


**Mithilfe von Außerkraftsetzungen ständig pro Absender klassifizieren**

[Erstellen einer Außerkraftsetzung für eine Absender](#CreateOverrideV2) | [Abrufen aller Benutzer Außerkraftsetzungen](#GetAllSenderOverridesV2) | [Aktualisieren Sie eine Außerkraftsetzung für Absender](#UpdateOverrideV2) | [eine Absender Überschreibung löschen](#DeleteOverrideV2) 


<a name="UpdateMessageClassificationV2"></a>
###<a name="update-message-classification"></a>Aktualisieren Sie die Nachrichtenklassifikation

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Ändern Sie die **InferenceClassification** -Eigenschaft der angegebenen Nachricht. Wenn die Nachricht im Posteingang ist, sieht der Benutzer die Nachricht unter den entsprechenden `Focused` oder `Other` Registerkarte. Diese Art von Korrektur Schulung auch das Klassifizierung Nachrichtensystem zum Anpassen von zukünftigen Klassifikation für den angegebenen Benutzer. 

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages('{message_id}')

PATCH https://outlook.office.com/api/v2.0/Users('{user_id}')/messages('{message_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID des den Entwurf einer Nachricht zu senden.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Die aktualisierte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Beispiel für eine Anforderung**

Dieses Beispiel ändert die **InferenceClassification** -Eigenschaft auf `Other` für die angegebenen Nachricht der des angemeldeten Benutzers.
```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkADA1MTQBAAA=')

{
    "InferenceClassification": "Other"
}
```

**Beispielantwort**

Das hier gezeigte Response-Objekt zeigt die aktualisierte **InferenceClassification** -Eigenschaft und der Kürze halber abgeschnitten. Eine tatsächliche PATCH-Anforderung gibt alle Eigenschaften der Nachricht.
```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTQBAAA=')",
    "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAffAsD\"",
    "Id": "AAMkADA1MTQBAAA=",
    "Importance": "Normal",
    "Sender": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Admin",
                "Address": "admin@adatum.onmicrosoft.com"
            }
        }
    ],
    "InferenceClassification": "Other"
}
```


<a name="CreateOverrideV2"></a>
###<a name="create-an-override-for-a-sender"></a>Erstellen einer Außerkraftsetzung für eine Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Erstellen einer Außerkraftsetzung für eine SMTP-Adresse identifizierten Absender. Nachrichten von diesem SMTP-Adresse konsistent eingestuft wird wie in die Außerkraftsetzung angegeben.

<a name="CreateOverrideNoteV2"></a>

**Hinweis**

- Wenn bereits eine Überschreibung mit der gleichen SMTP-Adresse vorhanden ist, werden die **Felder der die Außerkraftsetzung** und **ClassifyAs** mit den angegebenen Werten aktualisiert.
- Die maximale Anzahl von Außerkraftsetzungen unterstützt für ein Postfach ist 1000, basierend auf eindeutige Absenderadressen SMTP.
- POST-Operation unterstützt nur eine Außerkraftsetzung zu einem Zeitpunkt erstellen. Wenn mehrere Außerkraftsetzungen erstellen möchten, können Sie mehrere POST-Anforderungen oder [Batch](..\api\batch-outlook-rest-requests.md) senden sie.


```no-highlight
POST https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

POST https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Die neu erstellte [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)oder aktualisierte **InferenceClassicationOverride** -Instanz, wenn eine mit dem gleichen bereits SMTP-Adresse vorhanden ist.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

{
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```

**Beispielantwort**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```


<a name="GetAllSenderOverridesV2"></a>
###<a name="get-all-user-overrides"></a>Abrufen Sie aller Benutzer Außerkraftsetzungen

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie die überschreibt, die ein Benutzer zum Klassifizieren von Nachrichten von bestimmten Absendern immer spezifisch festgelegt hat.

Überschreiben jeweils entspricht einer SMTP-Adresse des Absenders. Ein Benutzer muss zunächst keine Außerkraftsetzungen.

```no-highlight
GET https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

GET https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Eine Auflistung von [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) Instanzen.
Eine leere Auflistung wird zurückgegeben, wenn der Benutzer keine Außerkraftsetzungen einrichten.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides
```

**Beispielantwort**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
            "ClassifyAs": "Focused",
            "SenderEmailAddress": {
                "Name": "Fanny Downs",
                "Address": "fannyd@adatum.onmicrosoft.com"
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
            "ClassifyAs": "Other",
            "SenderEmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@adatum.onmicrosoft.com"
            }
        }
    ]
}
```


<a name="UpdateOverrideV2"></a>
###<a name="update-an-override-for-a-sender"></a>Aktualisieren Sie eine Außerkraftsetzung für eine Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Ändern einer Außerkraftsetzung gemäß **ClassifyAs** Feld. 

Sie können keine PATCH verwenden, um alle anderen Felder in einer Instanz des [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) ändern. 

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen Anzeigenamen ändert, können Sie die [POST, um eine Aktualisierung in das Feld Name in der vorhandenen Überschreibung erzwingen verwenden](#CreateOverrideNoteV2).

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen SMTP-Adresse, [Löschen](#DeleteOverrideV2) der vorhandenen außer Kraft setzen und [Erstellen von ändert](#CreateOverrideV2) ist eine neue mit der neuen SMTP-Adresse die einzige Möglichkeit, der die Außerkraftsetzung für diesen Absender "Aktualisieren".


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('{override_id}')

PATCH https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|override_id|string|Die ID der die Außerkraftsetzung zu aktualisieren.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Antworttyp**

Die aktualisierte [InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource) -Instanz.


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird eine Außerkraftsetzung für die angemeldeten Benutzers. Die Überschreibung mit der SMTP-Adresse des Absenders ist randiw@adatum.onmicrosoft.com aus `Other` auf `Focused`.
```
PATCH https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')

{
    "ClassifyAs": "Focused"
}

```

**Beispielantwort**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@adatum.onmicrosoft.com"
    }
}
```


<a name="DeleteOverrideV2"></a>
###<a name="delete-a-sender-override"></a>Löschen Sie eine Überschreibung Absender

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Löschen Sie eine durch seine ID angegebene Überschreibung


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('{override_id}')

DELETE https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|override_id|string|Die ID des den Entwurf einer Nachricht zu senden.|
|USER_ID|string|E-Mail-Adresse des Benutzers. |


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')
```

**Beispielantwort**

```
Status code: 204 No Content
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in V2. 0 und Beta. Um mehr zu erfahren, verwenden Sie das Steuerelement in der oberen rechten Ecke des Artikels, und wählen Sie eine der folgenden Versionen.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="ManageMentions"></a>
##<a name="manage--mentions-preview"></a>Verwalten von @-Mentions (Preview)

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Aufrufen von einem Empfänger zum Abrufen des Empfängers Aufmerksamkeit in einer Nachricht ist eine allgemeine soziale Bewegung.
Die [erwähnen](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource) Ressource enthält einen Mechanismus leicht informieren einer anderen Empfänger oder von einem Absender in einer Nachricht eine Benachrichtigung erhalten möchten. 

<!-- Comment out for Mentions API
Add this sentence when support for events is back in

**Mention** is also supported by 
[Event](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

-->

Über die Benutzeroberfläche eine app kann Benutzer Vermerk in eine Nachricht einzufügen, indem Sie vor der Erwähnung mit lassen `@` (häufig verwendet, um ähnliche Szenarien in anderen apps, daher der Begriff @-mention). programmgesteuert die app können [Erstellen](#CreateMentionInNewMessage) die Erwähnung, indem Sie die Eigenschaft **erwähnt** , in der gleichen hinzugefügt `POST` Anruf an die Nachricht zu erstellen. 

Die app können Benutzer [Nachschlagen](#GetAllMessagesMentionUser) , ob sie alle Nachrichten in ihren Posteingang benachrichtigt wurden. Benutzer können [Hier finden Sie Details](#GetDetailsEachMentionInMessage) der einzelnen Erwähnung in einer Nachricht. Sie können außerdem einen Vermerk in einer Nachricht [Löschen](#DeleteMention) .



<a name="CreateMentionInNewMessage"></a>
**Erstellen von erwähnungen in einer neuen Nachricht**

[Erstellen und Senden von erwähnungen im Rahmen einer neuen Nachricht](#CreateSendMention) | [Erstellen erwähnt wird als Teil eines e-Mail-Entwurfs](#CreateMentionInDraft)


**Abrufen von Informationen über erwähnungen in einer Nachricht**

[Möchten Sie alle Nachrichten, in denen die angemeldeten Benutzers erwähnt](#GetAllMessagesMentionUser) | [Details der einzelnen Erwähnung in einer Nachricht erhalten möchten](#GetDetailsEachMentionInMessage)


**Löschen der Vermerk in einer Nachricht**

[Löschen der Vermerk](#DeleteMention)


<a name="CreateSendMention"></a>
###<a name="create-and-send-mentions-as-part-of-a-new-message"></a>Erstellen und Senden von erwähnungen im Rahmen einer neuen Nachricht

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

Erstellen Sie und senden Sie eine Nachricht im Textkörper Anforderung die enthält eine Auflistung von einer oder mehreren [erwähnen](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource) Instanzen angegeben.

Dies verwendet die gleiche [SendMail](#SendMessageOnTheFly) -Aktion auf die [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Ressource. Darüber hinaus können Sie die Eigenschaft **Erwähnungen** im Rahmen des Parameters Body **Nachricht** .


```no-highlight
POST https://outlook.office.com/api/beta/me/sendmail
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Textkörper-Parameter_|
|Message|[Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|Die zu sendende Nachricht.|
|SavetoSentItems|boolean|Gibt an, ob die Nachricht in gesendete Objekte gespeichert. Der Standardwert ist **true**. Nur erforderlich, wenn **false**.|

Geben Sie den Parameter **Nachricht** mit required **ToRecipients** -Eigenschaft der **Erwähnungen** -Eigenschaft und alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

Und für jede erwähnt werden in der Eigenschaft **erwähnt** , müssen Sie die Eigenschaften **Mentioned** und **CreatedBy** angeben.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/sendmail
Content-Type: application/json

{
  "Message": {
    "Subject": "Project kickoff",
    "ToRecipients":[
      {
          "EmailAddress":{
          "Name":"Fanny Downs",
          "Address":"fannyd@contoso.onmicrosoft.com"
          }
      }
    ],
    "Mentions":[
      {
        "Mentioned":{
          "Name":"Dana Swope",
          "Address":"danas@contoso.onmicrosoft.com"
         },
        "CreatedBy": {
            "Name":"Randi Welch",
            "Address":"randiw@contoso.onmicrosoft.com"
        }
      }
    ]
  }
}
```

**Beispielantwort**

```
Status code: 202 Accepted
```


<a name="CreateMentionInDraft"></a>
###<a name="create-mentions-as-part-of-a-message-draft"></a>Erstellen von erwähnungen als Teil eines e-Mail-Entwurfs

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Erstellen Sie einen Entwurf einer neuen Nachricht enthält eine Auflistung von mindestens [erwähnen](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource) Instanzen. Sie können den Entwurf in alle Ordner und optional [Aktualisieren](#UpdateMessages) erstellen sie vor dem [Senden](#SendDraftMessages). 

Die gleiche [POST](#CreateNewDraft) -Methode verwendet auf die [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Ressource; Darüber hinaus können Sie dessen **erwähnt** -Eigenschaft im Textkörper Anforderung enthalten.

```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die Ziel-Ordner-ID oder die `Inbox` oder `Drafts` bekannte Ordnername.|

Angeben der Eigenschaft **erwähnt wird** und alle schreibbaren [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Eigenschaften im Textkörper Anforderung.

Und für jede erwähnt werden in der Eigenschaft **erwähnt** , müssen Sie die **Mentioned** und **CreatedBy** -Eigenschaften angeben.

**Antworttyp**

Der Entwurf einer [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages
Content-Type: application/json

{
    "Subject": "Party planning",
    "ToRecipients":[
      {
          "EmailAddress":{
          "Name":"Fanny Downs",
          "Address":"fannyd@contoso.onmicrosoft.com"
          }
      }
    ],
    "Mentions":[
      {    
        "Mentioned":{
          "Name":"Dana Swope",
          "Address":"danas@contoso.onmicrosoft.com"
         },
        "CreatedBy": {
            "Name":"Randi Welch",
            "Address":"randiw@contoso.onmicrosoft.com"
        }
      }
    ]
}
```

**Beispielantwort**

Die folgende Abbildung zeigt die erstellten Entwurf einer Nachricht. Hinweis: Das hier gezeigte Response-Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.

```
Status code: 201 Created

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAW1fsAAAAA==')",
  "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAbYj7\"",
  "Id":"AQMkADJmMTUAAAW1fsAAAAA==",
  "Body":{
    "ContentType":"Text",
    "Content":""
  },
  "BodyPreview":"",
  "Sender":null,
  "From":null,
  "ToRecipients":[
    {
      "EmailAddress":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com"
      }
    }
  ],
  "MentionsPreview":{
    "IsMentioned":false
  },
  "Mentions@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages('AQMkADJmMTUAAAW1fsAAAAA%3D%3D')/Mentions",
  "Mentions":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAW1fsAAAAA==')/Mentions('4577bba4-b063-4cea-9073-6f7ca815fcec')",
      "Id":"4577bba4-b063-4cea-9073-6f7ca815fcec",
      "Mentioned":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com",
        "ExternalId":"72137a84-1a8b-4b92-aa06-cca538e8616b"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-22T02:22:44Z",
      "ServerCreatedDateTime":"2016-07-22T02:22:44.201Z",
      "DeepLink":null,
      "Application":null
    }
  ]
}
```


<a name="GetAllMessagesMentionUser"></a>
###<a name="get-all-messages-that-mention-the-signed-in-user"></a>Abrufen Sie alle Nachrichten, in denen die angemeldeten Benutzers erwähnt

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie alle Nachrichten im Postfach des angemeldeten Benutzers oder im angegebenen Ordner, die eine [erwähnen](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource) dieses Benutzers enthalten.

Dies verwendet die gleiche Methode [GET verfügbar für die [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Ressource;](#GetMessageCollection) Darüber hinaus enthalten Sie eine `$filter` Parameter für die Eigenschaft **MentionsPreview** Abfragen. 

In der Standardeinstellung eine `GET /me/messages` Anruf gibt keine **erwähnt** -Eigenschaft zurück. Verwendung der `$expand` Abfragen Parameter [Hier finden Sie Details](#GetDetailsEachMentionInMessage) der einzelnen Erwähnung in einer Nachricht.

Hinweis: Stellen Sie sicher, dass der aktuelle Anruf entsprechend die Leerzeichen in der Abfragezeichenfolge Parameter codiert.

```no-highlight
GET https://outlook.office.com/api/beta/me/messages?$filter=MentionsPreview/IsMentioned eq true

GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages?$filter=MentionsPreview/IsMentioned eq true
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die Ziel-Ordner-ID oder die `Inbox` oder `Drafts` bekannte Ordnername.|


**Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) -Auflistung.


**Beispiel für eine Anforderung**

Im folgenden Beispiel werden alle Nachrichten im Postfach des angemeldeten Benutzers für Benutzer, in denen den Benutzer erwähnt Filter. Es verwendet `$select` um eine Teilmenge der Eigenschaften der einzelnen Nachrichten in der Antwort zurückzugeben. Sie umfasst auch die URL-Codierung für die Leerzeichen in der Abfragezeichenfolge-Parameter.

```
GET https://outlook.office.com/api/beta/me/messages?$filter=MentionsPreview/IsMentioned%20eq%20true&$select=Subject,Sender,ReceivedDateTime,MentionsPreview
```

**Beispielantwort**

Die Antwort enthält 2 Nachrichten, in denen die angemeldeten Benutzers erwähnt an.

```
Status code: 200 OK

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages(Subject,Sender,ReceivedDateTime,MentionsPreview)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')",
      "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAATI\"",
      "Id":"AQMkADJmMTUAAAgVZAAAA",
      "ReceivedDateTime":"2016-07-21T07:40:21Z",
      "Subject":"Re: Start planning soon",
      "Sender":{
        "EmailAddress":{
          "Name":"Randi Welch",
          "Address":"randiw@contoso.onmicrosoft.com"
        }
      },
      "MentionsPreview":{
        "IsMentioned":true
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAjwVAAAA')",
      "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAEGj\"",
      "Id":"AQMkADJmMTUAAAjwVAAAA",
      "ReceivedDateTime":"2016-07-21T07:40:20Z",
      "Subject":"Re: Start planning soon",
      "Sender":{
        "EmailAddress":{
          "Name":"Randi Welch",
          "Address":"randiw@contoso.onmicrosoft.com"
        }
      },
      "MentionsPreview":{
        "IsMentioned":true
      }
    }
  ]
}
```


<a name="GetDetailsEachMentionInMessage"></a>
###<a name="get-details-of-each-mention-in-a-message"></a>Details der einzelnen Erwähnung in einer Nachricht erhalten möchten

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie eine Meldung mit den Details jeder [erwähnen](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource) , in der Nachricht erweitert.

Dies verwendet die gleiche Methode [GET verfügbar für die [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) Ressource;](#GetMessage) Darüber hinaus enthalten Sie eine `$expand` Parameter Navigationseigenschaft **erwähnt** Abfragen.

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')?$expand=Mentions
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID der angeforderten Nachricht.|


**Antworttyp**

Die angeforderte [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource).


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird die angemeldeten Benutzers Dana Swope. Das Beispiel zeigt die Details der alle Vorkommnisse in der angegebenen Nachricht im Postfach des Dana abrufen.

```
GET https://outlook.office.com/api/beta/me/messages('AQMkADJmMTUAAAgVZAAAA')?$expand=Mentions 
```

**Beispielantwort**

Die folgende Abbildung zeigt die angeforderte Nachricht, einschließlich Details zu einzelnen Erwähnung in der Eigenschaft **erwähnt** . Diese Nachricht enthält 2 erwähnt, eine für die angemeldeten Benutzers Dana und das andere für Randi Welch.

Hinweis: Das hier gezeigte Response-Objekt wird der Kürze halber auf die Eigenschaften im Zusammenhang mit der Unterstützung **erwähnen**konzentrieren Zahl gekürzt.

```
Status code: 200 OK

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')",
  "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAATI\"",
  "Id":"AQMkADJmMTUAAAgVZAAAA",
  "Subject":"Start planning soon",
  "Body":{
    "ContentType":"HTML",
    "Content":"<html><head></head><body"><p><a href=\"mailto:danas@contoso.onmicrosoft.com\">@Dana Swope</a>,<a href=\"mailto:randiw@contoso.onmicrosoft.com\">@Randi Welch</a>, forgot to mention, I will be away&nbsp;this weekend. I can start on Monday though.</p></body></html>"
  },
  "BodyPreview":"@Dana Swope<mailto:danas@contoso.onmicrosoft.com>, @Randi Welch, forgot to mention, I will be away this weekend. I can start on Monday though.",
  "Sender":{
    "EmailAddress":{
      "Name":"Fanny Downs",
      "Address":"fannyd@contoso.onmicrosoft.com"
    }
  },
  "From":{
    "EmailAddress":{
      "Name":"Fanny Downs",
      "Address":"fannyd@contoso.onmicrosoft.com"
    }
  },
  "ToRecipients":[
    {
      "EmailAddress":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients":[
  ],
  "BccRecipients":[
  ],
  "MentionsPreview":{
    "IsMentioned":true
  },
  "Mentions@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions",
  "Mentions":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions('138f4c0a-1130-4776-b780-bf79d73abb3f')",
      "Id":"138f4c0a-1130-4776-b780-bf79d73abb3f",
      "Mentioned":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com",
        "ExternalId":"72137a84-1a8b-4b92-aa06-cca538e8616b"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-21T07:40:20.152Z",
      "ServerCreatedDateTime":"2016-07-21T07:40:20.152Z",
      "DeepLink":null,
      "Application":null
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions('7b94df1a-0086-482a-b0da-e62fae12f983')",
      "Id":"7b94df1a-0086-482a-b0da-e62fae12f983",
      "Mentioned":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-21T07:40:20.158Z",
      "ServerCreatedDateTime":"2016-07-21T07:40:20.158Z",
      "DeepLink":null,
      "Application":null
    }
  ]
}

```


<a name="DeleteMention"></a>
###<a name="delete-a-mention"></a>Löschen der Vermerk

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Löscht das angegebene Erwähnung in der angegebenen Nachricht im Postfach des angemeldeten Benutzers. 

```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages('{message_id}')/mentions('{mention_id}')
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|mention_id|string|Die ID des die Erwähnung zu löschen.|
|message_id|string|Die ID der Nachricht, die die Erwähnung enthält.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/messages('AAMkADA1MTk1ZAAAKXBQCAAA=')/mentions('7b94df1a-0086-482a-b0da-e62fae12f983')
```

**Beispielantwort**

```
Status code: 204 No Content
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="Unsubscribe"></a>
##<a name="unsubscribe-preview"></a>Melden Sie sich ab (Preview)

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Send_
- _WL.IMAP_

Fordert die e-Mail im Namen des angemeldeten Benutzers an eine e-Mail-Verteilerliste kündigen. Verwendet die Informationen in der `List-Unsubscribe` Kopfzeile.

```no-highlight
POST https://outlook.office.com/api/beta/me/messages('{message_id}')/unsubscribe
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die ID des den Entwurf einer Nachricht zu senden.|


Absender einer Nachricht können Adressenlisten benutzerfreundliche durch die Option für Empfänger einschließen zum Aufheben der Bestätigung. Hierzu können sie angeben den `List-Unsubscribe` Kopfzeile in jede Nachricht [RFC 2369](http://www.faqs.org/rfcs/rfc2369.html)befolgen.

**Hinweis** Insbesondere für die Aktion **zum Abmelden** funktioniert, der Absender muss angeben, `mailto:` und nicht URL-basierte melden Sie sich Informationen ab.

Durch Festlegen dieser Kopfzeile würden **UnsubscribeEnabled** Eigenschaft der Instanz [Nachricht](../api/complex-types-for-mail-contacts-calendar.md#MessageResource) mit auch festlegen `true`, und der **UnsubscribeData** -Eigenschaft mit den Kopfzeilendaten.

Wenn die **UnsubscribeEnabled** -Eigenschaft einer Nachricht `true`, können Sie die Aktion **zum Abmelden** , um die Benutzer ähnliche zukünftige Nachrichten zu kündigen, wie durch den Absender der Nachricht verwaltet. 

Eine erfolgreiche **kündigen** -Aktion wird die Nachricht in den Ordner Gelöschte Elemente verschoben. Der tatsächliche Ausschluss des Benutzers aus der zukünftigen Mail Verteilung wird vom Absender verwaltet.



**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/messages('AAMkADA1MTk1ZAAAKXBQCAAA=')/unsubscribe
```

**Beispielantwort**

```
Status code: 202 Accepted
```
 


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="GetAutoReplySettings"></a>
##<a name="get-auto-reply-settings"></a>Abrufen von Einstellungen für automatische Antworten

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Automatische Antworten können Sie Personen mit einer Nachricht automatisch zu benachrichtigen, wenn sie, dass Sie per e-Mail senden. Sie können beispielsweise benachrichtigt, wenn Sie nicht verfügbar sind und können nicht auf diese reagieren.

Da automatische Antworten zu den Einstellungen des Benutzers Postfach (dargestellt durch [MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)) gehören, können Sie durch Abrufen aller postfacheinstellungen, die Einstellungen für automatische Antworten umfassen, oder durch speziell der Einstellungen für automatische Antworten empfangen Einstellungen für automatische Antworten anzeigen.

Sie können die `Prefer: outlook.timezone` -HTTP-Header an die bevorzugte Zeitzone, um die Werte **ScheduledStartDateTime** und **ScheduledEndDateTime** anzuzeigen.

REST-API: [Abrufen aller postfacheinstellungen](#GetAllMailboxSettingsBeta) | [speziell Einstellungen für automatische Antwort erhalten](#GetOnlyAutoReplySettingsBeta)


<a name="GetAllMailboxSettingsBeta"></a>
###<a name="get-all-mailbox-settings"></a>Abrufen Sie aller postfacheinstellungen

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_

Rufen Sie die Einstellungen für das primäre Postfach des angemeldeten Benutzers.


```no-highlight
GET https://outlook.office.com/api/beta/me/MailboxSettings
```

 **Antworttyp**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta).


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/MailboxSettings
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "All",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-14T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
        "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}
```


<a name="GetOnlyAutoReplySettingsBeta"></a>
###<a name="get-automatic-reply-settings"></a>Abrufen von Einstellungen für automatische Antworten

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_

Rufen Sie die Einstellungen für automatische Antworten Postfach des angemeldeten Benutzers.


```no-highlight
GET https://outlook.office.com/api/beta/me/MailboxSettings/AutomaticRepliesSetting
```

 **Antworttyp**

[AutomaticRepliesSetting](../api/complex-types-for-mail-contacts-calendar.md#AutomaticRepliesSettingBeta).


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/MailboxSettings/AutomaticRepliesSetting
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings/AutomaticRepliesSetting",
    "Status": "AlwaysEnabled",
    "ExternalAudience": "None",
    "ScheduledStartDateTime": {
        "DateTime": "2016-03-19T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "ScheduledEndDateTime": {
        "DateTime": "2016-03-20T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Automatische Antworten können Sie Personen mit einer Nachricht automatisch zu benachrichtigen, wenn sie, dass Sie per e-Mail senden. Sie können beispielsweise benachrichtigt, wenn Sie nicht verfügbar sind und können nicht auf diese reagieren.

Da automatische Antworten zu den Einstellungen des Benutzers Postfach (dargestellt durch [MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)) gehören, können Sie durch Abrufen aller postfacheinstellungen, die Einstellungen für automatische Antworten umfassen, oder durch speziell der Einstellungen für automatische Antworten empfangen Einstellungen für automatische Antworten anzeigen.

Sie können die `Prefer: outlook.timezone` -HTTP-Header an die bevorzugte Zeitzone, um die Werte **ScheduledStartDateTime** und **ScheduledEndDateTime** anzuzeigen.

REST-API: [Abrufen aller postfacheinstellungen](#GetAllMailboxSettingsV2) | [speziell Einstellungen für automatische Antwort erhalten](#GetOnlyAutoReplySettingsV2)


<a name="GetAllMailboxSettingsV2"></a>
###<a name="get-all-mailbox-settings"></a>Abrufen Sie aller postfacheinstellungen

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_

Rufen Sie die Einstellungen für das primäre Postfach des angemeldeten Benutzers.


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailboxSettings
```

 **Antworttyp**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2).


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/MailboxSettings
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "All",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-14T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
        "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}
```


<a name="GetOnlyAutoReplySettingsV2"></a>
###<a name="get-automatic-reply-settings"></a>Abrufen von Einstellungen für automatische Antworten

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_

Rufen Sie die Einstellungen für automatische Antworten Postfach des angemeldeten Benutzers.


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailboxSettings/AutomaticRepliesSetting
```

 **Antworttyp**

[AutomaticRepliesSetting](../api/complex-types-for-mail-contacts-calendar.md#AutomaticRepliesSettingV2).


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/MailboxSettings/AutomaticRepliesSetting
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings/AutomaticRepliesSetting",
    "Status": "AlwaysEnabled",
    "ExternalAudience": "None",
    "ScheduledStartDateTime": {
        "DateTime": "2016-03-19T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "ScheduledEndDateTime": {
        "DateTime": "2016-03-20T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in V2. 0 und Beta. Um mehr zu erfahren, verwenden Sie das Steuerelement in der oberen rechten Ecke des Artikels, und wählen Sie eine der folgenden Versionen.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****



<a name = "UpdateAutoReplySettings"></a>
##<a name="update-auto-reply-settings"></a>Aktualisieren der Einstellungen für automatische Antworten

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_


Automatische Antworten sind Teil der Postfach-Einstellungen des Benutzers (dargestellt durch [MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)). Sie können aktivieren, konfigurieren oder deaktivieren automatische Antworten durch die entsprechenden postfacheinstellungen zu aktualisieren. 

**Hinweis** Erstellen oder löschen eine beliebige Einstellung Postfach.

```no-highlight
PATCH https://outlook.office.com/api/beta/me/MailboxSettings
```

**Antworttyp**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta).


**Beispiel für eine Anforderung**

Nach dem [vorherigen Beispiel](#GetOnlyAutoReplySettingsBeta) Abrufen von Einstellungen für automatische Antworten, das nächste Beispiel ändert den **Status** von `AlwaysEnabled` , `Scheduled`, und die Anfangs- und Enddatum an einen anderen Datumsbereich.



```
PATCH https://outlook.office.com/api/beta/me/MailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ScheduledStartDateTime": {
          "DateTime": "2016-03-20T18:00:00.0000000",
          "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
          "DateTime": "2016-03-28T18:00:00.0000000",
          "TimeZone": "UTC"
        }
    }
}
```



**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "None",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-20T02:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T02:00:00.0000000",
            "TimeZone": "UTC"
        },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}


```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**Mindestens erforderliche Bereich**: https://outlook.office.com/mailboxsettings.readwrite_


Automatische Antworten sind Teil der Postfach-Einstellungen des Benutzers (dargestellt durch [MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)). Sie können aktivieren, konfigurieren oder deaktivieren automatische Antworten durch die entsprechenden postfacheinstellungen zu aktualisieren. 

**Hinweis** Erstellen oder löschen eine beliebige Einstellung Postfach.

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/MailboxSettings
```

**Antworttyp**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2).


**Beispiel für eine Anforderung**

Nach dem [vorherigen Beispiel](#GetOnlyAutoReplySettingsV2) Abrufen von Einstellungen für automatische Antworten, das nächste Beispiel ändert den **Status** von `AlwaysEnabled` , `Scheduled`, und die Anfangs- und Enddatum an einen anderen Datumsbereich.



```
PATCH https://outlook.office.com/api/v2.0/me/MailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ScheduledStartDateTime": {
          "DateTime": "2016-03-20T18:00:00.0000000",
          "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
          "DateTime": "2016-03-28T18:00:00.0000000",
          "TimeZone": "UTC"
        }
    }
}
```



**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "None",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-20T02:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T02:00:00.0000000",
            "TimeZone": "UTC"
        },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}


```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in Beta und v2. 0. Um mehr zu erfahren, verwenden Sie das Steuerelement in der oberen rechten Ecke des Artikels, und wählen Sie eine der folgenden Versionen.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetMailTips"></a>
##<a name="get-mailtips-preview"></a>Abrufen von e-Mail-Infos (Preview)

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**Mindestens erforderliche Bereich**_: einer der folgenden:

- _https://Outlook.Office.com/Mail.Read.My_
- _https://Outlook.Office.com/Mail.Read.Shared_

Rufen Sie die e-Mail-Infos für einen oder mehrere Empfänger als verfügbar für dem angemeldeten Benutzer. Beachten Sie, dass dies als einen POST-Vorgang für die Aktion **GetMailTips** durchgeführt wird.


```no-highlight
POST https://outlook.office.com/api/beta/me/GetMailTips
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Textkörper-Parameter_|
|EmailAddresses|Collection(String)|Eine Auflistung von SMTP-Adressen der Empfänger für e-Mail-Infos zu erhalten.|
|MailTipsOptions|[MailTipsType](../api/complex-types-for-mail-contacts-calendar.md#MailTipsType)|Die Arten von e-Mail-Infos für die angegebenen Empfänger zu erhalten.|


**Antworttyp**

Auflistung von [e-Mail-Infos](../api/complex-types-for-mail-contacts-calendar.md#MailTips).


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird die e-Mail-Infos für die angegebenen Empfänger, für alle Einstellungen für automatische Antworten und Postfach voll Status.


```
POST https://outlook.office.com/api/beta/me/GetMailTips
Content-Type: application/json

{
    "EmailAddresses": [
        "danas@contoso.onmicrosoft.com", 
        "fannyd@contoso.onmicrosoft.com"
    ],
    "MailTipsOptions": "AutomaticReplies, MailboxFullStatus"
}
```



**Beispielantwort**

```
Status code: 200 OK

{
    "@odata.context":"https://outlook.office.com/api/beta/$metadata#Collection(Microsoft.OutlookServices.MailTips)",
    "value":[
        {
            "EmailAddress":{
                "Name":"",
                "Address":"danas@contoso.onmicrosoft.com"
            },
            "AutomaticReplies":{
                "Message":"<style type=\"text/css\" style=\"\">\r\n<!--\r\np\r\n\t{margin-top:0;\r\n\tmargin-bottom:0}\r\n-->\r\n</style>\r\n<div dir=\"ltr\">\r\n<div id=\"x_divtagdefaultwrapper\" style=\"font-size:12pt; color:#000000; background-color:#FFFFFF; font-family:Calibri,Arial,Helvetica,sans-serif\">\r\n<p>Hi, I am on vacation right now. I'll get back to you after I return.<br>\r\n</p>\r\n</div>\r\n</div>",
                "MessageLanguage":{
                    "Locale":"en-US",
                    "DisplayName":"English (United States)"
                }
            },
            "MailboxFull":false
        },
        {
            "EmailAddress":{
                "Name":"",
                "Address":"fannyd@contoso.onmicrosoft.com"
            },
            "AutomaticReplies":{
                "Message":""
            },
            "MailboxFull":false
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in der Betaversion verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="GetAttachments"> </a>
##<a name="get-attachments"></a>Abrufen von Anlagen

Sie können eine Anlage-Auflistung abzurufen oder Anlage erhalten möchten. Anlagen können Dateien (beispielsweise werden. 

REST-API: [Abrufen eine Anlage-Auflistung (REST)](#GetAttachmentCollection) | [Abrufen eine Anlage (REST)](#GetAttachment)

Client-Bibliotheken: [erhalten Sie eine oder mehrere Nachrichtenanlagen (Client)](#GetAttachmentsClient)


<a name="GetAttachmentCollection"> </a>
###<a name="get-an-attachment-collection-rest"></a>Rufen Sie eine Anlage-Auflistung (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie die Anlagen aus einer bestimmten Nachricht.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|

**Hinweis** Jede Anlage in der Antwort enthält standardmäßig alle Eigenschaften entsprechend der Anlage Typs. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [ReferenceAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)sein kann.


**Beispiel-Anforderungen und-Antworten**

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** soll nur die **Name** -Eigenschaft der einzelnen Dateianlage in der Antwort zurückgeben. Finden Sie unter Beispielantwort im [Abrufen einer Anlage (REST)](#GetAttachment) für eine vollständige Liste der Eigenschaften an, die für eine Anlage zurückgegeben wird, wenn Sie **$select**nicht verwenden.

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=/attachments?$select=Name
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments(Name)",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
            "Id": "AAMkAGI2j4kShdM=",
            "Name": "minutes.docx"
        }
    ]
}
```

Das folgende Beispiel zeigt das Abrufen der einzigen Anlage ist ein Outlook-Mail-Element. Die Antwort enthält eine Anlage-ID die ID der Nachricht angefügte auch handelt es sich.

```
GET https://outlook.office.com/api/beta/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "LastModifiedDateTime": "2015-09-24T05:57:59Z",
    }
  ]
}
```




[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|

**Hinweis** Jede Anlage in der Antwort enthält standardmäßig alle Eigenschaften entsprechend der Anlage Typs. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)sein kann.


**Beispiel-Anforderungen und-Antworten**

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** soll nur die **Name** -Eigenschaft der einzelnen Dateianlage in der Antwort zurückgeben. Finden Sie unter Beispielantwort im [Abrufen einer Anlage (REST)](#GetAttachment) für eine vollständige Liste der Eigenschaften an, die für eine Anlage zurückgegeben wird, wenn Sie **$select**nicht verwenden.

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=/attachments?$select=Name
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments(Name)",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
            "Id": "AAMkAGI2j4kShdM=",
            "Name": "minutes.docx"
        }
    ]
}
```

Das folgende Beispiel zeigt das Abrufen der einzigen Anlage ist ein Outlook-Mail-Element. Die Antwort enthält eine Anlage-ID die ID der Nachricht angefügte auch handelt es sich.

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "LastModifiedDateTime": "2015-09-24T05:57:59Z",
    }
  ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|

**Hinweis** Jede Anlage in der Antwort enthält standardmäßig alle Eigenschaften entsprechend der Anlage Typs. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)sein kann.


**Beispiel-Anforderungen und-Antworten**

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** soll nur die **Name** -Eigenschaft der einzelnen Dateianlage in der Antwort zurückgeben. Finden Sie unter Beispielantwort im [Abrufen einer Anlage (REST)](#GetAttachment) für eine vollständige Liste der Eigenschaften an, die für eine Anlage zurückgegeben wird, wenn Sie **$select**nicht verwenden.

[!code-REST-i[mail_api_get_attachments](./_data/mail_api_get_attachments.json)]


Das folgende Beispiel zeigt das Abrufen der einzigen Anlage ist ein Outlook-Mail-Element. Die Antwort enthält eine Anlage-ID die ID der Nachricht angefügte auch handelt es sich.

```
GET https://outlook.office.com/api/v1.0/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/v1.0/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "DateTimeLastModified": "2015-09-24T05:57:59Z",
    }
  ]
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetAttachment"> </a>
###<a name="get-an-attachment-rest"></a>Abrufen einer Anlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Rufen Sie eine Anlage aus einer bestimmten Nachricht.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}/attachments/{attachment_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der Anlage. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Ein Beispiel finden Sie in [einer Anlage-Auflistung (REST) abrufen](#GetAttachmentCollection) .  
Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

**Antworttyp**

Die gewünschte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [Referenz Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource).


**Beispiel für eine Anforderung (Dateianlage)**

Im folgenden Beispiel wird die Datei an eine bestimmte Nachricht angefügt.

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=/attachments/AAMkAGI2j4kShdM=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
    "Id": "AAMkAGI2j4kShdM=",
    "LastModifiedDateTime": "2014-10-20T00:41:52Z",
    "Name": "minutes.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11585,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQDCAAA4KQAAAAA="
}
```

**Beispiel für eine Anforderung (Referenz Attachment)**

Das folgende Beispiel ruft die Verweis Anlage einer Nachricht ab.

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/attachments/AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments/$entity",
  "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
  "LastModifiedDateTime": "2016-03-12T06:04:38Z",
  "Name": "Koala picture",
  "ContentType": null,
  "Size": 382,
  "IsInline": false,
  "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
  "ProviderType": "OneDriveBusiness",
  "ThumbnailUrl": null,
  "PreviewUrl": null,
  "Permission": "Edit",
  "IsFolder": false
}
```


**Beispiel für eine Anforderung ($Erweitern auf Anlagen)**

Im folgenden Beispiel dient zum Abrufen und erweitert alle 3 Verweis Anlagen Inline mit den Eigenschaften der Nachricht.

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/?$expand=attachments
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages/$entity",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZsPav\"",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAA=",
  "CreatedDateTime": "2016-03-08T01:01:57Z",
  "LastModifiedDateTime": "2016-03-12T06:18:54Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZsPav",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-08T01:01:57Z",
  "SentDateTime": "2016-03-08T01:01:51Z",
  "HasAttachments": true,
  "InternetMessageId": "<SN2SR0101MB00299F0D7D22EE5D380104ED84B20@SN2SR0101MB0029.namsdf01.sdf.exchangelabs.com>",
  "Subject": "RE: New year activity",
  "Body": {
    "ContentType": "html",
    "Content": "<html>\r\n<<body>Let's gather to celebrate the new year! </body>\r\n</html>\r\n"
  },
  "BodyPreview": "What about the tulips?\r\n________________________________\r\nFrom: Dana Swope <danas@contoso.onmicrosoft.com>\r\nSent: Monday, March 7, 2016 10:51:39 PM\r\nTo: Dana Swope; Culinary Expert Group\r\nSubject: RE: New year activity\r\n\r\nLet's gather to celebrate the new year! ",
  "Importance": "Normal",
  "ParentFolderId": "AQMkAGE1MQN7j5uzzwAAAIBDAAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Dana Swope",
      "Address": "danas@contoso.onmicrosoft.com"
    }
  },
  "From": {
    "EmailAddress": {
      "Name": "Dana Swope",
      "Address": "danas@contoso.onmicrosoft.com"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Dana Swope",
        "Address": "danas@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Culinary Expert Group",
        "Address": "Chefs@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGE1MMM2SaRFsKgx7BKVfig=",
  "ConversationIndex": "AQHRaThgdSG4wzZJpEWwqDHsEpV+KJ9OtWGUgAAkYLI=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": false,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADUv0uFAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" },
  "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments",
  "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAL53d0u3BKBJmCxKVxZKBZ8=",
      "LastModifiedDateTime": "2016-03-12T05:54:31Z",
      "Name": "Personal pictures",
      "ContentType": null,
      "Size": 362,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": true
    },
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
      "LastModifiedDateTime": "2016-03-12T06:04:38Z",
      "Name": "Koala picture",
      "ContentType": null,
      "Size": 382,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    },
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAO3wkFiM3KlCpn81m8qS1W0=",
      "LastModifiedDateTime": "2016-03-12T06:18:54Z",
      "Name": "Hydrangea picture",
      "ContentType": null,
      "Size": 412,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    }
  ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments/{attachment_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der Anlage. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Ein Beispiel finden Sie in [einer Anlage-Auflistung (REST) abrufen](#GetAttachmentCollection) .  
Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

 **Antworttyp**

Der angeforderte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder die [Anlage des Elements](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=/attachments/AAMkAGI2j4kShdM=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
    "Id": "AAMkAGI2j4kShdM=",
    "LastModifiedDateTime": "2014-10-20T00:41:52Z",
    "Name": "minutes.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11585,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQDCAAA4KQAAAAA="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments/{attachment_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften der Anlage. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Ein Beispiel finden Sie in [einer Anlage-Auflistung (REST) abrufen](#GetAttachmentCollection) .  
Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

 **Antworttyp**

Der angeforderte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder die [Anlage des Elements](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).


[!code-REST-i[mail_api_get_attachment_by_id](./_data/mail_api_get_attachment_by_id.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="GetAttachmentsClient"> </a>
###<a name="get-one-or-more-message-attachments-client"></a>Erhalten Sie eine oder mehrere e-Mail-Anlagen (Client)

Abrufen von Anlagen auf Nachricht durch Aufrufen der **Attachments** -Eigenschaft. Um eine bestimmte Anlage erhalten möchten, geben Sie die Anlage-ID als Index **Anlagen** 
 -Auflistung oder **GetById** -Methode verwenden.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


**Hinweis** Anlage Sammlungen unterstützen Abfrageausdrücke wie **auswählen**, **OrderBy**und **durchführen**.


In diesem Beispiel wird die-Methode aufgerufen, [den Outlook-Client erstellt](..\api\use-outlook-rest-api.md#GetClient). Der .NET Code wird vorausgesetzt Sie bereits [die Nachrichten-ID haben](#GetMessagesClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
var messages = await outlookClient.Me.Folders["Inbox"].Messages
  .Where(m => m.HasAttachments == true)
  .Expand(m => m.Attachments)
  .Take(10)
  .ExecuteAsync();

foreach (var message in messages.CurrentPage)
{
  var attachments = message.Attachments.CurrentPage;
  System.Diagnostics.Debug.WriteLine("Message '{0}' contains '{1}' attachment(s).",
    message.Subject,
    attachments.Count);

  foreach (var attachment in attachments)
  {
    System.Diagnostics.Debug.WriteLine("*    '{0}' ({1} KB)",
      attachment.Name,
      attachment.Size);
  }
}

```
```javascript-i
outlookClient.me.folders.getFolder('Inbox').messages.getMessages().filter('HasAttachments eq true').fetchAll(10).then(function (result) {
    result.forEach(function (message) {
        message.attachments.getAttachments().fetchAll(100).then(function (attachmentResult) {
            console.log('Message "' + message.subject + '" contains ' + attachmentResult.length + ' attachment(s)');
            attachmentResult.forEach(function (attachment) {
                console.log('*    "' + attachment.name + '" (' + attachment.size + ' KB)');
            });
        });
    }, function (error) {
        console.log(error);
    });
}, function (error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="CreateAttachments"> </a>
##<a name="create-attachments"></a>Erstellen von Anlagen
Erstellen Sie eine Dateianlage oder für eine Nachricht [eine Elementanlage erstellen](#CreateItemAttachment) .

REST-API: [Erstellen Sie eine Dateianlage (REST)](#CreateFileAttachment) | [Erstellen Elementanlage (REST)](#CreateItemAttachment) | 
[Erstellen Sie eine Referenz Anlage (REST)](#CreateReferenceAttachment)



<a name="CreateFileAttachment"></a>
###<a name="create-a-file-attachment-rest"></a>Erstellen Sie eine Dateianlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Fügen Sie eine Dateianlage für eine Nachricht hinzu.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|_Textkörper-Parameter_|
|@odata.type|string|`#Microsoft.OutlookServices.FileAttachment`|
|Name|string|Der Name der Anlage.|
|ContentBytes|Binär|Die Datei anfügen.|

Geben Sie den Parametern **Name** und **ContentBytes** und alle schreibbaren [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) Eigenschaften im Textkörper Anforderung.


<!--comment out until I get a working request body
[!code-REST-i[mail_api_create_file_attachment](./_data/mail_api_create_file_attachment.json)]

-->

 **Antworttyp**

Die neue [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource).

****


<a name="CreateItemAttachment"></a>
###<a name="create-an-item-attachment-rest"></a>Erstellen Sie eine Elementanlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Fügen Sie einer Nachricht eine Elementanlage hinzu.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|_Textkörper-Parameter_|
|@odata.type|string|```#Microsoft.OutlookServices.ItemAttachment```|
|Name|string|Der Name der Anlage.|
|Element|Eine [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) oder eine [Ereignisprozedur](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) Entität.|Das Element an.|

Geben Sie den **Namen** und **Element** -Parameter und alle schreibbaren [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource) Eigenschaften im Textkörper Anforderung.

<!--comment out until I get a working request body
[!code-REST-i[mail_api_create_file_attachment](./_data/mail_api_create_file_attachment.json)]

-->

 **Antworttyp**

Das neue [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

<!--
<a name="AddAttachments"> </a>
## Add attachments

Add a **FileAttachment** or an **ItemAttachment** to a message.

Updating attachments is not supported. Instead, delete the existing attachment and add a new one with updated values.

### Add file attachments

Add a file attachment to a message by getting the file and calling **AddAttachmentAsync**.

This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages).



```cs
    FileAttachment newFileAttachment = new FileAttachment
    {
        ContentBytes = System.IO.File.ReadAllBytes(@"C:\Attachments\capture.png"),
        Name = "capture.png"
    };
    await outlookClient.Me.Messages[messageId].Attachments.AddAttachmentAsync(newFileAttachment);
```



### Add item attachments

Add message attachment to a message by getting the message and calling **AddAttachmentAsync**.

This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages) of the message to add the attachment to and the message to attach.



```cs

    IMessage messageToAttach = await outlookClient.Me.Messages[messageId].ExecuteAsync();
    ItemAttachment newItemAttachment = new ItemAttachment
    {
        Item = (Message)messageToAttach
    };
    await outlookClient.Me.Messages[messageId].Attachments.AddAttachmentAsync(newItemAttachment);
```
-->

****

<a name="CreateReferenceAttachment"></a>


###<a name="create-a-reference-attachment-preview-rest"></a>Erstellen Sie eine Referenz Anlage (Preview) (REST)

<!-- ==================================== Start beta content ====================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Fügen Sie einer Nachricht eine Anlage Verweis hinzu.

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|String|Die Nachrichten-ID.|
|_Textkörper-Parameter_|
|@odata.type|String|```#Microsoft.OutlookServices.ReferenceAttachment```|
|Name|String|Der Anzeigename der Anlage. Erforderlich.|
|SourceUrl|String | URL den Anlageninhalt abrufen. Ist dies eine URL zu einem Ordner, legen Sie dann für den Ordner in Outlook oder Outlook im Web ordnungsgemäß anzuzeigende **IsFolder** auf "true". Erforderlich.|

Geben Sie den **Namen** und **SourceUrl** -Parameter und alle schreibbaren [Verweis Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource) Eigenschaften im Textkörper Anforderung.



**Antworttyp**

Die [Anlage Verweis](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource).


**Beispiel für eine Anforderung**

Das folgende Beispiel fügt eine Anlage Verweis auf eine vorhandene Nachricht. Die Anlage ist eine Verknüpfung zu einer Datei in OneDrive for Business.

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/attachments
Content-Type: application/json

{ 
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment", 
    "Name": "Koala picture", 
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg", 
    "ProviderType": "oneDriveBusiness", 
    "Permission": "Edit", 
    "IsFolder": "False" 
} 
```


**Beispielantwort**

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments/$entity",
  "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
  "LastModifiedDateTime": "2016-03-12T06:04:38Z",
  "Name": "Koala picture",
  "ContentType": null,
  "Size": 382,
  "IsInline": false,
  "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
  "ProviderType": "oneDriveBusiness",
  "ThumbnailUrl": null,
  "PreviewUrl": null,
  "Permission": "edit",
  "IsFolder": false
}
```


**Beispiel für eine Anforderung**

Das folgende Beispiel fügt eine Anlage Verweis in einem Anruf als den Entwurf einer Nachricht erstellen. Die Anlage ist eine Verknüpfung zu einer Datei in OneDrive for Business.

```
POST https://outlook.office.com/api/beta/me/messages
Content-Type: application/json

{
    "Subject": "Plan for dinner",
    "Body": {
      "ContentType": "HTML",
      "Content": "Office anniversary is coming soon!"
    },
    "ToRecipients": [
      {
        "EmailAddress": {
          "Address": "randiw@contoso.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment", 
        "Name": "Hydrangea picture", 
        "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg", 
        "ProviderType": "oneDriveBusiness", 
        "Permission": "Edit", 
        "IsFolder": "False" 
      }
    ]
}
```


**Beispielantwort**

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages/$entity",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZ8qi1\"",
  "Id": "AAMkAGE1Mbs88AADZ0CU9AAA=",
  "CreatedDateTime": "2016-03-12T09:04:54Z",
  "LastModifiedDateTime": "2016-03-12T09:04:54Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZ8qi1",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-12T09:04:54Z",
  "SentDateTime": "2016-03-12T09:04:54Z",
  "HasAttachments": true,
  "InternetMessageId": "<BL2SR0101MB00188944566BDECE6EDE57F384B60@BL2SR0101MB0018.namsdf01.sdf.exchangelabs.com>",
  "Subject": "Plan for dinner",
  "Body": {
    "ContentType": "html",
    "Content": "<html>\r\n<body>\r\nOffice anniversary is coming soon!\r\n</body>\r\n</html>\r\n"
  },
  "BodyPreview": "Office anniversary is coming soon!",
  "Importance": "normal",
  "ParentFolderId": "AQMkAGE1MQN7j5uzzwAAAIBDwAAAA==",
  "Sender": null,
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
      "Name": "Randi Welch",
      "address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGE1MMAAQAJk0cqqggzpKtIHErqyDkcU=",
  "ConversationIndex": "AQHRfD4+mTRyqqCDOkq0gcSurIORxQ==",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADZ0CU9AAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "InferenceClassification": "focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "flagStatus": "notFlagged" },
  "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADZ0CU9AAA%3D')/attachments",
  "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADZ0CU9AAABEgAQAGe4H1iqXwtLsrCCLLkDxqo=",
      "LastModifiedDateTime": null,
      "Name": "Hydrangea picture",
      "ContentType": null,
      "Size": 0,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
      "ProviderType": "oneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    }
  ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End beta content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****


<a name="DeleteAttachments"> </a>
##<a name="delete-attachments"></a>Anlagen löschen

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Die angegebene Anlage einer Nachricht gelöscht. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [Verweis Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)sein.

```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages/{message_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8S-AAA=/attachments/AAMkAGE0Mg67gL7o=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Die angegebene Anlage einer Nachricht gelöscht. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8S-AAA=/attachments/AAMkAGE0Mg67gL7o=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Die angegebene Anlage einer Nachricht gelöscht. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|message_id|string|Die Nachrichten-ID.|
|attachment_id|string|Die Anlage-ID|

[!code-REST-i[mail_api_delete_attachment](./_data/mail_api_delete_attachment.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



<!--
<a name="DeleteAttachments"> </a>
## Delete attachments

You can delete an attachment by calling **DeleteAsync** on a **FileAttachment** or **ItemAttachment**.


This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages).



```cs

    //No ToFileAttachment or Attachment.ExecuteAsync
    Attachment attachmentToDelete = await outlookClient.Me.Messages[messageId].
        Attachments[attachmentId].ToFileAttachment().ExecuteAsync();
    await attachmentToDelete.DeleteAsync();

    IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
    IPagedCollection<IAttachment> attachmentsResults = message.Attachments;
    List<IAttachment> attachmentsPage = attachmentsResults.CurrentPage.ToList();

    // Delete the first attachment in the collection.
    Attachment attachmentToDelete = (Attachment)attachmentsPage[0];
    await attachmentToDelete.DeleteAsync();
```
-->



****


<a name="GetFolders"> </a>
##<a name="get-folders"></a>Abrufen von Ordnern

Sie können eine Ordner-Auflistung abzurufen oder Abrufen von Ordnern im Postfach des Benutzers.

REST-API: [Abrufen einer Auflistung Ordner (REST)](#GetFolderCollection) | [Abrufen eines Ordners (REST)](#GetFolder)

Client-Bibliotheken: [Abrufen eines Ordners oder Ordner-Auflistung (Client)](#GetFoldersClient)


<a name="GetFolderCollection"> </a>
###<a name="get-a-folder-collection-rest"></a>Abrufen einer Auflistung Ordner (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_



<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Alle e-Mail-Ordner im Postfach des angemeldeten Benutzers abrufen (`.../me/MailFolders`), oder rufen Sie die Auflistung Ordner unterhalb des angegebenen Ordners.

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/childfolders
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie aus einem bestimmten Ordner Ordner optimal nutzen.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/MailFolders
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEKAAA=')",
            "Id": "AAMkAGI2AAEKAAA=",
            "DisplayName": "Deleted Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 1,
            "WellKnownName": "deleteditems"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEPAAA=')",
            "Id": "AAMkAGI2AAEPAAA=",
            "DisplayName": "Drafts",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "drafts"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
            "Id": "AAMkAGI2AAEMAAA=",
            "DisplayName": "Inbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 6,
            "TotalItemCount": 6,
            "WellKnownName": "inbox"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEeAAA=')",
            "Id": "AAMkAGI2AAEeAAA=",
            "DisplayName": "Junk Email",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "junkemail"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAELAAA=')",
            "Id": "AAMkAGI2AAELAAA=",
            "DisplayName": "Outbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "outbox"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEJAAA=')",
            "Id": "AAMkAGI2AAEJAAA=",
            "DisplayName": "Sent Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 3,
            "WellKnownName": "sentitems"
        }
    ]
}

```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Rufen Sie die Ordner-Auflistung im Stammordner des angemeldeten Benutzers (`.../me/MailFolders`), oder unter dem angegebenen Ordner. Sie können die `.../me/MailFolders` Verknüpfung mit die Ordner der obersten Ebene-Auflistung abrufen und navigieren zu einem anderen Ordner.

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/childfolders
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie aus einem bestimmten Ordner Ordner optimal nutzen.|

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEKAAA=')",
            "Id": "AAMkAGI2AAEKAAA=",
            "DisplayName": "Deleted Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 1
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEPAAA=')",
            "Id": "AAMkAGI2AAEPAAA=",
            "DisplayName": "Drafts",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
            "Id": "AAMkAGI2AAEMAAA=",
            "DisplayName": "Inbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 6,
            "TotalItemCount": 6
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEeAAA=')",
            "Id": "AAMkAGI2AAEeAAA=",
            "DisplayName": "Junk Email",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAELAAA=')",
            "Id": "AAMkAGI2AAELAAA=",
            "DisplayName": "Outbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEJAAA=')",
            "Id": "AAMkAGI2AAEJAAA=",
            "DisplayName": "Sent Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 3
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Rufen Sie die Ordner-Auflistung im Stammordner des angemeldeten Benutzers (`.../me/folders`), oder unter dem angegebenen Ordner. Sie können die `.../me/folders` Verknüpfung mit die Ordner der obersten Ebene-Auflistung abrufen und navigieren zu einem anderen Ordner.

```no-highlight
GET https://outlook.office.com/api/v1.0/me/folders
GET https://outlook.office.com/api/v1.0/me/folders/{folder_id}/childfolders
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnernamen, wenn Sie aus einem bestimmten Ordner Ordner optimal nutzen.|

[!code-REST-i[mail_api_get_folders](./_data/mail_api_get_folders.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Der angeforderte [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource) -Auflistung.

****


<a name="GetFolder"> </a>
###<a name="get-a-folder-rest"></a>Abrufen eines Ordners (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

Abrufen von Ordnern nach ID.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/MailFolders/inbox
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
    "Id": "AAMkAGI2AAEMAAA=",
    "DisplayName": "Inbox",
    "ParentFolderId": "AAMkAGI2AAEIAAA=",
    "ChildFolderCount": 0,
    "UnreadItemCount": 6,
    "TotalItemCount": 6,
    "WellKnownName": "inbox"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders/inbox
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
    "Id": "AAMkAGI2AAEMAAA=",
    "DisplayName": "Inbox",
    "ParentFolderId": "AAMkAGI2AAEIAAA=",
    "ChildFolderCount": 0,
    "UnreadItemCount": 6,
    "TotalItemCount": 6
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|

[!code-REST-i[mail_api_get_folder_by_id](./_data/mail_api_get_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Der angeforderte [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).

****

<a name="GetFoldersClient"> </a>
###<a name="get-a-folder-or-folder-collection-client"></a>Abrufen eines Ordners oder Ordner-Auflistung (Client)

Abrufen von Ordnern auf oberster Ebene im Postfach mithilfe der `Me.Folders` Kontextmenü-Eigenschaft. Um die Ordner aus einem bestimmten Ordner erhalten möchten, verwenden Sie die **ChildFolders** -Eigenschaft.
Sie können die folgenden bekannten Ordnernamen statt der ID verwenden, für den entsprechenden Ordner: `Inbox`; `SentItems`; `Drafts`; `DeletedItems`.

Beispiel:`outlookClient.Me.Folders["Drafts"].ChildFolders.ExecuteAsync()`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


Wenn Sie einen bestimmten Ordner erhalten möchten, geben Sie die Ordner-ID als der Index des der **Folders** -Auflistung oder verwenden Sie **GetById** -Methode.

**Hinweis** Ordner Websitesammlungen unterstützen Abfrageausdrücke wie **auswählen**, **OrderBy**und **durchführen**.

In diesem Beispiel wird die-Methode aufgerufen, [Ruft den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
var mailFolders = await outlookClient.Me.Folders
  .Take(10)
  .ExecuteAsync();

foreach(var mailFolder in mailFolders.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Mail folder '{0}'.", mailFolder.DisplayName);
}

```
```javascript-i
outlookClient.me.folders.getFolders().fetchAll(100).then(function (result) {
    result.forEach(function (folder) {
        console.log('Folder "' + folder.displayName + '"');
    });
}, function (error) {
    console.log(error);
});
```

<!-- ENDSECTION -->


****

<a name="SynchronizeFolders"></a>
##<a name="synchronize-folder-hierarchy"></a>Synchronisieren der Ordner-Hierarchie

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

Sie können eine flache Tabelle aller Ordner in einem Postfach abzurufen. Fordern Sie beim Synchronisieren einer Ordnerhierarchie Mail dieser Kategorie an.

|**Endpunkt**|**Ordner Kategorie**|
|:-----|:-----|
| Me / MailFolders | E-Mail-Ordner |

Sie können nur die oberste Ebene von jeder Kategorie Ordner synchronisieren. Sie können beispielsweise anfordern _mich / MailFolders_ , aber nicht _Me/MailFolders('inbox')_.

Synchronisierung unterstützt sowohl auf vollständige Synchronisierung starten, der alle Ordner in einer Hierarchie abruft und inkrementelle Synchronisierung, das alle Ordner abruft, die seit der letzten vollständigen Synchronisierung geändert haben. 

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Header-parameter_|
|Bevorzugen|OData.trackchanges|Gibt an, dass die Anforderung einer synchronisierungsanforderung ist.|
|_Textkörper-Parameter_|
|odata.deltaLink|string|Das Token, das das letzte Mal gibt an, dass die Ordnerhierarchie synchronisiert wurde.|

Wenn eine der folgenden Abfrageparameter - `$filter`; `$orderby`; `$search`; `$top` -enthalten sind in der Anforderung ignoriert.

**Antworttyp**

Eine Liste der Ordner in der angeforderten Kategorie.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

Sie können eine flache Tabelle aller Ordner in einem Postfach abrufen. Fordern Sie beim Synchronisieren einer Ordnerhierarchie Mail dieser Kategorie an.

|**Endpunkt**|**Ordner Kategorie**|
|:-----|:-----|
| Me / MailFolders | E-Mail-Ordner |

Sie können nur die oberste Ebene von jeder Kategorie Ordner synchronisieren. Sie können beispielsweise anfordern _mir / MailFolders_ , aber nicht _Me/MailFolders('inbox')_.

Synchronisierung unterstützt sowohl auf vollständige Synchronisierung starten, die alle Ordner in einer Hierarchie abruft und inkrementelle Synchronisierung, die alle Ordner abruft, die seit der letzten vollständigen Synchronisierung geändert wurden. 


_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.Read_
- _WL.IMAP_


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Groupbyheader-Parameters_|
|Bevorzugen|OData.trackchanges|Gibt an, dass die Anforderung einer synchronisierungsanforderung ist.|
|_Textkörper-Parameter_|
|odata.deltaLink|string|Das Token, das das letzte Mal gibt an, dass die Ordnerhierarchie synchronisiert wurde.|

Wenn eine der folgenden Abfrageparameter - `$filter`; `$orderby`; `$search`; `$top` -enthalten sind in der Anforderung ignoriert.

**Antworttyp**

Eine Liste der Ordner in der angeforderten Kategorie.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

Dieses Feature ist derzeit in V2. 0 und Beta. Um mehr zu erfahren, verwenden Sie das Steuerelement in der oberen rechten Ecke des Artikels, und wählen Sie eine der folgenden Versionen.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="CreateFolders"> </a>
##<a name="create-folders"></a>Ordner erstellen

Fügen Sie einen neuen Ordner auf die Ordner-Auflistung.

REST-API: [Erstellen eines Ordners (REST)](#CreateAFolder)

Client-Bibliotheken: [Erstellen eines Ordners (Client)](#CreateFoldersClient)

<a name="CreateAFolder"> </a>
###<a name="create-a-folder-rest"></a>Erstellen Sie einen Ordner (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Erstellen Sie einen untergeordneten Ordner durch den Namen in **"DisplayName"**angegeben. **DisplayName** ist die nur schreibbare Eigenschaft für einen [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/childfolders
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Der Anzeigename des Ordners.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/MailFolders/inbox/childfolders
Content-Type: application/json

{
  "DisplayName": "Company"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders('inbox')/ChildFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Company",
  "ChildFolderCount": 0,
  "UnreadItemCount": 2,
  "TotalItemCount": 27,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/childfolders
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Der Anzeigename des Ordners.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/inbox/childfolders
Content-Type: application/json

{
  "DisplayName": "Company"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('inbox')/ChildFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Company",
  "ChildFolderCount": 0,
  "UnreadItemCount": 2,
  "TotalItemCount": 27
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/childfolders
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Der Anzeigename des Ordners.|

[!code-REST-i[mail_api_create_folder](./_data/mail_api_create_folder.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Den neuen [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).

**Hinweise**

Sie können keinen Ordner der obersten Ebene erstellen. Sie können nur einen Ordner zum Hinzufügen einer `childfolders` Endpunkt.

****

<a name="CreateFoldersClient"> </a>
###<a name="create-a-folder-client"></a>Erstellen Sie einen Ordner (Client)

Erstellen **eines Ordnerobjekts** aus, und geben Sie ihn der **AddFolderAsync** Methode auf den Zielordner **ChildFolders** Auflistung.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die ID](#GetFolders) des übergeordneten Ordners.


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
Folder newFolder = new Folder
{
    DisplayName = "Private"
};
await outlookClient.Me.Folders["Inbox"].ChildFolders.AddFolderAsync(newFolder);

// Get the ID of the new folder.
string folderId = newFolder.Id;
```

<!-- ENDSECTION -->


****


<a name="UpdateFolders"> </a>
##<a name="update-folders"></a>Ordner aktualisieren

Ändern von Ordnernamen.

REST-API: [Aktualisieren eines Ordners (REST)](#UpdateAFolder)

Client-Bibliotheken: [Aktualisieren eines Ordners (Client)](#UpdateFoldersClient)

<a name="UpdateAFolder"> </a>
###<a name="update-a-folder-rest"></a>Aktualisieren eines Ordners (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Ändern Sie den Namen des Ordners an, der im **DisplayName**. Der Name ist die nur schreibbare Eigenschaft für einen [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Den neuen Anzeigenamen des Ordners.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=
Content-Type: application/json

{
  "DisplayName": "Business"
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}

```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Den neuen Anzeigenamen des Ordners.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=
Content-Type: application/json

{
  "DisplayName": "Business"
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}

```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DisplayName|string|Den neuen Anzeigenamen des Ordners.|

[!code-REST-i[mail_api_update_folder_by_id](./_data/mail_api_update_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Der aktualisierten [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).

****

<a name="UpdateFoldersClient"> </a>
###<a name="update-a-folder-client"></a>Aktualisieren eines Ordners (Client)

Ändern von Ordnernamen. **DisplayName** ist die einzige nicht schreibgeschützte Eigenschaft für einen Ordner.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben die Ordner-ID](#GetFoldersClient).


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
folder.DisplayName = "Personal";
await folder.UpdateAsync();

// Get the updated property.
string updatedName = folder.DisplayName;
```

<!-- ENDSECTION -->

Sie können mehrere Updates mithilfe der clientseitigen definieren und senden die Anforderungen alle gleichzeitig (diese batch) mit dem folgenden Muster:
1. Rufen Sie `UpdateAsync(true)` für jede Entität, die Sie aktualisieren möchten. Angeben von `true` registriert die Updates lokal auf dem Client, jedoch nicht auf dem Server bereitstellen.
2. Rufen Sie `outlookClient.Context.SaveChangesAsync()` lokal für die Bereitstellung aller Updates, die registriert sind.

****


<a name="DeleteFolders"> </a>
##<a name="delete-folders"></a>Löschen von Ordnern

Löschen eines Ordners und des gesamten Inhalts.

**Hinweis** Seien Sie vorsichtig, wenn Sie den Ordner löschen. Gelöschte Inhalt können nicht wiederhergestellt werden.
Weitere Informationen finden Sie unter [Elemente werden](http://msdn.microsoft.com/library/c81e3160-e12b-47e0-b3d6-4be28537f301%28Office.15%29.aspx).

REST-API: [Löschen eines Ordners (REST)](#DeleteAFolder)

Client-Bibliotheken: [Löschen eines Ordners (Client)](#DeleteFoldersClient)

<a name="DeleteAFolder"> </a>
###<a name="delete-a-folder-rest"></a>Löschen eines Ordners (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Löschen Sie den in **Folder_id**angegebenen Ordner.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
DELETE https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/BETA/me/MailFolders/AAMkAGE0Mz-l_AAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|

[!code-REST-i[mail_api_delete_folder_by_id](./_data/mail_api_delete_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="DeleteFoldersClient"> </a>
###<a name="delete-a-folder-client"></a>Löschen eines Ordners (Client)

Löschen eines Ordners durch seine ID und die aufrufende **"deleteasync"**.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben die Ordner-ID](#GetFolders).


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.DeleteAsync();
```

<!-- ENDSECTION -->

****

<a name="MoveCopyFolders"> </a>
##<a name="move-or-copy-folders"></a>Verschieben oder Kopieren von Ordnern
Sie können verschieben oder Kopieren eines Ordners in einen anderen Ordner.

REST-API: [Verschieben eines Ordners (REST)](#MoveFolders) | [Kopieren eines Ordners (REST)](#CopyFolders)

Client-Bibliotheken: [verschieben oder Kopieren eines Ordners (Client)](#MoveFoldersClient)

<a name="MoveFolders"> </a>
###<a name="move-a-folder-rest"></a>Verschieben eines Ordners (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Verschieben Sie einen Ordner und seinen Inhalt in einen anderen Ordner mit der **Move** -Methode.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGE0MyxQ9AAA="
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MyxQ9AAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGE0MyxQ9AAA="
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MyxQ9AAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/move
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|

[!code-REST-i[mail_api_move_folder_by_id](./_data/mail_api_move_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **Antworttyp**

Der [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource) , die verschoben wurde.

****


<a name="CopyFolders"> </a>
###<a name="copy-a-folder-rest"></a>Kopieren eines Ordners (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/Mail.ReadWrite_
- _WL.IMAP_

Kopieren Sie einen Ordner und seinen Inhalt in einen anderen Ordner mithilfe der **Copy** -Methode.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-mAAAA=')",
  "Id": "AAMkAGE0Mz-mAAAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


**Beispiel für eine Anforderung**


```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|


```
POST https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-mAAAA=')",
  "Id": "AAMkAGE0Mz-mAAAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/copy
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|folder_id|string|Die ID der Ordner oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|
|_Textkörper-Parameter_|
|DestinationId|string|Die Ziel-Ordner-ID oder die `Inbox`, `Drafts`, `SentItems`, oder `DeletedItems` bekannten Ordnername.|

[!code-REST-i[mail_api_copy_folder_by_id](./_data/mail_api_copy_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

**Antworttyp**

Die neue Kopie des [Ordners](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource).

****

<a name="MoveFoldersClient"> </a>
###<a name="move-or-copy-a-folder-client"></a>Verschieben oder Kopieren eines Ordners (Client)

Verschieben Sie oder kopieren Sie einen Ordner, indem Sie die ID des Zielordners an die **MoveAsync** oder **CopyAsync** -Methode übergeben.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die ID](#GetFoldersClient) des Ordners zu verschieben und den Zielordner.

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.MoveAsync("AAMkADE3N...");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.CopyAsync("Inbox");
```

<!-- ENDSECTION -->

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelt.

- [Erste Schritte mit e-Mail-Nachrichten, Kalender und Kontakte REST-APIs](http://dev.outlook.com/RestGettingStarted).

- Verwenden Sie die Office 365-APIs verwenden die interaktive [API Sandkasten](http://apisandbox.msdn.microsoft.com/)aus.

- Soll Beispiele werden? [Wir haben sie](..\howto\starter-projects-and-code-samples.md).


Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Outlook-REST-API für das Outlook Developer Center](http://dev.outlook.com/RestGettingStarted/Overview)

- [Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)

- [Office 365-app-Authentifizierung und Ressource Autorisierung](..\howto\common-app-authentication-tasks.md)

- [Registrieren Sie Ihre app mit Azure AD manuell, sodass es auf Office 365-APIs zugreifen können](..\howto\add-common-consent-manually.md)

- [Kalender-API-Referenz](..\api\calendar-rest-operations.md)

- [Kontakte-API-Referenz](..\api\contacts-rest-operations.md)

- [Aufgabe REST-API](..\api\task-rest-operations.md) (Vorschau)

- [OneDrive-API](https://dev.onedrive.com/)

- [Ermittlung REST-Dienst-API-Referenzen für Vorgänge](..\api\discovery-service-rest-operations.md)

- [Resource-Referenz für die e-Mail-Nachrichten, Kalender, Kontakte und Aufgabe REST-APIs](..\api\complex-types-for-mail-contacts-calendar.md)


[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]



