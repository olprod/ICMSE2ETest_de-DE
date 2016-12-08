MS TocTitle: Batch Outlook REST-Anforderungen (Preview) Titel: Senden von Outlook-REST-Anforderungen in Batches (Preview) Beschreibung: wie Sie mehrere REST batch fordert zusammen bilden eine einzelne HTTP-Anforderung und verringern den Aufwand davor mehrere HTTP-Verbindungen.
MS ContentId: a842854e-46b3-47d9-8899-c27b481f4e78 <<<<<<< HEAD ms.topic: ms.date-API-Referenz: Mai 16, 2016 =======
ms.date: 13 September 2016
>>>>>>> Staging

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="send-outlook-rest-requests-in-batches-preview"></a>Senden von Outlook-REST-Anforderungen in Batches (Preview)

[!INCLUDE [Add the Outlook REST API filters--beta default v1 v2 disabled](../includes/controls/addOutlookversion_betadefault_v1v2disabled.html)]    


 _**Gilt für:** Exchange Online | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

<p class="previewnote">Dieser Dokumentation umfasst mehrere Outlook-REST-Anforderungen als einem einzelnen Batch-Anforderung an die derzeit in der Vorschau ist senden. Preview-Features können vor der Finalisierung geändert werden, und Code, deren verwendet wird, können beschädigt werden. Aus diesem Grund sollten Sie nur eine Produktionsversion einer API im Allgemeinen in Ihrem Produktionscode verwenden. Falls verfügbar, ist v2. 0 aktuell die bevorzugten Version.</p>

Batchverarbeitung können Sie mehrere Outlook-REST-Anforderungen in einer HTTP-Batchanforderung, die Anzahl der HTTP-Verbindungen und Aufwand reduziert zu platzieren. Die Anforderungen in einem Batch Zugriff auf die Daten des angemeldeten Benutzers von Azure Active Directory in Office 365 oder in einem Microsoft-Konto (Hotmail.com, Live.com, MSN-, Outlook.com oder Passport.com) gesichert. 


**Hinweis** Zur Vereinfachung des Verweises verwendet der Rest des Artikels **"Outlook.com", um diese Microsoft-Kontodomänen einzuschließen**. 

## <a name="overview"></a>Übersicht

Eine REST-Anforderung erfordert eine HTTP-Verbindung zwischen dem Client und Server, der eine bestimmte Menge des Aufwand entstehen. Batchverarbeitung können Sie Verbindung Aufwand zu reduzieren, indem Sie mehrere Aufrufe von REST-API in einer einzelnen HTTP POST-Anforderung an den Endpunkt $batch zu verbinden:  
```
POST https://outlook.office.com/api/{version}/$batch
```
Eine Batchanforderung kann bis zu 20 einzelne REST-API-Aufrufe, die Datenabfrage sein kann enthalten (z. B. GET) oder zu ändern (z. B. POST) Vorgänge. Sie können angeben, dass eine Kopfzeile [bevorzugen](#PreferContinueOnError) , um den Batch fortfahren, auch wenn eine oder mehrere REST-aufrufen fehlschlagen haben.

Batchverarbeitung ist besonders für große Datenmengen synchronisieren. API-Aufrufe im selben Batch unterschiedliche auf Ressourcen zugreifen können, wie Nachrichten und Ereignisse, die für dasselbe Postfach des angemeldeten Benutzers gehören. 

Verwenden Sie Wenn Sie mehr als 20 Anrufe tätigen müssen oder die Reihenfolge der Abschluss der Anrufe wichtig ist, mehrere Batchanforderungen.


## <a name="example"></a>Beispiel

Ein einfaches Beispiel bewährte veranschaulicht Batchverarbeitung. Die folgenden Batchanforderung versetzt 2 Outlook REST-API-Aufrufe in einem einzelnen Batch an:
1. RUFT alle Ereignisse des angemeldeten Benutzers
2. BEREITSTELLEN einer Nachricht.

### <a name="batch-request"></a>Batchanforderung

```
POST https://outlook.office.com/api/beta/$batch HTTP/1.1

Authorization: Bearer aGFwcHlnQGRr==
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_myBatchId


--batch_myBatchId
Content-Type: application/http
Content-Transfer-Encoding: binary

GET  /api/beta/me/events?$select=subject,organizer    HTTP/1.1


--batch_myBatchId
Content-Type: application/http
Content-Transfer-Encoding: binary

POST  /api/beta/me/sendmail    HTTP/1.1
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
          "Address": "rufus@contoso.com"
        }
      }
    ]
  }
}


--batch_myBatchId--
```

### <a name="batch-response"></a>Batchantwort

Batchantwort enthält separate Antwortcodes und Texte, gegebenenfalls für die Batchanforderung und der einzelnen Anrufe. 

```
HTTP/1.1 200 OK
Content-Type: multipart/mixed; boundary=batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Length: 12898

--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 200 OK
OData-Version: 4.0
Content-Type: application/json;odata.metadata=minimal;odata.streaming=true;IEEE754Compatible=false;charset=utf-8

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Events('AAMkAGEtk-hAAA=')",
            "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAX791Eg==\"",
            "Id": "AAMkAGEtk-hAAA=",
            "Subject": "Standup meeting",
            "Organizer": {
                "EmailAddress": {
                    "Address": "rufus@contoso.com",
                    "Name": "Rufus Tallent"
                }
            }
        },

        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Events('AAMkAGED3CAAA=')",
            "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAD6Ir3g==\"",
            "Id": "AAMkAGED3CAAA=",
            "Subject": "Discuss the campaign",
            "Organizer": {
                "EmailAddress": {
                    "Address": "basil@contoso.com",
                    "Name": "Basil Pearsall"
                }
            }
        }
    ]
}
--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 202 Accepted

--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09--
```

****

## <a name="batch-details"></a>Batch-details

### <a name="endpoint-url"></a>Endpunkt-URL

Führen Sie eine POST-ANFORDERUNG für den Endpunkt $batch, um einen Batch von mehrere Outlook-REST-Anforderungen zu senden:
```
POST https://outlook.office.com/api/{version}/$batch HTTP/1.1
```

**Aufmerksamkeit**  Wenn Sie die Stamm-URL-https://outlook.office.com für eine optimale Leistung zu verwenden, wird fügen Sie eine **X-AnchorMailbox** -Kopfzeile hinzu, und legen Sie es an die e-Mail-Adresse des Benutzers. Darüber hinaus verarbeiten Sie den Fall, in dem Postfach eines Benutzers Outlook.com noch nicht für die Outlook-REST API - überprüfen die Fehlercodes MailboxNotEnabledForRESTAPI und MailboxNotSupportedForRESTAPI aktiviert wurde. Weitere Informationen finden Sie [hier](..\api\use-outlook-rest-api.md#OutlookRESTCaution). 

**Hinweise für Entwickler in China** 

- Wenn Sie von apps entwickeln _für Office 365_ in China, Sie sollten auch weiterhin mithilfe der [API-Endpunkten von Office 365 für China](..\api\o365-china-endpoints.md).

- Wenn Sie apps erstellen _für Outlook.com_ in China, müssen Sie die [v2 app-Modell Preview](..\api\use-outlook-rest-api.md#RegAuthConverged)und den folgenden Outlook-REST-Endpunkt verwenden:`https://outlook.office.com/api/{version}`


###<a name="version-of-api"></a>Version der API

Batchverarbeitung ist derzeit in vorschaustatus und steht nur in der Beta-Namespace, geben Sie `{version}` als `beta`:

`https://outlook.office.com/api/beta/$batch`

Da eine Batchanforderung und der REST-Anrufe in der Batch muss den gleichen Host und die Version der API verwenden, können Sie derzeit nur Outlook-REST-aufrufen, die in der Beta-Version verfügbar gemacht batch. 

**Aufmerksamkeit** Beachten Sie, dass einige API-Aufrufe, die Sie in einem Batch enthalten möglicherweise anders in der Beta-Version als in Versionen für allgemeine Verfügbarkeit, wie v2. 0 und v1. 0 reagieren. Im Allgemeinen, wenn Sie API-Aufrufe in vorschaustatus in der Beta-Version verwenden möchten, Planen Sie zum Überprüfen der Features in Ihrer app und damit mögliche neueste Änderungen.
 

###<a name="target-user"></a>Zielbenutzer

Sie können Outlook-REST-API-Aufrufe für dasselbe Postfach des angemeldeten Benutzers in einem Batch gruppieren. Das Postfach kann auf Office 365 oder Outlook.com sein.

### <a name="authentication"></a>Authentifizierung

Senden von [Outlook-REST-API-](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI) Aufrufe als einzelne Anforderungen ähnlich, sollten Sie eine gültige Zugriffstoken in ein **Authorization** -Header einschließen. Wenn Sie diesen Header für die Batchanforderung angeben, sollte das Zugriffstoken die erforderliche Berechtigungen für alle Anrufe in diesem Batch darstellen.
Optional können Sie ein Zugriffstoken für einen bestimmten Aufruf im Batch angeben, wenn dieses Aufrufs ein anderen Zugriffstoken erforderlich sind.
 
Erste ein Zugriffstoken benötigen Sie registriert haben, Ihre app identifiziert und die entsprechende Autorisierung abgerufen. 
[Hier erfahren Sie mehr](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow) über einige optimierte Registrierung und Autorisierung Optionen für Sie. Beachten Sie dies wie Sie mehr erfahren über die Batchverarbeitung von Anforderungen.

### <a name="batch-request-headers"></a>Batch-Anforderungsheader

Umfassen Sie die folgenden Kopfzeilen bei jeder Batchanforderung:

```
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_<batchId> 
```

wobei `{batchId}` ein Batches identifiziert und wird verwendet, um Anfragen im Batch zu begrenzen. Es kann eine GUID oder eine beliebige eindeutige Zeichenfolge sein.

Sie können gegebenenfalls andere Header enthalten. Mit Ausnahme der Header Content-bezogene wie **Content-Type**gelten die Kopfzeilen in der Batchanforderung im Allgemeinen für jeden Vorgang im Batch. Wenn Sie eine Kopfzeile in der Batchanforderung und einen bestimmten Vorgang im Batch angeben, da letztere Vorrang und gilt für diese Operation.   


### <a name="batch-request-body"></a>Batch-Anforderungstext

Starten Sie jeden Vorgang in einem Batch mit den folgenden Zeilen:
```
--batch_{batchId} 
Content-Type: application/http 
Content-Transfer-Encoding: binary 
```
Den letzten Vorgang im Batch mit diesem zu beenden:
```
--batch_{batchId}--
```


### <a name="operations-in-a-batch"></a>Vorgänge in einem batch
Sie können bis zu 20 Vorgänge in einer Batchanforderung angeben.

Ein Vorgang in einem Batch kann eine Datenabfrage, Änderung, Aktion oder Funktion Aufruf Anforderung werden. Während Sie vollständige URLs und Zustand aller Kopfzeilen für jeden Vorgang im Batch wiederholt haben, stellen Sie sicher, bestimmte Kopfzeilen und Textkörper anfordern, wenn sie für einen Vorgang benötigt werden.

### <a name="relative-urls-within-a-batch"></a>Relative URLs in einem batch
Als Alternative zu eine vollständige URL für einen Vorgang angeben können Sie eine relative URL einschließen. Beispielsweise gibt GET-Anforderung im folgenden Beispiel eine URL `/api/beta/me/events` relativ zum angegebenen in der Batchanforderung Host `https://outlook.office.com`.

```
POST https://outlook.office.com/api/beta/$batch HTTP/1.1

User-Agent: YouRock
Authorization: Bearer {accessToken}
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_<myBatchID>

--batch_{batchID}
Content-Type: application/http
Content-Transfer-Encoding: binary

GET  /api/beta/me/events?$select=subject,organizer    HTTP/1.1

--batch_{batchID>}--

```

### <a name="processing-a-batch-request"></a>Verarbeitung einer Batchanforderung
Eine Batchanforderung auf einem eigenen als eine Anforderung verarbeitet und einen eigenen Antwortcode zurückgegeben. Eine wohlgeformte Batchanforderung mit richtigen Kopfzeilen Gibt HTTP 200 OK zurück. Dies bedeutet nicht jedoch, dass alle Anforderungen im Batch erfolgreich waren. Jeder Anforderung im Batch Anforderungstext wiederum separat verarbeitet und einen eigenen Antwortcode, und jeder Antwortnachricht Body und Fehler zurückgegeben.

Der Server möglicherweise Vorgänge in einem Batch in beliebiger Reihenfolge ausführen. Wenn Sie in einer bestimmten Reihenfolge ausgeführten Vorgänge verfügen müssen, sollten Sie nicht in der gleichen Batchanforderung speichern. Stattdessen ein Sendevorgang durch selbst, warten Sie die Antwort vor dem Senden der nächsten Folie.

<a name="PreferContinueOnError"></a>

Standardmäßig wird Sie auf den ersten Vorgang angehalten, der einen Fehler zurückgibt. Sie können angeben, dass die folgenden-Headers, um die Verarbeitung den Fehler ignorieren und Fortfahren mit dem nächsten Vorgang im Batch haben:

```
Prefer: odata.continue-on-error
```



<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelt.

- [Erste Schritte mit e-Mail-Nachrichten, Kalender und Kontakte REST-APIs](http://dev.outlook.com/RestGettingStarted).

- Verwenden Sie die Office 365-APIs verwenden die interaktive [API Sandkasten](https://apisandbox.msdn.microsoft.com/).

- Möchten Sie Beispiele? [Wir haben diese](..\howto\starter-projects-and-code-samples.md).


Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Outlook-REST-API für das Outlook Developer Center](http://dev.outlook.com/RestGettingStarted/Overview)

- [Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)

- [Office 365-app-Authentifizierung und Ressource Autorisierung](..\howto\common-app-authentication-tasks.md)

- [Registrieren Sie Ihre app mit Azure AD manuell, sodass es auf Office 365-APIs zugreifen können](..\howto\add-common-consent-manually.md)

- [Verweisen auf e-Mail-REST-APIs](..\api\mail-rest-operations.md)

- [Kalender-REST-APIs (engl.)](..\api\calendar-rest-operations.md)

- [Kontakte-REST-APIs (engl.)](..\api\contacts-rest-operations.md)

- [Aufgabe REST-API (Preview)](..\api\task-rest-operations.md) 

- [Resource-Referenz für die e-Mail-Nachrichten, Kalender, Kontakte und Aufgabe REST-APIs](..\api\complex-types-for-mail-contacts-calendar.md)

- [Office 365 Daten Extensions REST-API-Referenz](..\api\extensions-rest-operations.md)

- [Personen REST-API-Referenz](..\api\people-rest-operations.md)

- [Benachrichtigungen REST-API-Referenz](..\api\notify-rest-operations.md)

- [Benutzer Foto REST-API-Referenz](..\api\photo-rest-operations.md)

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]
