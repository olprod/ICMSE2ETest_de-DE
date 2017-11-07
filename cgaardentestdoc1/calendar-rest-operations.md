MS. TocTitle: Outlook-Kalender REST-API-Referenz für Titel: Outlook-Kalender REST-API-Referenz Beschreibung: Verweisen auf die Interaktion mit der REST-API für Kalender und Client Bibliotheks-APIs, die Zugriff auf Ereignisse, Kalender und Kalendergruppen in Exchange Online bereitzustellen.
MS. ContentId: 443f1cdf-1adb-46a2-b299-228c6f429954 ms.topic: Verweis (API) ms.date: 29 Juni 2016

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyleshtml)]

# <a name="outlook-calendar-rest-api-reference"></a>Outlook-Kalender REST-API-Referenz


[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2defaulthtml)]

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<p class="previewnote">In dieser Dokumentation werden die API für Suchen Besprechungszeiten, Ereignisse und Verweis Anlagen sind in der Vorschau Abbrechen behandelt. Preview-Features können vor dem Abschluss des Vorgangs geändert werden, und Code, der diese Elemente verwendet werden, können beschädigt. Aus diesem Grund sollten Sie nur eine Produktionsversion einer API im Allgemeinen in Ihrem Produktionscode verwenden. Falls verfügbar, ist v2. 0 aktuell die bevorzugten Version.</p>

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

   
 _**Gilt für:** Exchange Online | Office 365 | Hotmail.com | Live.com | MSN | Outlook.com | Passport.com_

Die Kalender-API bietet Zugriff auf Ereignisse, Kalender und Kalenderdaten Gruppe von Azure Active Directory in Office 365 gesichert, und ähnliche Daten in Microsoft-Konten in diesen Domänen speziell: Hotmail.com, Live.com, MSN-, Outlook.com und Passport.com. 
  

<!-- Can add the following sentence back once the client libraries have been updated for converged auth and outlook.com

You can access the Calendar API by calling the corresponding REST APIs directly in your apps, or by using the Office 365 client libraries and SDKs.
-->

**Hinweis** 

- Die Ausnahme ist die API [Besprechungszeiten suchen](#FindMeetingTimesPreview), die zu Office 365 Postfächer (auf Azure AD) und nicht zum Microsoft-Konten angewendet wird. 
- Zur Vereinfachung des Verweises verwendet der Rest des Artikels **"Outlook.com" Einbeziehung die oben aufgeführten Microsoft Kontendomänen**.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

**In der Beta-Version der API nicht interessiert?** Verwenden Sie in der oberen rechten Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

**Nicht interessiert v2. 0 der API?** Verwenden Sie in der rechten oberen Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->




<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

**Nicht in v1. 0 der API interessiert?** Verwenden Sie in der rechten oberen Ecke des Steuerelements, und wählen Sie die gewünschte Version aus.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->
 
 
 
## <a name="all-calendar-api-operations"></a>Alle Kalender API-Vorgänge

<a name="EventOperations"></a> 
 **Ereignisvorgänge** ein Ereignis einen Termin oder eine Besprechung auf den Kalender des Benutzers darstellt. Ein Ereignis kann eine Datenreihe Master (für Ereignisserien), das Auftreten eines Serientermins, eine einzelne Instanz oder eine Ausnahme sein.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

[Get Events](#GetEvents) | [synchrone Ereignisse](#SyncCalendarView) | [Besprechungszeiten suchen (Preview)](#FindMeetingTimesPreview) | [Erstellen Ereignisse](#CreateEvents) | 
[Ereignisse aktualisieren](#UpdateEvents) | [auf Ereignisse reagieren](#RespndToEvents) | [Delete-Ereignisse](#DeleteEvents) | [Abbrechen Ereignisse (Preview)](#CancelEvents) | 
[Abrufen von Anlagen](#GetAttachments) | [Erstellen Anlagen](#CreateAttachments) | [Anlagen löschen](#DeleteAttachments) | 
[Reminders erhalten möchten](#GetReminders) | [erneut erinnern Erinnerungen](#SnoozeReminders)] | [Dismiss Erinnerungen](#DismissReminders)


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

[Get Events](#GetEvents) | [synchrone Ereignisse](#SyncCalendarView) | [Erstellen-Ereignisse](#CreateEvents) | 
[Aktualisieren Ereignisse](#UpdateEvents) | [auf Ereignisse reagieren](#RespndToEvents) | [Delete-Ereignisse](#DeleteEvents) | 
[Abrufen von Anlagen](#GetAttachments) | [Erstellen Anlagen](#CreateAttachments) | [Anlagen löschen](#DeleteAttachments) | 
[Reminders erhalten](#GetReminders) | [erneut erinnern Erinnerungen](#SnoozeReminders)] | [Dismiss Erinnerungen](#DismissReminders)


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

[Get Events](#GetEvents) | [synchrone Ereignisse](#SyncCalendarView) | [Erstellen-Ereignisse](#CreateEvents) | 
[Aktualisieren Ereignisse](#UpdateEvents) | [auf Ereignisse reagieren](#RespndToEvents) | [Delete-Ereignisse](#DeleteEvents) | 
[Abrufen von Anlagen](#GetAttachments) | [Erstellen Anlagen](#CreateAttachments) | [Anlagen löschen](#DeleteAttachments) | 
[Reminders erhalten](#GetReminders) | [erneut erinnern Erinnerungen](#SnoozeReminders)] | [Dismiss Erinnerungen](#DismissReminders)

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->




<a name="CalendarOperations"> </a>
**Kalender-Vorgänge** Ein Kalender dient als Container für Ereignisse. Ein Benutzer kann mehrere Kalender besitzen. In Office 365 kann jeden Kalender Kalendergruppen zugewiesen werden.

[Abrufen von Kalendern](#GetCalendars) | [Erstellen Kalender](#CreateCalendars) | [Aktualisieren von Kalendern](#UpdateCalendars) | [Kalender löschen](#DeleteCalendars) 

<a name="CalendarGroupOperations"></a> 
 **Kalender Gruppe Vorgänge** Kalendergruppen bieten eine Möglichkeit, mehrere Kalender zu organisieren. Benutzer können mehrere Kalender in einer einzelnen Kalendergruppe in Outlook oder Outlook Web App hinzufügen. Dies vereinfacht die für Benutzer schnell alle Kalender innerhalb der Gruppe anzeigen.


**Hinweis** Outlook.com unterstützt nur die Kalender Standardgruppe zugänglich ist die `../me/calendars` Verknüpfung. Sie können nicht dieser Kalendergruppe löschen oder einem anderen Kalendergruppe erstellen.


[Abrufen von Kalendergruppen](#GetCalendarGroups) | [Kalendergruppen erstellen](#CreateCalendarGroups) | 
[Aktualisieren Kalendergruppen](#UpdateCalendarGroups) | [Kalendergruppen löschen](#DeleteCalendarGroups)  

Siehe auch:

[REST-API-Ereignis Resource](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) | 
[REST-API Kalender Ressource](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) |
[REST-API Kalender Group-Ressource](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)



<a name="Overview"> </a>
## <a name="using-the-calendar-rest-api"></a>Verwenden des Kalenders REST-API

### <a name="authentication"></a>Authentifizierung

Wie andere [Outlook-REST-API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)für jede Anforderung an den Kalender API sollten Sie eine gültige Zugriffstoken einschließen. Erste ein Zugriffstoken benötigen Sie registriert haben, Ihre app identifiziert und die entsprechende Autorisierung abgerufen. Sie können [Hier erfahren Sie mehr](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow) über einige optimierte Registrierung und Autorisierungsoptionen für die für Sie. Beachten Sie dies wie Sie bestimmte Vorgänge in der Kalender API fortsetzen.

<a name="SupportedVersions"> </a>

###<a name="version-of-api"></a>Version der API

Der Kalender REST-API wird in allen Versionen von Outlook-REST-API unterstützt. Die Funktionalität kann je nach der bestimmten Version abweichen.

###<a name="target-user"></a>Zielbenutzer

Die Kalender-API-Anforderungen werden immer im Auftrag des aktuellen Benutzers ausgeführt. 

Weitere Informationen für alle Untermengen der Outlook-REST-API finden Sie unter [Verwendung der Outlook-REST-API](..\api\use-outlook-rest-api.md) .

****

<a name="GetEvents"> </a>
## <a name="get-events"></a>Abrufen von Ereignissen

Rufen Sie eine Ereignissammlung oder ein Ereignis. 

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

Alle Vorgänge, die Ereignisse im Kalender erhalten können die _bevorzugen: outlook.timezone_ HTTP-Headers, geben Sie die Zeitzone für die Anfangs- und Endzeiten in der Antwort. Beispielsweise die folgenden _bevorzugen: outlook.timezone_ Header legt die Anfangs- und Endzeiten in der Antwort Eastern Standard Time.

```
Prefer: outlook.timezone="Eastern Standard Time"
``` 

Wenn Sie keine angeben die _bevorzugen: outlook.timezone_ -Headers, die Anfangs- und Endzeiten in der Antwort in UTC zurückgegeben werden.

Sie können die Eigenschaften _OriginalStartTimeZone_ und _OriginalEndTimeZone_ für die Ressource _Ereignis_ verwenden, um zu ermitteln, die Zeitzone verwendet, wenn das Ereignis erstellt wurde.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->
<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

Alle Vorgänge, die Kalenderereignisse abrufen können die _bevorzugen: outlook.timezone_ HTTP-Header auf die Zeitzone für die Anfangs- und Endzeiten in der Antwort angeben. Beispielsweise den folgenden _bevorzugen: outlook.timezone_ Header legt die Anfangs- und Endzeiten der Reaktion auf Eastern Standard Time.

```
Prefer: outlook.timezone="Eastern Standard Time"
``` 

Wenn Sie keine angeben die _bevorzugen: outlook.timezone_ -Headers, die Anfangs- und Endzeiten in der Antwort in UTC zurückgegeben werden. [Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. 

Sie können _OriginalStartTimeZone_ und _OriginalEndTimeZone_ -Eigenschaften für die Ressource _Ereignis_ verwenden, um zu ermitteln, die Zeitzone verwendet, wenn das Ereignis erstellt wurde.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->


REST-API: [Abrufen eine Kalenderansicht (REST)](#GetCalendarView) |  
[Erste Reihe Master- und einzelne Ereignisse (REST)](#GetEventCollection) |
 [Ereignisinstanzen (REST) abgerufen](#GetEventInstances) | [ein Ereignis (REST)](#GetEvent) 

Client-Bibliotheken: [Get Events aus dem Kalender des Benutzers (Client)](#GetEventsClient)

****

<a name="GetCalendarView"> </a>
###<a name="get-a-calendar-view-rest"></a>Abrufen einer Kalenderansicht (REST) 

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Abrufen der vorkommen, Ausnahmen und einzelne Instanzen von Ereignissen in einer Kalenderansicht definiert durch ein Zeitbereich, aus dem primären Kalender des Benutzers (`../me/calendarview`) oder aus einem anderen Kalender.
   

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Datum und Uhrzeit für das Ende des Ereignisses.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Mal in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Hinweis** Standardmäßig sind in der Antwort jedes Ereignis alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise erhalten Sie die Kalenderansicht für den Monat Oktober, nur die Subject-Eigenschaft für jedes Ereignis zurückgeben. Unter der Annahme, dass die _bevorzugen: outlook.timezone_ Kopfzeile ist nicht in der Anforderung enthalten ist, ist die Zeitzone UTC. 

```
GET https://outlook.office.com/api/beta/me/calendarview?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject
```

 **Antworttyp**

Die erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) innerhalb des angegebenen Zeitraums.


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Das Datum und die Uhrzeit für das Ende des Ereignisses.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten in die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Hinweis** Standardmäßig enthält jedes Ereignis in der Antwort alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung zu müssen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise erhalten Sie die Kalenderansicht für den Monat Oktober, nur die Subject-Eigenschaft für jedes Ereignis zurückgeben. Unter der Annahme, dass die _bevorzugen: outlook.timezone_ Kopfzeile ist nicht in der Anforderung enthalten ist, ist die Zeitzone UTC. 

```
GET https://outlook.office.com/api/v2.0/me/calendarview?startDateTime=2014-10-01T01:00:00&endDateTime=2014-10-31T23:00:00&$select=Subject
```

 **Antworttyp**

Die erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) innerhalb des angegebenen Zeitraums.


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendarview?start={start_datetime}&end={end_datetime}
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Das Datum und die Uhrzeit für das Ende des Ereignisses.|

**Hinweis** Standardmäßig sind in der Antwort jedes Ereignis alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung zu müssen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise erhalten Sie die Kalenderansicht für den Monat Oktober, nur die Subject-Eigenschaft für jedes Ereignis zurückgeben: 

```
GET https://outlook.office.com/api/v1.0/me/calendarview?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject
```

 **Antworttyp**

Die erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) innerhalb des angegebenen Zeitraums.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetEventCollection"> </a>
###<a name="get-series-master-and-single-events-rest"></a>Erste Reihe Master- und einzelne Ereignisse (REST) 

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Eine Auflistung von Series Master- und einzelne Instanz Ereignissen aus dem primären Kalender des Benutzers abrufen (`../me/events`) oder aus einem anderen Kalender. Wenn expanded-Ereignisinstanzen erhalten möchten, können Sie  [erhalten die Kalenderansicht](#GetCalendarView) oder [Instanzen eines Ereignisses abgerufen](#GetEventInstances).



<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/events
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Header-Parameter|
|Bevorzugen:|Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie Ereignisse aus einem bestimmten Kalender optimal nutzen.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Mal in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Kopfzeile ist nicht angegeben ist, Start-und Endzeit in UTC zurückgegeben werden.

**Hinweis** Jedes Ereignis in der Antwort enthält alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Finden Sie im nächste Beispiel. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Das folgende Beispiel veranschaulicht das **$select** verwenden, um nur die Eigenschaften **Subject**, **Organisator**, **Start** und **Ende** der einzelnen Ereignisse in der Antwort zurückgeben angeben. Finden Sie in der ersten Beispielantwort in [ein Ereignis (REST)](#GetEvent) für eine vollständige Liste der Eigenschaften, die für ein Ereignis zurückgegeben wird, wenn Sie **$select**nicht verwenden.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/events?$select=Subject,Organizer,Start,End
```

**Beispielantwort**

Statuscode: 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer,Start,End)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyDAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWw==\"",
            "Id": "AAMkAGI28tEyDAAA=",
            "Subject": "Scrum",
            "Start": {
                "DateTime": "2015-11-02T17:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-02T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyCAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWg==\"",
            "Id": "AAMkAGI28tEyCAAA=",
            "Subject": "team lunch",
            "Start": {
                "DateTime": "2015-11-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-03T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2ADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49w==\"",
            "Id": "AAMkAGI2G93AAA=",
            "Subject": "Weekly Meeting on Contoso Project",
            "Start": {
                "DateTime": "2014-10-13T21:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T22:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49g==\"",
            "Id": "AAMkAGI2TG92AAA=",
            "Subject": "Daily Team Meeting",
            "Start": {
                "DateTime": "2014-10-13T18:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T18:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2TG91AAA=",
            "Subject": "Rob:Alex 1:1",
            "Start": {
                "DateTime": "2014-10-15T16:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-15T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2TG90AAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2015-11-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-27T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2TG9zAAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2014-11-27T00:00:00"
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-11-28T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49Q==\"",
            "Id": "AAMkAGI2TG9yAAA=",
            "Subject": "New Year's Day Holiday",
            "Start": {
                "DateTime": "2015-01-01T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-01-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2TG9xAAA=",
            "Subject": "Christmas Holiday",
            "Start": {
                "DateTime": "2014-12-25T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-12-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie Ereignisse aus einem bestimmten Kalender optimal nutzen.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Hinweis** Jedes Ereignis in der Antwort umfasst alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Finden Sie im nächste Beispiel. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Das folgende Beispiel veranschaulicht das **$select** verwenden, um nur die Eigenschaften **Subject**, **Organisator**, **Start** und **Ende** der einzelnen Ereignisse in der Antwort zurückgeben angeben. Finden Sie in der ersten Beispielantwort in [ein Ereignis (REST)](#GetEvent) für eine vollständige Liste der Eigenschaften, die für ein Ereignis zurückgegeben wird, wenn Sie **$select**nicht verwenden.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/events?$select=Subject,Organizer,Start,End
```

**Beispielantwort**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer,Start,End)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyDAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWw==\"",
            "Id": "AAMkAGI28tEyDAAA=",
            "Subject": "Scrum",
            "Start": {
                "DateTime": "2015-11-02T17:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-02T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyCAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWg==\"",
            "Id": "AAMkAGI28tEyCAAA=",
            "Subject": "team lunch",
            "Start": {
                "DateTime": "2015-11-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-03T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2ADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49w==\"",
            "Id": "AAMkAGI2G93AAA=",
            "Subject": "Weekly Meeting on Contoso Project",
            "Start": {
                "DateTime": "2014-10-13T21:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T22:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49g==\"",
            "Id": "AAMkAGI2TG92AAA=",
            "Subject": "Daily Team Meeting",
            "Start": {
                "DateTime": "2014-10-13T18:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T18:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2TG91AAA=",
            "Subject": "Rob:Alex 1:1",
            "Start": {
                "DateTime": "2014-10-15T16:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": "2014-10-15T17:30:00Z",
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2TG90AAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2015-11-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-27T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2TG9zAAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2014-11-27T00:00:00"
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-11-28T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49Q==\"",
            "Id": "AAMkAGI2TG9yAAA=",
            "Subject": "New Year's Day Holiday",
            "Start": {
                "DateTime": "2015-01-01T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-01-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2TG9xAAA=",
            "Subject": "Christmas Holiday",
            "Start": {
                "DateTime": "2014-12-25T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-12-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID, wenn Sie Ereignisse aus einem bestimmten Kalender optimal nutzen.|

**Hinweis** Jedes Ereignis in der Antwort umfasst alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Finden Sie im nächste Beispiel. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Das folgende Beispiel veranschaulicht das **$select** verwenden, um nur die Eigenschaften **Subject**, **Organisator**, **Start** und **Ende** der einzelnen Ereignisse in der Antwort zurückgeben angeben. Finden Sie in der ersten Beispielantwort in [ein Ereignis (REST)](#GetEvent) für eine vollständige Liste der Eigenschaften, die für ein Ereignis zurückgegeben wird, wenn Sie **$select**nicht verwenden.


```REST-i
{
   "method": "GET",
   "resourceFormat": "https://outlook.office.com/api/v1.0/me/events?$select=Subject,Organizer,Start,End",
   "requestUrl": "https://outlook.office.com/api/v1.0/me/events?$select=Subject,Organizer,Start,End",
   "requestHeaders": {
      "Accept": "application/json"
   },
   "parameterDetails": [],
   "statusCode": 200,
   "responseBody": {
    "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:13:47.3959685Z",
            "DateTimeLastModified": "2014-10-19T23:13:47.6772234Z",
            "Subject": "Weekly Meeting on Contoso Project",
            "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-13T21:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-10-13T22:00:00Z",
            "EndTimeZone": "Pacific Standard Time",           
            "Location": {
                "DisplayName": "Alex's Office"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Janet Schorr"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Pavel Bansky"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "Weekly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "First",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-13T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48A==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG92AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48A==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:13:01.9733945Z",
            "DateTimeLastModified": "2014-10-19T23:13:02.426753Z",
            "Subject": "Daily Team Meeting",
            "BodyPreview": "Daily sync on project progress and team member status",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nDaily sync on project progress and team member status\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-13T18:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-10-13T18:30:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": "Team Room"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "roby@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Rob Young"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Pavel Bansky"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Janet Schorr"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Garth Fort"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Katie Jordan"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "Weekly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "First",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday",
                        "Tuesday",
                        "Wednesday",
                        "Thursday",
                        "Friday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-13T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG91AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:12:40.7543183Z",
            "DateTimeLastModified": "2014-10-19T23:12:41.0043215Z",
            "Subject": "Rob:Alex 1:1",
            "BodyPreview": "Let's meet every month to engage in project review and career discussion",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none\"><!-- p { margin-top: 0px; margin-bottom: 0px; }--></style>\r\n</head>\r\n<body dir=\"ltr\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>Let's meet every month to engage in project review and career discussion<br>\r\n</p>\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-15T16:30:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2014-10-15T17:30:00Z",
            "EndTimeZone": "Pacific Standard Time",                      
            "Location": {
                "DisplayName": "Alex's Office"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "roby@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Rob Young"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "RelativeMonthly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "Third",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Wednesday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-15T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG90AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46g==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:48:13.6271741Z",
            "DateTimeLastModified": "2014-10-19T08:48:13.6427985Z",
            "Subject": "Thanksgiving Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-11-26T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2015-11-27T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9zAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:46:18.8700566Z",
            "DateTimeLastModified": "2014-10-19T08:46:18.8856803Z",
            "Subject": "Thanksgiving Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-11-27T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-11-28T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46A==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46A==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:43:37.2138006Z",
            "DateTimeLastModified": "2014-10-19T08:43:37.2450436Z",
            "Subject": "New Year's Day Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-01-01T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2015-01-02T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9xAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x45w==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:33:45.1538198Z",
            "DateTimeLastModified": "2014-10-19T08:33:45.200696Z",
            "Subject": "Christmas Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-12-25T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2014-12-26T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        }
    ]
}
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetEventInstances"></a>
###<a name="get-event-instances-rest"></a>Ereignisinstanzen (REST) abgerufen

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Sie können die Instanzen (vorkommen) eines Ereignisses für einen angegebenen Zeitraum abrufen. Wenn das Ereignis einen **SeriesMaster** -Typ ist, gibt dies die Vorkommen und Ausnahmen des Ereignisses in den angegebenen Zeitraum.


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standard-Zeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|start_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses endet.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

 **Antworttyp**

Der angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) -Auflistung.

**Hinweis** Standardmäßig sind in der Antwort jedes Ereignis alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.  
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise für den Monat Oktober Instanzen eines bestimmten Ereignisses abgerufen, nur die Eigenschaften **Subject**, **Anfang** und **Ende** jeder Instanz zählen: 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/beta/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|start_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses endet.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

 **Antworttyp**

Der angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) -Auflistung.

**Hinweis** Standardmäßig sind in der Antwort jedes Ereignis alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.  
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise für Oktober Instanzen eines bestimmten Ereignisses abgerufen, nur die Eigenschaften **Subject**, **Start** und **Ende** jeder Instanz enthalten: 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|start_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|UTC-Datum und Uhrzeit des Ereignisses endet.|


 **Antworttyp**

Der angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) -Auflistung.

**Hinweis** Standardmäßig sind in der Antwort jedes Ereignis alle zugehörigen Eigenschaften. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben.  
Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Beispielsweise für den Monat Oktober Instanzen eines bestimmten Ereignisses abgerufen, nur die Eigenschaften **Subject**, **Anfang** und **Ende** jeder Instanz zählen: 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetEvent"> </a>
###<a name="get-an-event-rest"></a>Abrufen eines Ereignisses (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Rufen Sie ein Ereignis-ID


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standard-Zeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2TG93AAA=
```

**Beispielantwort**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "CreatedDateTime": "2014-10-19T23:13:47.3959685Z",
        "LastModifiedDateTime": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        },        
        "Location": {
            "DisplayName": "Alex's Office",
            "Address": null,
            "Coordinates": null,
            "LocationEmailAddress": "",
            "LocationUri": ""
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "RecurrenceTimeZone": "Pacific Standard Time",
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13",
                "EndDate": "2014-11-13",
                "NumberOfOccurrences": 0
            }
        },
        "OriginalEndTimeZone": "Pacific Standard Time",
        "OriginalStartTimeZone": "Pacific Standard Time",
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        },
        "OnlineMeetingUrl": null
    }
```


**Antworttyp**

Das angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften des Ereignisses. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** zurückgeben nur der **Betreff**, **Organisieren**, **Start** und **End** -Eigenschaften des Ereignisses angegeben. 


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2TG93AAA=?$select=Subject,Organizer,Start,End
```

**Beispielantwort**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "Subject": "Weekly Meeting on Contoso Project",
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        }, 
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standardzeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2TG93AAA=
```

**Beispielantwort**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "CreatedDateTime": "2014-10-19T23:13:47.3959685Z",
        "LastModifiedDateTime": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        },        
        "Location": {
            "DisplayName": "Alex's Office",
            "Address": null
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "RecurrenceTimeZone": "Pacific Standard Time",
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13",
                "EndDate": "2014-11-13",
                "NumberOfOccurrences": 0
            }
        },
        "OriginalEndTimeZone": "Pacific Standard Time",
        "OriginalStartTimeZone": "Pacific Standard Time",
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


**Antworttyp**

Das angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften des Ereignisses. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** zurückgeben nur der **Betreff**, **Organisieren**, **Start** und **End** -Eigenschaften des Ereignisses angegeben. 

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2TG93AAA=?$select=Subject,Organizer,Start,End
```

**Beispielantwort**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "Subject": "Weekly Meeting on Contoso Project",
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        }, 
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

```REST-i
[!INCLUDE [calendar_api_get_event_by_id](./_data/calendar_api_get_event_by_id.json)]
```


**Antworttyp**

Das angeforderte [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

**Hinweis** Die Antwort enthält standardmäßig alle Eigenschaften des Ereignisses. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrage-Parameter](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

Im folgenden Beispiel wird veranschaulicht, wie mit **$select** zurückgeben nur der **Betreff**, **Organisieren**, **Start** und **End** -Eigenschaften des Ereignisses angegeben. 

```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}?$select=Subject,Organizer,Start,End",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=?$select=Subject,Organizer,Start,End",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "DateTimeCreated": "2014-10-19T23:13:47.3959685Z",
        "DateTimeLastModified": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-10-13T21:00:00Z",
        "StartTimeZone": "Pacific Standard Time",        
        "End": "2014-10-13T22:00:00Z",
        "EndTimeZone": "Pacific Standard Time",        
        "Location": {
            "DisplayName": "Alex's Office"
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13T00:00:00-07:00",
                "EndDate": "0001-01-01T00:00:00Z",
                "NumberOfOccurrences": 0
            }
        },
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="GetEventsClient"></a>
### <a name="get-events-from-the-users-calendar-client"></a>Abrufen von Ereignissen aus den Kalender des Benutzers (Client)

Rufen Sie die Ereignisse aus Standardkalender des Benutzers an. Um die Ereignisse aus einem anderen Kalender abzurufen, rufen Sie den Kalender **Events** -Eigenschaft.

Beispiel:`outlookClient.Me.Calendars[calendarId].Events.ExecuteAsync()`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


Wenn ein bestimmtes Ereignis erhalten möchten, können die Ereignis-ID als Index der Auflistung **Ereignisse** angeben oder **GetById** -Methode verwenden.

**Hinweis** Ereignis Websitesammlungen unterstützen Abfrageausdrücke wie **auswählen**, **OrderBy**und **durchführen**.

In diesem Beispiel wird die-Methode aufgerufen, [den Outlook-Client erstellt](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar" -->

```cs-i
var outlookClient = await CreateOutlookClientAsync("Calendar");
var events = await outlookClient.Me.Events
  .Take(10)
  .ExecuteAsync();
 
foreach(var calendarEvent in events.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Event '{0}'.", calendarEvent.Subject);
}
 
```

```javascript-i
outlookClient.me.events.getEvents().fetch().then(function (result) {
    result.currentPage.forEach(function (event) {
console.log('Event "' + event.subject + '"')
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->


Dieses Anrufs gibt Ereignis Datenreihen, nicht die einzelnen erweiterten Instanzen für wiederkehrende Ereignisse (beispielsweise eine wöchentliche Team Besprechung) zurück.

Abfragen von Ereignisinstanzen wird in der Clientbibliothek nicht unterstützt. Sie können die REST-API für die Abfrage der **CalendarView** -Eigenschaft für die Ressource  [Kalender](..\api\calendar-rest-operations.md#CalendarResource) oder die Eigenschaft **Instanzen** für die Ressource [Ereignis](..\api\calendar-rest-operations.md#EventResource) verwenden:


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->
 
<!--Update c# example to get instance-->
<!--Update js example and remove note when this works in js-->

****

<a name="SyncCalendarView"> </a>
##<a name="sync-events"></a>Synchrone Ereignisse  

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Synchronisieren und ne, aktualisiert oder gelöscht werden Ereignisse in einem angegebenen Zeitraum aus dem primären Kalender des Benutzers (`../me/calendarview`) oder aus einem anderen Kalender. Eine solche ein Satz von Ereignissen in einem Zeitraum ist auch bekannt als eine Kalenderansicht. Die zurückgegebene Ereignisse gehören vorkommen und Ausnahmen von sich wiederholenden Reihe und einzelne Instanzen. 

Synchronisieren von in der Regel eine Kalenderansicht erfordert eine Round von zwei oder mehr Synchronisierungsanfragen, von denen jedes eine GET-Anruf ist. Verwenden Sie zum Synchronisieren einer Kalenderansicht die GET-Methode, ähnlich wie Sie [eine Kalenderansicht erhalten möchten](#GetCalendarView), mit der Ausnahme, dass Sie bestimmte Anforderungsheader und _DeltaToken_ oder _SkipToken_ bei Bedarf einschließen.  

**Anforderungsheader**

- Sie müssen angeben, die "bevorzugen: odata.track Änderungen" Kopfzeile in alle Sync fordert ausgenommen solche, die enthalten eine `skipToken` aus einer früheren Sync-Anforderung zurückgegeben wird. Suchen Sie in der ersten Antwort, nach der _Einstellung angewendet: odata.track Änderungen_ Header zu bestätigen, dass die Ressource unterstützt synchronisieren, bevor Sie fortfahren. (Weitere Informationen zu einer `skipToken` im [zweiten Antwort-Beispieldaten](#SyncCalendarViewSampleSecondResponse) unten.)
- Sie können angeben, die "bevorzugen: odata.maxpagesize={x}" Kopfzeile an, dass die maximale Anzahl von Ereignissen, die zu Anforderung gibt synchronisierenden.

Hier ist eine typische Rundung der Synchronisierung von Ereignissen in einer Kalenderansicht:

1. Erstellen die anfängliche GET-Anforderung mit der obligatorisch _bevorzugen: odata.track Änderungen_ Kopfzeile. Die erste Antwort auf eine Anforderung Sync gibt immer einen _DeltaToken_zurück. (Die zweiten und nachfolgenden GET-Anfragen unterscheiden sich von der ersten GET-Anforderung, einschließlich einer _DeltaToken_ oder einer _SkipToken_ in einer vorherigen Antwort erhalten.)

2. Wenn die erste Antwort zurückgegeben wird die _Einstellung angewendet: odata.track Änderungen_ Kopfzeile, können Sie mit der Synchronisierung fortfahren.

  - Stellen Sie eine zweite GET-Anforderung. Geben Sie den _bevorzugen: odata.track Änderungen_ Kopf- und der _DeltaToken_ aus der ersten GET zu ermitteln, ob es keine weiteren Ereignisse sind zurückgegeben. Wenn mehr Ereignisse verfügbar oder eine _DeltaToken_ vorhanden sind, wenn das letzte Ereignis in diesem Fall können Sie die Übertragung synchronisiert wurde, wird die zweite Anforderung zusätzliche Ereignisse und eine _SkipToken_ zurückgegeben.

  - Weiterhin synchronisieren durch das Senden eines Anrufs GET und einschließlich einer _SkipToken_ , die vom vorherigen Aufruf zurückgegeben wird. Beendet, wenn Sie eine endgültige Antwort erhalten, die enthält ein _@odata.deltaLink_ Kopfzeile mit einem _DeltaToken_ erneut, womit die Synchronisierung abgeschlossen ist.

Sehen Sie sich die Syntax für die Anfangs- und nachfolgende Aufrufe in einer Runde von Synchronisierung an.

<!-- ==================================== Begin beta content ======================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

**Im Standardkalender synchronisieren**

Anfängliche Anforderung: 

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

Dritte oder nachfolgenden Anforderung in der gleichen runde  

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**In einem bestimmten Kalender synchronisieren**

Anfängliche Anforderung:

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


Dritte oder nachfolgenden Anforderung in der gleichen runde:

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**Parameter**

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standard-Zeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|user_context|string|Der Benutzerkontext. Sie können den Wert des "me" verwenden, im Kontext des aktuellen Benutzers an. Sie können auch die Benutzer / {Upn} Format des **Upn** ist, auf dem die Benutzerprinzipalnamen zu benennen ist in der Regel die e-Mail-Adresse des Benutzers.|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Datum und Uhrzeit für das Ende des Ereignisses.|
|delta_token|string|Die `deltaToken` Zeichenfolge zurückgegeben wird, als Teil des Werts für @odata.deltaLink in der vorherigen Antwort synchronisieren.|
|skip_token|string|Die `skipToken` Zeichenfolge zurückgegeben wird, als Teil des Werts für @odata.nextLink in der vorherigen Antwort synchronisieren. |

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header nicht angegeben ist, werden die Anfangs- und Endzeiten in UTC zurückgegeben.

**Hinweis** 

- Beim Angeben von "bevorzugen: odata.track Änderungen" in die erste Anforderung, wenn die Antwort Sync, unterstützt die Antwort zählen "Voreinstellung angewendet: odata.track Änderungen" in der Kopfzeile.
- Wenn Sie versuchen, eine Ressource zu synchronisieren, die nicht unterstützt wird oder falls dies nicht der ersten Synchronisierung Anforderung ist, sehen Sie nicht die Kopfzeile "Einstellung angewendet" in der Antwort.
- Sie können das Änderung Zeitfenster verändern, indem die Abfrageparameter Startdatetime und Enddatetime.  
- Jedes Ereignis in der Antwort umfasst alle zugehörigen Eigenschaften. 
- Für eine Besprechungsserie enthält eine Antwort Sync das gesamte-Ereignis für das wiederkehrende Master-Shape und Ausnahmeereignisse. 
- Instanzen von sich wiederholenden Reihe abgekürzt werden und nur die Eigenschaften **Start** und **End** enthalten. Sie können die restliche die Ereignisinformationen Vorkommen aus der master Ereignisserie erfassen. Referenzinformationen finden Sie unter [Ereignis Ressource](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) .
- Sie können nicht die $filter, $count, $select, $skip, $top und $search Abfrageparametern verwenden. 

**Antworttyp**

Erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) und gekürzte Version des Ereignisse innerhalb des angegebenen Zeitraums.

**Beispiel**

Das folgende Beispiel zeigt die erste und zweite Synchronisierungsanfragen Standardkalender für den Benutzer zu synchronisieren. Jeder Anforderung gibt an, dass jeweils nur eine vollständige Ereignis zurück:
- Die erste Antwort ein Ereignis gibt einen `deltaLink` und `deltaToken`. 
- Die zweite Anforderung verwendet, die `deltatoken`. Die zweite Antwort ein Ereignis gibt einen `nextLink` und `skipToken`. 

Um die Synchronisierung abgeschlossen haben, verwenden Sie die `skipToken` aus der vorherigen Sync-Anforderung zurückgegeben werden, bis die Sync-Antwort zurückgegeben wird eine `deltaLink` und `deltaToken`, in diesem Fall dieses Round Synchronisierung abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung. 

Weitere Informationen finden Sie unter [Synchronize Ereignisse in einer Outlook-Kalender anzeigen](..\howto\sync-calendar-view.md).
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**Beispiel für eine anfängliche Anforderung**

```
    GET https://outlook.office.com/api/beta/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
    Prefer: outlook.timezone="Pacific Standard Time"
```

**Erste Antwort-Beispieldaten**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/beta/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": {
                    "DateTime": "2015-04-05T18:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "End": {
                    "DateTime": "2015-04-05T19:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "ReminderMinutesBeforeStart": "15",
                "IsReminderOn": "true",
                "Location": {
                    "DisplayName": "",
                    "Address": null,
                    "Coordinates": null,
                    "LocationEmailAddress": "",
                    "LocationUri": ""
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "OriginalEndTimeZone": "Pacific Standard Time",
                "OriginalStartTimeZone": "Pacific Standard Time",
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
                "OnlineMeetingUrl": null
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/beta/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**Beispiel für eine zweite Anforderung**

```
    GET https://outlook.office.com/api/beta/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
    Prefer: outlook.timezone="Pacific Standard Time"
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**Zweite Antwort-Beispieldaten**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": {
                "DateTime": "2015-04-16T18:00:00",
                "TimeZone": "Pacific Standard Time"
            }
            "End": {
                "DateTime": "2015-04-16T19:00:00",
                "TimeZone": Pacific Standard Time"
            }
            "ReminderMinutesBeforeStart": "15",
            "IsReminderOn": "true",
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                },
                "Coordinates": {
                    "Accuracy": "NaN",
                    "Altitude": "NaN",
                    "AltitudeAccuracy": "NaN",
                    "Latitude": "NaN",
                    "Longitude": "NaN"
                },
                "LocationEmailAddress": "",
                "LocationUri": ""
            },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "OriginalEndTimeZone": "Pacific Standard Time",
            "OriginalStartTimeZone": "Pacific Standard Time",
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
            "OnlineMeetingUrl": null
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/beta/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


**Im Standardkalender synchronisieren**

Anfängliche Anforderung: 

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

Dritte oder nachfolgenden Anforderung in der gleichen runde  

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**In einem bestimmten Kalender synchronisieren**

Anfängliche Anforderung:

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


Dritte oder nachfolgenden Anforderung in der gleichen runde:

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**Parameter**

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|user_context|string|Der Benutzerkontext. Den Wert der "me" können Sie im Kontext des aktuellen Benutzers anzuzeigen. Sie können auch die Benutzer / {Upn}-Format, in dem der **Upn** ist den Benutzerprinzipalnamen, zu benennen ist in der Regel die e-Mail-Adresse des Benutzers.|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Datum und Uhrzeit für das Ende des Ereignisses.|
|delta_token|string|Die `deltaToken` Zeichenfolge zurückgegeben wird, als Teil des Werts für @odata.deltaLink in der vorherigen Antwort synchronisieren.|
|skip_token|string|Das `skipToken` Zeichenfolge zurückgegeben wird, im Rahmen des Werts für @odata.nextLink in der vorherigen Antwort synchronisieren. |

**Hinweis** 

- Beim Angeben von "bevorzugen: odata.track Änderungen" in die erste Anforderung, wenn die Antwort Sync, unterstützt die Antwort zählen "Voreinstellung angewendet: odata.track Änderungen" in der Kopfzeile.
- Wenn Sie versuchen, eine Ressource zu synchronisieren, die nicht unterstützt wird, oder wenn dies nicht der ersten Synchronisierung Anforderung ist, wird die Kopfzeile "Voreinstellung angewendet" in der Antwort nicht angezeigt.
- Sie können das Änderung Zeitfenster verändern, indem die Startdatetime und Enddatetime Abfrageparameter.  
- Jedes Ereignis in der Antwort umfasst alle zugehörigen Eigenschaften. 
- Für eine Besprechungsserie enthält eine Antwort Sync das gesamte-Ereignis für das wiederkehrende Master-Shape und Ausnahmeereignisse. 
- Instanzen von sich wiederholenden Reihe abgekürzt werden und nur die Eigenschaften **Start** und **End** enthalten. Sie können die restliche die Ereignisinformationen Vorkommen aus der master Ereignisserie erfassen. Referenzinformationen finden Sie unter [Ereignis Ressource](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) .
- Sie können nicht die $filter, $count, $select, $skip, $top und $search Abfrageparametern verwenden. 

**Antworttyp**

Erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) und gekürzte Version des Ereignisse innerhalb des angegebenen Zeitraums.

**Beispiel**

Das folgende Beispiel zeigt die erste und zweite Synchronisierungsanfragen Standardkalender für den Benutzer zu synchronisieren. Jeder Anforderung gibt an, dass jeweils nur eine vollständige Ereignis zurück:
- Die erste Antwort ein Ereignis gibt einen `deltaLink` und `deltaToken`. 
- Die zweite Anforderung verwendet, die `deltatoken`. Die zweite Antwort ein Ereignis gibt einen `nextLink` und `skipToken`. 

Um die Synchronisierung abgeschlossen haben, verwenden Sie die `skipToken` aus der vorherigen Sync-Anforderung zurückgegeben werden, bis die Sync-Antwort zurückgegeben wird eine `deltaLink` und `deltaToken`, in diesem Fall dieses Round Synchronisierung abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung. 

Weitere Informationen finden Sie unter [Synchronize Ereignisse in einer Outlook-Kalender anzeigen](..\howto\sync-calendar-view.md).
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**Beispiel für eine anfängliche Anforderung**

```
    GET https://outlook.office.com/api/v2.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

**Erste Antwort-Beispieldaten**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v2.0/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": {
                    "DateTime": "2015-04-05T18:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "End": {
                    "DateTime": "2015-04-05T19:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "ReminderMinutesBeforeStart": "15",
                "IsReminderOn": "true",
                "Location": {
                    "DisplayName": "",
                    "Address": null
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "OriginalEndTimeZone": "Pacific Standard Time",
                "OriginalStartTimeZone": "Pacific Standard Time",
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/v2.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**Beispiel für eine zweite Anforderung**

```
    GET https://outlook.office.com/api/v2.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**Zweite Antwort-Beispieldaten**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": {
                "DateTime": "2015-04-16T18:00:00",
                "TimeZone": "Pacific Standard Time"
            }
            "End": {
                "DateTime": "2015-04-16T19:00:00",
                "TimeZone": Pacific Standard Time"
            }
            "ReminderMinutesBeforeStart": "15",
            "IsReminderOn": "true",
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                }
             },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "OriginalEndTimeZone": "Pacific Standard Time",
            "OriginalStartTimeZone": "Pacific Standard Time",
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/v2.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


**Im Standardkalender synchronisieren**

Anfängliche Anforderung: 

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

Dritte oder nachfolgenden Anforderung in der gleichen runde  

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**In einem bestimmten Kalender synchronisieren**

Anfängliche Anforderung:

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


Zweite Anforderung oder die erste Anforderung einer nachfolgenden Rundung:

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


Dritte oder nachfolgenden Anforderung in der gleichen runde:

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**Parameter**

|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|user_context|string|Der Benutzerkontext. Sie können den Wert des "me" verwenden, im Kontext des aktuellen Benutzers an. Sie können auch die Benutzer / {Upn} Format des **Upn** ist, auf dem die Benutzerprinzipalnamen zu benennen ist in der Regel die e-Mail-Adresse des Benutzers.|
|calendar_id|string|Die Kalender-ID, wenn Sie eine Kalenderansicht aus einem bestimmten Kalender optimal nutzen.|
|start_datetime|DateTimeOffset|Datum und Uhrzeit des Ereignisses gestartet wird.|
|end_datetime|DateTimeOffset|Datum und Uhrzeit für das Ende des Ereignisses.|
|delta_token|string|Die `deltaToken` Zeichenfolge zurückgegeben wird, als Teil des Werts für @odata.deltaLink in der vorherigen Antwort synchronisieren.|
|skip_token|string|Die `skipToken` Zeichenfolge zurückgegeben wird, als Teil des Werts für @odata.nextLink in der vorherigen Antwort synchronisieren. |

**Hinweis** 

- Beim Angeben von "bevorzugen: odata.track Änderungen" in die erste Anforderung, wenn die Antwort Sync, unterstützt die Antwort zählen "Voreinstellung angewendet: odata.track Änderungen" in der Kopfzeile.
- Wenn Sie versuchen, eine Ressource zu synchronisieren, die nicht unterstützt wird oder falls dies nicht der ersten Synchronisierung Anforderung ist, sehen Sie nicht die Kopfzeile "Einstellung angewendet" in der Antwort.
- Sie können das Änderung Zeitfenster verändern, indem die Abfrageparameter Startdatetime und Enddatetime.  
- Jedes Ereignis in der Antwort umfasst alle zugehörigen Eigenschaften. 
- Für eine Besprechungsserie enthält eine Antwort Sync das gesamte-Ereignis für das wiederkehrende Master-Shape und Ausnahmeereignisse. 
- Instanzen von sich wiederholenden Reihe abgekürzt werden und nur die Eigenschaften **Start** und **End** enthalten. Sie können die restliche die Ereignisinformationen Vorkommen aus der master Ereignisserie erfassen. Referenzinformationen finden Sie unter [Ereignis Ressource](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) .
- Sie können nicht die $filter, $count, $select, $skip, $top und $search Abfrageparametern verwenden. 

**Antworttyp**

Erweiterte [Ereignisse](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) und gekürzte Version des Ereignisse innerhalb des angegebenen Zeitraums.

**Beispiel**

Das folgende Beispiel zeigt die erste und zweite Synchronisierungsanfragen Standardkalender für den Benutzer zu synchronisieren. Jeder Anforderung gibt an, dass jeweils nur eine vollständige Ereignis zurück:
- Die erste Antwort ein Ereignis gibt einen `deltaLink` und `deltaToken`. 
- Die zweite Anforderung verwendet, die `deltatoken`. Die zweite Antwort ein Ereignis gibt einen `nextLink` und `skipToken`. 

Um die Synchronisierung abgeschlossen haben, verwenden Sie die `skipToken` aus der vorherigen Sync-Anforderung zurückgegeben werden, bis die Sync-Antwort zurückgegeben wird eine `deltaLink` und `deltaToken`, in diesem Fall dieses Round Synchronisierung abgeschlossen ist. Speichern Sie die `deltaToken` für die nächste Runde von Synchronisierung. 

Weitere Informationen finden Sie unter [Synchronize Ereignisse in einer Outlook-Kalender anzeigen](..\howto\sync-calendar-view.md).
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**Beispiel für eine anfängliche Anforderung**

```
    GET https://outlook.office.com/api/v1.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

**Erste Antwort-Beispieldaten**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": "2015-04-05T18:00:00Z",
                "StartTimeZone": "Pacific Standard Time",
                "End": "2015-04-05T19:00:00Z",
                "EndTimeZone": "Pacific Standard Time",
                "Reminder": 15,
                "Location": {
                    "DisplayName": "",
                    "Address": null
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/v1.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**Beispiel für eine zweite Anforderung**

```
    GET https://outlook.office.com/api/v1.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**Zweite Antwort-Beispieldaten**

```
{
    "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-04-16T18:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2015-04-16T19:00:00Z",
            "EndTimeZone": "Pacific Standard Time",
            "Reminder": 15,
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                }
            },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/v1.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="FindMeetingTimesPreview"></a>
## <a name="find-meeting-times-preview"></a>Suchen Sie nach Besprechungszeiten (Preview)

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Hier finden Sie Besprechungstermin basierend auf Organisator und Teilnehmer Verfügbarkeit und Uhrzeit oder Speicherort Integritätsregeln als Parameter festgelegt. 

Dieser Vorgang ist derzeit in der Vorschau und in der Beta-Version verfügbar. Es gilt für nur Office 365-Postfächer (für Azure AD) und nicht für Microsoft-Konten.

```no-highlight
POST https://outlook.office.com/api/{version}/me/findmeetingtimes
```

Alle unterstützten Parameter sind unten aufgeführt. Je nach Szenario geben Sie die erforderlichen Parameter im Anforderungstext der **FindMeetingTimes** Aktion aus. 

|**Parameter**|**Typ**|**Beschreibung**|**Erforderlich?**|
|:-----|:-----|:-----|:-----|
| Teilnehmer | Auflistung ([AttendeeBase](complex-types-for-mail-contacts-calendar.md#AttendeeBase)) | Teilnehmer oder Ressourcen für die Besprechung. Eine leere Auflistung bewirkt, dass **FindMeetingTimes** kostenlos Zeitfenster nur den Organisator gesucht. | Optional |
| LocationConstraint | [LocationConstraint](complex-types-for-mail-contacts-calendar.md#LocationConstraint) | Der Organisator Anforderungen über den Speicherort für die Besprechung, z. B., ob Vorschläge für einen Besprechungsort ist erforderlich, oder es sind bestimmte Orte nur, in dem die Besprechung stattfinden kann. | Optional |
| TimeConstraint | [TimeConstraint](complex-types-for-mail-contacts-calendar.md#TimeConstraint) | Die Start- und Endzeit Zeitbereich in dem die Besprechung durchgeführt werden soll. | Optional |
| MeetingDuration | Edm.Duration |Die Länge der Besprechung, der im ISO 8601-Format für die Dauer, beispielsweise `PT1H` 1 Stunde darstellt. Wenn keine Besprechungsdauer angegeben wird, verwendet **FindMeetingTimes** die Standardeinstellung von 30 Minuten. | Optional |
| MaxCandidates | Edm.Int32 |Die maximale Anzahl der Besprechungsvorschläge in der Antwort zurückgegeben. | Optional |
| IsOrganizerOptional | Edm.Boolean | Geben Sie `true` , wenn der Organisator notwendigerweise nicht für die Teilnahme an. Der Standardwert ist `false`. | Optional |
| ReturnSuggestionHints | Edm.Boolean | Geben Sie `true` einen Grund für jeden besprechungsvorschlag in der **SuggestionHint** -Eigenschaft zurückgegeben. Der Standardwert ist `false` diese Eigenschaft nicht zurückgegeben. | Optional |

Basierend auf den angegebenen Parametern, überprüft **FindMeetingTimes** den Frei/Gebucht-Status, in dem primären Kalender der Organisator und Teilnehmer. Die Aktion berechnet die bestmögliche Besprechungszeiten und Besprechungsvorschläge zurück.

**Antworttyp**

Ein [MeetingTimeCandidatesResult](complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidatesResult) umfasst eine Auflistung von Besprechungsvorschläge, jede geben [MeetingTimeCandidate](#MeetingTimeCandidate)und eine **EmptySuggestionsHint** -Eigenschaft.

<!-- Location suggestions are based on the organizer's booking history during the past 7 days and next 2 days. If the organizer doesn't have sufficient booking history 
in the corresponding time window, the request returns HTTP 200 OK, but does not include any meeting suggestions in the response. -->

Jede Vorschlag ist definiert als eine [MeetingTimeCandidate](complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidate)mit Teilnehmern auf [den Mittelwert einer Confidence Level Chance 50 % oder mehr für die Teilnahme an](complex-types-for-mail-contacts-calendar.md#ConfidenceScoreDetails). Standardmäßig wird jedes Mal Besprechung Vorschlag in UTC zurückgegeben. Anwenden der `Prefer: outlook.timezone` Anforderungsheader Besprechungstermin zurückgegebene in einer anderen Zeitzone, zum Beispiel haben:

```no-highlight
Prefer: outlook.timezone="Pacific Standard Time"
```

Wenn **FindMeetingTimes** Besprechungsvorschläge zurückgeben kann, würde die Antwort einen Grund in der **EmptySuggestionsHint** -Eigenschaft angeben. Anhand dieses Werts, können Sie besser passen Sie die Parameter und erneut **FindMeetingTimes** aufrufen.


**Hinweis**

Derzeit **FindMeetingTimes** wird Folgendes vorausgesetzt:

- Alle [Teilnehmer](..\api\complex-types-for-mail-contacts-calendar.md#Attendee) , eine Person (im Gegensatz zu einer Ressource ist) ist ein Erforderlicher Teilnehmer. Geben Sie also `Required` einer Person und `Resource` für eine Ressource in der entsprechenden **Type** -Eigenschaft als Teil des Parameters-Auflistung **Teilnehmer** .
- Alle besprechungsvorschlag tritt auf, während nur den Arbeitsstunden der Organisator oder einem Teilnehmer. Sie können die Angabe der **ActivityDomain** -Eigenschaft des ein [TimeConstraint](..\api\complex-types-for-mail-contacts-calendar.md#TimeConstraint)ignorieren. 

Jedes Beispiel unten **FindMeetingTimes**aufruft und variiert je nach Attendee Verfügbarkeit, Uhrzeit und Ort Einschränkungen wie unten beschrieben:

- [Hier finden Sie Zeit und Standort mit den Teilnehmern (REST) erfüllen](#FindTimeToMeet) 
- [Suchen Sie in einem bekannten Speicherort Besprechungstermine, und erhalten Sie einen Grund für jeden einzelnen Vorschlag (REST)](#FindTimeToMeetAtKnownLocation) 
- [Find Zeit zum erfüllen, aber keine Attendee ist verfügbar (REST)](#FindTimeToMeetButNobodyAvailable) 
- [Suchen Sie nach Uhrzeit zu erfüllen, aber nur einige Teilnehmer verfügbar (REST)](#FindTimeToMeetSomeAvailable)
- [Hier finden Sie kostenlose Zeitfenster für die angemeldeten Benutzers (REST)](#FindFreeSlots)


<a name="FindTimeToMeet"></a>

### <a name="find-time-and-location-to-meet-with-specific-attendees-rest"></a>Hier finden Sie Zeit und Standort mit bestimmten Teilnehmern (REST) erfüllen

Wie oft suchen und Speicherorte erfüllen, indem Sie die folgenden Parameter im Anforderungstext angeben:
- **Teilnehmer**
- **TimeConstraint**
- **MeetingDuration**

**Beispiel für eine Anforderung**

Im folgenden Beispiel wird schlägt Besprechungszeiten und Speicherorte Berücksichtigung der Organisator vor und Verfügbarkeit während der Besprechung angeforderten Bereich und die angeforderte Zeitdauer Zeit.

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "TimeConstraint": { 
    "Timeslots": [ 
       { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H" 
} 
```



**Beispielantwort**

Statuscode: 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "11:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
               {
                    "DisplayName": "Tokyo conference room",
                    "LocationEmailAddress": "",
                    "LocationUri": "",
                    "Address": null,
                    "Coordinates": null
                }
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "11:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
               {
                    "DisplayName": "Paris conference room",
                    "LocationEmailAddress": "",
                    "LocationUri": "",
                    "Address": null,
                    "Coordinates": null
                }
            ]
        }
    ],
    "EmptySuggestionsHint": ""
}
```


****

<a name="FindTimeToMeetAtKnownLocation"></a>

### <a name="find-time-to-meet-at-a-known-location-and-get-a-reason-for-each-suggestion-rest"></a>Suchen Sie in einem bekannten Speicherort Besprechungstermine, und erhalten Sie einen Grund für jeden einzelnen Vorschlag (REST)

Suchen Sie Zeit zum erfüllen an einem vordefinierten Speicherort, und fordern Sie einen Grund für jeden einzelnen Vorschlag durch die folgenden Parameter im Anforderungstext angeben:
- **Teilnehmer**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**
- **ReturnSuggestionHints**

Durch Festlegen des **ReturnSuggestionHints** -Parameters, erhalten Sie auch eine Erläuterung für jeden einzelnen Vorschlag in der **SuggestionHint** -Eigenschaft, wenn **FindMeetingTimes** Vorschläge zurückgibt.


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT2H",
  "ReturnSuggestionHints": "true"
} 
```



**Beispielantwort**

Statuscode: 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
                {
                    "DisplayName": "Conf room Hood"
                }
            ],
            "SuggestionHint": "Suggested because it is one of the nearest times when all attendees are available."
        }
    ],
    "EmptySuggestionsHint": ""
}
```


****

<a name="FindTimeToMeetButNobodyAvailable"></a>

### <a name="find-time-to-meet-but-no-attendee-is-available-rest"></a>Find Zeit zum erfüllen, aber keine Attendee ist verfügbar (REST)

Suchen Sie die Zeit an einem vordefinierten Speicherort, zu erfüllen, indem Sie die folgenden Parameter im Textkörper Anforderung angeben:
- **Teilnehmer**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**

In diesem Beispiel wird anhand der angegebenen Parameter und der Verfügbarkeit von Teilnehmern, **FindMeetingTimes** Vorschläge können nicht zurückzugeben und gibt einen Grund stattdessen `AttendeesUnavailable` in der **EmptySuggestionsHint** -Eigenschaft. 

Finden Sie unter andere [Mögliche Gründe für Besprechungsvorschläge nicht zurückgeben](..\api\complex-types-for-mail-contacts-calendar.md#ReasonsNoMeetingSuggestion).


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "14:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT2H" 
}
```



**Beispielantwort**

Statuscode: 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
    ],
    "EmptySuggestionsHint": "AttendeesUnavailable"
}
```

****

<a name="FindTimeToMeetSomeAvailable"></a>
### <a name="find-time-to-meet-but-only-some-attendees-are-available-rest"></a>Find Uhrzeit erfüllen, aber nur einige Teilnehmer sind verfügbar (REST)

Suchen Sie die Zeit an einem vordefinierten Speicherort, zu erfüllen, indem Sie die folgenden Parameter im Textkörper Anforderung angeben:
- **Teilnehmer**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**
- **ReturnSuggestionHints**

In diesem Beispiel ist nur einen der Teilnehmer 2 verfügbar. Jeden besprechungsvorschlag, der **FindMeetingTimes** zurückgibt umfasst:
- Die Verfügbarkeit der einzelnen Teilnehmer
- Eine berechnete Besprechung Confidence 50 %
- Ein **SuggestionHInt**, da der Parameter **ReturnSuggestionHints** festgelegt ist. 

Hier finden Sie weitere Informationen zu den [Confidence einer Besprechung](..\api\complex-types-for-mail-contacts-calendar.md#ConfidenceScoreDetails).


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    },
   { 
      "Type": "Optional",  
      "EmailAddress": { 
        "Address": "danas@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "9:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H",
  "ReturnSuggestionHints": "true"
}
```



**Beispielantwort**

Statuscode: 200
```
{
   "@odata.context":"https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
   "MeetingTimeSlots":[
      {
         "MeetingTimeSlot":{
            "Start":{
               "Date":"2016-05-20",
               "Time":"10:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            },
            "End":{
               "Date":"2016-05-20",
               "Time":"11:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            }
         },
         "Confidence":50.0,
         "OrganizerAvailability":"Free",
         "AttendeeAvailability":[
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"fannyd@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Free"
            },
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"danas@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Busy"
            }
         ],
         "Locations":[
            {
               "DisplayName":"Conf room Hood"
            }
         ],
         "SuggestionHint":"Suggested because it is one of the nearest times when most attendees are available."
      },
      {
         "MeetingTimeSlot":{
            "Start":{
               "Date":"2016-05-20",
               "Time":"11:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            },
            "End":{
               "Date":"2016-05-20",
               "Time":"12:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            }
         },
         "Confidence":50.0,
         "OrganizerAvailability":"Free",
         "AttendeeAvailability":[
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"fannyd@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Free"
            },
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"danas@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Busy"
            }
         ],
         "Locations":[
            {
               "DisplayName":"Conf room Hood"
            }
         ],
         "SuggestionHint":"Suggested because it is one of the nearest times when most attendees are available."
      }
   ],
   "EmptySuggestionsHint":""
}
```

****

<a name="FindFreeSlots"></a>
###<a name="find-free-time-slots-for-just-the-signed-in-user-rest"></a>Hier finden Sie kostenlose Zeitfenster für nur für den angemeldeten Benutzer (REST)

Finden Sie kostenlose Zeitfenster im primären Kalender des angemeldeten Benutzers, innerhalb eines Datumsbereichs, durch die folgenden Parameter im Anforderungstext angeben:

- **TimeConstraint**
- **MeetingDuration**

**Beispiel für eine Anforderung**

In diesem Beispiel wird sucht nach 1 Stunde Freizeit Steckplätze, gemäß **MeetingDuration**, des angemeldeten Benutzers primären Kalender innerhalb des Zeitraums, der durch **TimeConstraint**angegeben.

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [],
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H"
}
```



**Beispielantwort**

Statuscode: 200
```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "08:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "09:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "09:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "13:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        }
    ],
    "EmptySuggestionsHint": ""
}
```

****


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**. 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**. 

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="CreateEvents"> </a>
## <a name="create-events"></a>Erstellen von Ereignissen

REST-API: [Erstellen einer Kalenderereignis](#CreateAnEvent)

Client-Bibliotheken: [Erstellen einer Kalenderereignis (Client)](#CreateEventsClient)

<a name="CreateAnEvent"></a>
###<a name="create-a-calendar-event-rest"></a>Erstellen Sie ein Kalenderereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Erstellen Sie ein Ereignis in der primären Kalender des Benutzers oder einen bestimmten Kalender durch die Veröffentlichung auf des Kalenders `events` Endpunkt. Wenn das Ereignis erstellt wird, sendet der Server Einladungen an alle Teilnehmer.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events
POST https://outlook.office.com/api/beta/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/events
Content-Type: application/json
```

```
{
  "Subject": "Discuss the Calendar REST API",
  "Body": {
    "ContentType": "HTML",
    "Content": "I think it will meet our requirements!"
  },
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Type": "Required"
    }
  ]
}
```

**Beispielantwort**

Statuscode: 201

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE4v1RAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
  "Id": "AAMkAGE4v1RAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:56:10.1058291Z",
  "LastModifiedDateTime": "2014-01-22T20:56:10.3402186Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Status": {
        "Response": "None",
        "Time": "0001-01-01T00:00:00Z"
      },
      "Type": "Required"
    }
  ],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  },
  "OnlineMeetingUrl": null
}
```


**Antworttyp**

Das neue [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

Die Antwort enthält standardmäßig alle Eigenschaften des neuen Ereignisses an. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Es folgt ein Beispiel, um nur die Eigenschaften **Start** und **Ende** des neuen Ereignisses in der Antwort enthalten.

```
POST https://outlook.office.com/api/beta/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/events
POST https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/events
Content-Type: application/json
```

```
{
  "Subject": "Discuss the Calendar REST API",
  "Body": {
    "ContentType": "HTML",
    "Content": "I think it will meet our requirements!"
  },
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Type": "Required"
    }
  ]
}
```

**Beispielantwort**

Statuscode: 201

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE4v1RAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
  "Id": "AAMkAGE4v1RAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:56:10.1058291Z",
  "LastModifiedDateTime": "2014-01-22T20:56:10.3402186Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "",
    "Address": null
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Status": {
        "Response": "None",
        "Time": "0001-01-01T00:00:00Z"
      },
      "Type": "Required"
    }
  ],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  }
}
```


**Antworttyp**

Das new- [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

Die Antwort enthält standardmäßig alle Eigenschaften des neuen Ereignisses an. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Es folgt ein Beispiel, um nur die Eigenschaften **Start** und **Ende** des neuen Ereignisses in der Antwort enthalten.

```
POST https://outlook.office.com/api/v2.0/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


Standardmäßig sind die Werte für **Start** und **End** Zeit in UTC. Sie können Zeitzonen für **Start** und **End**, express die Zeit angeben, in der entsprechenden Zeitzone, und schließen einen Uhrzeit-Offset von UTC. Das folgende Beispiel veranschaulicht die Zeitwerte in der Pacific Standard Time zuzuweisen. Beachten Sie bei der Angabe einer Zeitzone Sie einen Wert für die anderen eine sowie angeben müssen.


```no-highlight
POST https://outlook.office.com/api/v1.0/me/events
POST https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/events
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|

```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 529
    },
    "parameterDetails": [],
    "requestBody": {
        "Subject": "Discuss the Calendar REST API",
        "Body": {
            "ContentType": "HTML",
            "Content": "I think it will meet our requirements!"
        },
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Type": "Required"
            }
        ]
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1RAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1RAAA=",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
        "Categories": [],
        "DateTimeCreated": "2014-01-22T20:56:10.1058291Z",
        "DateTimeLastModified": "2014-01-22T20:56:10.3402186Z",
        "Subject": "Discuss the Calendar REST API",
        "BodyPreview": "I think it will meet our requirements!",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Location": {
            "DisplayName": ""
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SingleInstance",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": null,
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "alexd"
            }
        }
    }
}
```


**Antworttyp**

Das new- [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

Die Antwort enthält standardmäßig alle Eigenschaften des neuen Ereignisses an. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. Es folgt ein Beispiel, um nur die Eigenschaften **Start** und **Ende** des neuen Ereignisses in der Antwort enthalten.

```
POST https://outlook.office.com/api/v1.0/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="CreateEventsClient"></a>
### <a name="create-a-calendar-event-client"></a>Erstellen Sie ein Kalenderereignis (Client)

Erstellen eines Ereignisses. Wenn Sie einen anderen Kalender ein Ereignis hinzufügen, verwenden Sie die **Ereignisse** -Eigenschaft der Ziel-Kalender.

Beispiel:`await client.Me.Calendars["AQMkADE3..."].Events.AddEventAsync(newEvent);`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- CHUCK, feel free to provide client library example that reflects the event breaking changes for beta.  --> 

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Create a location for the event
Location location = new Location 
{ 
    DisplayName = "Water cooler" 
}; 

// Create a description for the event   
ItemBody body = new ItemBody 
{ 
    Content = "Status updates, blocking issues, and next steps", 
    ContentType = BodyType.Text 
}; 
    
// Create an attendee for the event 
Attendee[] attendees =  
{  
    new Attendee  
    {  
        Type = AttendeeType.Required,  
        EmailAddress = new EmailAddress  
        {  
            Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"  
        },  
    },  
}; 
    
// Create the event object
Event newEvent = new Event 
{ 
    Subject = "Sync up", 
    Location = location, 
    Attendees = attendees, 
    Start = new DateTimeTimeZone()
    {
        TimeZone = TimeZoneInfo.Local.Id,
        DateTime = new DateTime(2015, 12, 1, 9, 30, 0).ToString("s")
    },
    End = new DateTimeTimeZone()
    {
        TimeZone = TimeZoneInfo.Local.Id,
        DateTime = new DateTime(2015, 12, 1, 10, 30, 0).ToString("s")
    },    
    Body = body 
};
    
// Add the event to the default calendar
await client.Me.Events.AddEventAsync(newEvent);

// Get the event ID.
string eventId = newEvent.Id;
```
```javascript
        var event = new Microsoft.OutlookServices.Event();
        event.subject = 'Your Subject';
        event.start = new Date("October 30, 2014 11:13:00").toISOString();
        event.end = new Date("October 30, 2014 12:13:00").toISOString();

        // Body
        event.body = new Microsoft.OutlookServices.ItemBody();
        event.body.content = 'Body Content';
        event.body.contentType = Microsoft.OutlookServices.BodyType.Text;

        // Location
        event.location = new Microsoft.OutlookServices.Location();
        event.location.displayName = 'Location';

        // Attendee
        var attendee1 = new Microsoft.OutlookServices.Attendee();
        var emailAddress1 = new Microsoft.OutlookServices.EmailAddress();
        emailAddress1.name = "Katie Jordan";
        emailAddress1.address = "katiej@a830edad9050849NDA1.onmicrosoft.com";

        attendee1.emailAddress = emailAddress1;

        event.attendees.push(attendee1);
        
        outlookClient.me.calendar.events.addEvent(event)
        .then(function (response) {
            console.log(response._Id);
        });    

```
<!-- ENDSECTION -->


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Create a location for the event
Location location = new Location 
{ 
    DisplayName = "Water cooler" 
}; 

// Create a description for the event   
ItemBody body = new ItemBody 
{ 
    Content = "Status updates, blocking issues, and next steps", 
    ContentType = BodyType.Text 
}; 
    
// Create an attendee for the event 
Attendee[] attendees =  
{  
    new Attendee  
    {  
        Type = AttendeeType.Required,  
        EmailAddress = new EmailAddress  
        {  
            Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"  
        },  
    },  
}; 
    
// Create the event object
Event newEvent = new Event 
{ 
    Subject = "Sync up", 
    Location = location, 
    Attendees = attendees, 
    Start = new DateTimeOffset(new DateTime(2014, 12, 1, 9, 30, 0)), 
    End = new DateTimeOffset(new DateTime(2014, 12, 1, 10, 0, 0)), 
    Body = body 
}; 
    
// Add the event to the default calendar
await client.Me.Events.AddEventAsync(newEvent);

// Get the event ID.
string eventId = newEvent.Id;
```
```javascript
        var event = new Microsoft.OutlookServices.Event();
        event.subject = 'Your Subject';
        event.start = new Date("October 30, 2014 11:13:00").toISOString();
        event.end = new Date("October 30, 2014 12:13:00").toISOString();

        // Body
        event.body = new Microsoft.OutlookServices.ItemBody();
        event.body.content = 'Body Content';
        event.body.contentType = Microsoft.OutlookServices.BodyType.Text;

        // Location
        event.location = new Microsoft.OutlookServices.Location();
        event.location.displayName = 'Location';

        // Attendee
        var attendee1 = new Microsoft.OutlookServices.Attendee();
        var emailAddress1 = new Microsoft.OutlookServices.EmailAddress();
        emailAddress1.name = "Katie Jordan";
        emailAddress1.address = "katiej@a830edad9050849NDA1.onmicrosoft.com";

        attendee1.emailAddress = emailAddress1;

        event.attendees.push(attendee1);
        
        outlookClient.me.calendar.events.addEvent(event)
        .then(function (response) {
            console.log(response._Id);
        });    

```
<!-- ENDSECTION -->

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->






****


<a name="UpdateEvents"> </a>
## <a name="update-events"></a>Update-Ereignisse

REST-API: [Update ein Ereignis im Kalender](#UpdateAnEvent)

Client-Bibliotheken: [Aktualisieren einer Kalenderereignis (Client)](#UpdateEventsClient)

<a name="UpdateAnEvent"></a>
###<a name="update-a-calendar-event-rest"></a>Aktualisieren einer Kalenderereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Ändern eines Ereignisses an. Nur die Eigenschaften, die Sie angeben, werden geändert. Wenn der Benutzer der Organisator befindet, sendet der Server besprechungsaktualisierungen an alle Teilnehmer.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/beta/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

Geben Sie alle schreibbaren [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) Eigenschaften im Textkörper Anforderung.

```
PATCH https://outlook.office.com/api/beta/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```

**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=
Content-Type: application/json

{
  "Location": {
    "DisplayName": "Your office",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  }
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE0M4v1OAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
  "Id": "AAMkAGE0M4v1OAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:49:05.5657528Z",
  "LastModifiedDateTime": "2014-01-22T21:14:17.4886416Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "Your office",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  },
  "OnlineMeetingUrl": null
}
```

**Antworttyp**

Das updated- [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource). Wenn der Benutzer der Organisator befindet, sendet der Server besprechungsaktualisierungen an alle Teilnehmer.

Die Antwort enthält standardmäßig alle Eigenschaften des updated-Ereignis. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. 




[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Die Ereignis-ID|

Geben Sie alle schreibbaren [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) Eigenschaften im Textkörper Anforderung.

**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/v2.0/me/events/AAMkAGE0M4v1OAAA=
Content-Type: application/json

{
  "Location": {
    "DisplayName": "Your office",
    "Address": null
  }
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE0M4v1OAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
  "Id": "AAMkAGE0M4v1OAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:49:05.5657528Z",
  "LastModifiedDateTime": "2014-01-22T21:14:17.4886416Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "Your office",
    "Address": null
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  }
}
```

**Antworttyp**

Das updated- [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource). Wenn der Benutzer der Organisator befindet, sendet der Server besprechungsaktualisierungen an alle Teilnehmer.

Die Antwort enthält standardmäßig alle Eigenschaften des updated-Ereignis. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. 

```
PATCH https://outlook.office.com/api/v2.0/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```




[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Die Ereignis-ID|

Geben Sie alle schreibbaren [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) Eigenschaften im Textkörper Anforderung.

```REST
{
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 62
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        }
    ],
    "requestBody": {
        "Location": {
            "DisplayName": "Your office"
        }
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
        "Categories": [],
        "DateTimeCreated": "2014-01-22T20:49:05.5657528Z",
        "DateTimeLastModified": "2014-01-22T21:14:17.4886416Z",
        "Subject": "Discuss the Calendar REST API",
        "BodyPreview": "I think it will meet our requirements!",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Location": {
            "DisplayName": "Your office"
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SingleInstance",
        "SeriesMasterId": null,
        "Attendees": [],
        "Recurrence": null,
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "alexd"
            }
        }
    }
}
```

**Antworttyp**

Das updated- [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource). Wenn der Benutzer der Organisator befindet, sendet der Server besprechungsaktualisierungen an alle Teilnehmer.

Die Antwort enthält standardmäßig alle Eigenschaften des updated-Ereignis. Verwenden Sie **$select** , um nur die Eigenschaften angeben, die Sie für eine optimale Leistung benötigen. Die **Id** -Eigenschaft wird immer zurückgegeben. 

```
PATCH https://outlook.office.com/api/v1.0/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->






****

<a name="UpdateEventsClient"></a>
### <a name="update-a-calendar-event-client"></a>Aktualisieren einer Kalenderereignis (Client)

Ändern eines Ereignisses an.

Sie können mehrere Updates mithilfe der clientseitigen definieren und senden die Anforderungen alle gleichzeitig (diese batch) mit dem folgenden Muster:
1. Rufen Sie `UpdateAsync(true)` für jede Entität, die Sie aktualisieren möchten. Angeben von `true` registriert die Updates lokal auf dem Client, jedoch nicht auf dem Server bereitstellen.
2. Rufen Sie `client.Context.SaveChangesAsync()` lokal für die Bereitstellung aller Updates, die registriert sind.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

<!-- CHUCK, feel free to provide client library example that reflects the event breaking changes for beta.  --> 

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Ereignis-ID haben](#GetEvents).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToUpdate = await client.Me.Events[eventId].ExecuteAsync();

// Add attendees
eventToUpdate.Attendees.Add(new Attendee
{
    Type = AttendeeType.Required,
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com",
    },
});

// Make other changes
eventToUpdate.Start = new DateTimeOffset(new DateTime(2014, 12, 1, 14, 30, 0));
eventToUpdate.End = new DateTimeOffset(new DateTime(2014, 12, 1, 15, 0, 0));
eventToUpdate.Subject = "New event name";
    
// Commit all changes to the event
await eventToUpdate.UpdateAsync();

// Get an updated property.
string newEventName = eventToUpdate.Subject;
```

<!-- ENDSECTION -->


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Ereignis-ID haben](#GetEvents).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToUpdate = await client.Me.Events[eventId].ExecuteAsync();

// Add attendees
eventToUpdate.Attendees.Add(new Attendee
{
    Type = AttendeeType.Required,
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com",
    },
});

// Make other changes
eventToUpdate.Start = new DateTimeOffset(new DateTime(2014, 12, 1, 14, 30, 0));
eventToUpdate.End = new DateTimeOffset(new DateTime(2014, 12, 1, 15, 0, 0));
eventToUpdate.Subject = "New event name";
    
// Commit all changes to the event
await eventToUpdate.UpdateAsync();

// Get an updated property.
string newEventName = eventToUpdate.Subject;
```

<!-- ENDSECTION -->

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->








****

<a name="RespndToEvents"></a>
## <a name="respond-to-events"></a>Reagieren auf Ereignisse

REST-API: [Accept-Ereignis (REST)](#AcceptEvent) | [mit Vorbehalt annehmen Ereignis (REST)](#TentAcceptEvent) | [Ablehnen-Ereignis (REST)](#DeclineEvent)

<a name="AcceptEvent"></a>
###<a name="accept-event-rest"></a>Ereignis (REST) akzeptieren

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Akzeptieren Sie das angegebene Ereignis.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/accept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Die Ereignis-ID Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/accept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/accept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->





****

<a name="TentAcceptEvent"></a>
###<a name="tentatively-accept-event-rest"></a>Mit Vorbehalt annehmen Sie Ereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Das angegebene Ereignis mit Vorbehalt annehmen.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/tentativelyaccept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/tentativelyaccept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/tentativelyaccept
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="DeclineEvent"></a>
###<a name="decline-event-rest"></a>Ablehnen-Ereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Auf das angegebene Ereignis Einladung ablehnen.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/decline
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/decline
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/decline
```


|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID. Erforderlich.|
|_Textkörper-Parameter_|
|Kommentar|string|Der Text in der Antwort enthalten. Optional|
|SendResponse|boolean| `true`Wenn eine Antwort an den Organisator gesendet werden soll; andernfalls `false`. Optional Der Standardwert lautet `true`.|
 
**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**Antwort**

Eine erfolgreiche Antwort wird durch ein HTTP 202 akzeptiert Antwortcode angezeigt.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="DeleteEvents"> </a>
## <a name="delete-events"></a>Delete-Ereignisse

REST-API: [Löschen Sie ein Kalenderereignis (REST)](#DeleteAnEvent)

Client-Bibliotheken: [Löschen Sie ein Kalenderereignis (Client)](#DeleteEventsClient)

<a name="DeleteAnEvent"></a>
###<a name="delete-a-calendar-event-rest"></a>Löschen Sie ein Kalenderereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Verschieben Sie ein Ereignis in den Ordner Gelöschte Elemente des angemeldeten Benutzers. Wenn das Ereignis gehört zu einer Besprechung, und der Benutzer angemeldet der Organisator ist, sendet der Server absagen an alle Teilnehmer.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

Diese Aktion unterscheidet sich von [Abbrechen](#CancelEvents) , **Löschen** der Organisator und Teilnehmer der Besprechung verfügbar sind. Wenn der angemeldet-Benutzer der Organisator der Besprechung ist, wird der Benutzer einfach die Besprechung ohne eine benutzerdefinierte Absage an die Teilnehmer abgebrochen.

```no-highlight
DELETE https://outlook.office.com/api/beta/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=
```

**Beispielantwort**

Statuscode: 204


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/events/AAMkAGE0M4v1OAAA=
```

**Beispielantwort**

Statuscode: 204



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/events/{event_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [ 
                {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        }
    ],
    
    "statusCode": 204
    
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="DeleteEventsClient"></a>
### <a name="delete-a-calendar-event-client"></a>Löschen Sie ein Kalenderereignis (Client)

Ein Ereignis in den Ordner Gelöschte Elemente zu verschieben.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [die Ereignis-ID haben](#GetEvents).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToDelete = await client.Me.Events[eventId].ExecuteAsync();

//Delete the event
await eventToDelete.DeleteAsync();
```

<!-- ENDSECTION -->

****

<a name="CancelEvents"> </a>
## <a name="cancel-events-preview"></a>Abbrechen-Ereignisse (Preview)

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Dieser Aktion kann den Organisator einer Besprechung senden eine Absage und das Ereignis abzubrechen. 

Die Aktion wird das Ereignis in den Ordner Gelöschte Objekte verschoben. Der Organisator kann auch ein Vorkommen einer Besprechungsserie abzubrechen, durch die Bereitstellung der Vorkommen-Ereignis-ID Diese Aktion aufrufen Teilnehmerin Ruft einen Fehler (HTTP 400 Ungültige Anforderung), wobei die folgende Fehlermeldung angezeigt:

"Die Anforderung konnte nicht abgeschlossen werden. Sie müssen ein Organisator eine Besprechung abgebrochen werden."

Diese Aktion unterscheidet sich von [Löschen](#DeleteEvents) , insofern, als **Abbrechen** steht nur der Organisator den Organisator eine benutzerdefinierte Meldung an die Teilnehmer über den Abbruch senden können.

```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/Cancel
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|_Textkörper-Parameter_|
|Kommentar|string|Einen Kommentar zu den Abbruch an alle Teilnehmer gesendet.|

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=/Cancel

Content-Type: application/json
{
  "Comment": "Cancelling this meeting as there is a time conflict for most folks."
}
```

**Beispielantwort**

Statuscode: 202 akzeptierte


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**. 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**. 

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetAttachments"> </a>
## <a name="get-attachments"></a>Abrufen von Anlagen

Sie können eine Anlage-Auflistung abzurufen oder Anlage erhalten möchten.

REST-API: [Abrufen eine Anlage-Auflistung (REST)](#GetAttachmentCollection) | [Abrufen eine Anlage (REST)](#GetAttachment)

<a name="GetAttachmentCollection"> </a>
###<a name="get-an-attachment-collection-rest"></a>Rufen Sie eine Anlage-Auflistung (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Abrufen der Anlagen von einem bestimmten Ereignis.

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|


**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [ReferenceAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)sein kann.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2NGTG9yAAA=/attachments
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events('AAMkAGI2NG9yAAA%3D')/Attachments",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2NGTG9yAAA=')/Attachments('AAMkAGI2NGLwydGuOzcHf1FBlo=')",
            "Id": "AAMkAGI2NGLwydGuOzcHf1FBlo=",
            "LastModifiedDateTime": "2014-10-22T00:30:26Z",
            "Name": "Company Party.docx",
            "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
            "Size": 11647,
            "IsInline": false,
            "ContentId": null,
            "ContentLocation": null,
            "ContentBytes": "UEsDBBQABgAIAAAAIQDfpNJs...AAF4pAAAAAA=="
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|


**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)sein kann.


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2NGTG9yAAA=/attachments
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events('AAMkAGI2NG9yAAA%3D')/Attachments",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2NGTG9yAAA=')/Attachments('AAMkAGI2NGLwydGuOzcHf1FBlo=')",
            "Id": "AAMkAGI2NGLwydGuOzcHf1FBlo=",
            "LastModifiedDateTime": "2014-10-22T00:30:26Z",
            "Name": "Company Party.docx",
            "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
            "Size": 11647,
            "IsInline": false,
            "ContentId": null,
            "ContentLocation": null,
            "ContentBytes": "UEsDBBQABgAIAAAAIQDfpNJs...AAF4pAAAAAA=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|


**Antworttyp**

Eine Anlage-Auflistung, der vom Typ [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)sein kann.


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=/attachments",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****


<a name="GetAttachment"> </a>
###<a name="get-an-attachment-rest"></a>Abrufen einer Anlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Rufen Sie eine Anlage aus einem bestimmten Ereignis.

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/attachments/{attachment_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Die gewünschte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [Referenz Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource).


**Beispiel für eine Anforderung**

Im folgenden Beispiel wird die Datei mit einem bestimmten Ereignis zugeordnet ist.

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2WRAAADTG9yAAA=/attachments/AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events('AAMkAGI2WRAAADTG9yAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2WRAAADTG9yAAA=')/Attachments('AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=')",
    "Id": "AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "LastModifiedDateTime": "2014-10-22T00:30:26Z",
    "Name": "Company Party.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11647,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQD...AAF4pAAAAAA=="
}
```

**Beispiel für eine Anforderung (Referenz Attachment)**

Das folgende Beispiel ruft die Anlage Verweis eines Ereignisses ab.

```
GET https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')/attachments('AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=')
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
    "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
    "lastModifiedDateTime": "2016-03-22T22:27:20Z",
    "name": "Hydrangea picture",
    "contentType": null,
    "size": 412,
    "isInline": false,
    "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
    "providerType": "oneDriveBusiness",
    "thumbnailUrl": null,
    "previewUrl": null,
    "permission": "edit",
    "isFolder": false
}

```


**Beispiel für eine Anforderung ($Erweitern auf Anlagen)**

Das folgende Beispiel dient zum Abrufen und den 2 Verweis Anlagen Inline mit Ereigniseigenschaften erweitert.

```
GET https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')?$expand=attachments
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events/$entity",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAA4KZrtA==\"",
    "id": "AAMkAGE1Mbs88AADggYEcAAA=",
    "createdDateTime": "2016-03-22T22:19:58.1359352Z",
    "lastModifiedDateTime": "2016-03-22T22:39:09.9335289Z",
    "changeKey": "mODEKWhc/Um6lA3uPm7PPAAA4KZrtA==",
    "categories": [
    ],
    "originalStartTimeZone": "Pacific Standard Time",
    "originalEndTimeZone": "Pacific Standard Time",
    "responseStatus": {
        "response": "organizer",
        "time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "040000008200E00074C5B7101A82E008000000005895FCF78884D10100000000000000001000000099DD7CA6BCF37C4F9F7DAACCADDD6B89",
    "reminderMinutesBeforeStart": 15,
    "isReminderOn": true,
    "hasAttachments": true,
    "subject": "Plan Easter egg hunt!",
    "body": {
        "contentType": "html",
        "content": "<html>\r\n<body>\r\nLet's get organized for this weekend's gathering.\r\n</body>\r\n</html>\r\n"
    },
    "bodyPreview": "Let's get organized for this weekend's gathering.",
    "importance": "normal",
    "sensitivity": "normal",
    "start": {
        "dateTime": "2016-03-26T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2016-03-26T18:00:00.0000000",
        "timeZone": "UTC"
    },
    "location": {
        "displayName": "",
        "address": {
            "type": "unknown"
        },
        "coordinates": {
        }
    },
    "isAllDay": false,
    "isCancelled": false,
    "isOrganizer": true,
    "recurrence": null,
    "responseRequested": true,
    "seriesMasterId": null,
    "showAs": "busy",
    "type": "singleInstance",
    "attendees": [
        {
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "type": "required",
            "emailAddress": {
                "name": "Randi Welch",
                "address": "randiw@contoso.onmicrosoft.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "Dana Swope",
            "address": "danas@contoso.onmicrosoft.com"
        }
    },
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADggYEcAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "onlineMeetingUrl": null,
    "attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments",
    "attachments": [
        {
            "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
            "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
            "lastModifiedDateTime": "2016-03-22T22:27:20Z",
            "name": "Hydrangea picture",
            "contentType": null,
            "size": 412,
            "isInline": false,
            "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
            "providerType": "oneDriveBusiness",
            "thumbnailUrl": null,
            "previewUrl": null,
            "permission": "edit",
            "isFolder": false
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
            "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAE1rHHth7YNLlR9WsgnODy0=",
            "lastModifiedDateTime": "2016-03-22T22:39:09Z",
            "name": "Koala picture",
            "contentType": null,
            "size": 382,
            "isInline": false,
            "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
            "providerType": "oneDriveBusiness",
            "thumbnailUrl": null,
            "previewUrl": null,
            "permission": "edit",
            "isFolder": false
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments/{attachment_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Der angeforderte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder die [Anlage des Elements](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2WRAAADTG9yAAA=/attachments/AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events('AAMkAGI2WRAAADTG9yAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2WRAAADTG9yAAA=')/Attachments('AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=')",
    "Id": "AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "LastModifiedDateTime": "2014-10-22T00:30:26Z",
    "Name": "Company Party.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11647,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQD...AAF4pAAAAAA=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

**Hinweis** Filter, Sortierung und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


**Antworttyp**

Der angeforderte [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder die [Anlage des Elements](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=/attachments/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        },
        {
            "name": "attachment_id",
            "type": "string",
            "description": "The attachment ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->




****


<a name="CreateAttachments"> </a>
## <a name="create-attachments"></a>Erstellen von Anlagen
Sie können eine Dateianlage oder für ein Ereignis [Erstellen Elementanlage](#CreateItemAttachment) erstellen.

REST-API: [Erstellen Sie eine Dateianlage (REST)](#CreateFileAttachment) | [Erstellen Elementanlage (REST)](#CreateItemAttachment) | 
[Erstellen Sie eine Referenz Anlage (REST)](#CreateReferenceAttachment)


<a name="CreateFileAttachment"></a>
###<a name="create-a-file-attachment-rest"></a>Erstellen Sie eine Dateianlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Fügen Sie eine Dateianlage für ein Ereignis hinzu.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|_Textkörper-Parameter_|
|@odata.type| string | #Microsoft.OutlookServices.FileAttachment |
|Name|string|Der Name der Anlage.|
|ContentBytes|Binär|Die Datei anfügen.|
 
<!-- Add post GA
```REST
[!INCLUDE [calendar_api_create_file_attachment](./_data/calendar_api_create_file_attachment.json)]
``` -->

**Antworttyp**

Die neue [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource).

****


<a name="CreateItemAttachment"></a>
###<a name="create-an-item-attachment-rest"></a>Erstellen Sie eine Elementanlage (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Hinzufügen einer Elementanlage auf ein Ereignis.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|_Textkörper-Parameter_|
|@odata.type| string | #Microsoft.OutlookServices.ItemAttachment |
|Name|string|Der Name der Anlage.|
|Element|Eine [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource), [Kontakt](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource) oder [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)Entität.|Das Element an.|
 

<!--Post GA
```REST
[!INCLUDE [calendar_api_create_item_attachment](./_data/calendar_api_create_item_attachment.json)]
``` -->


**Antworttyp**

Das neue [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

****

<a name="CreateReferenceAttachment"></a>

###<a name="create-a-reference-attachment-rest"></a>Erstellen Sie eine Referenz Anlage (REST)

<!-- ==================================== Start beta content ====================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**Bereich erforderlich**: https://outlook.office.com/mail.readwrite_

Fügen Sie eine Anlage Verweis auf ein Ereignis hinzu.

```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|String|Ereignis-ID.|
|_Textkörper-Parameter_|
|@odata.type|String|```#Microsoft.OutlookServices.ReferenceAttachment```|
|Name|String|Der Anzeigename der Anlage. Erforderlich.|
|SourceUrl|String | URL den Anlageninhalt abrufen. Ist dies eine URL zu einem Ordner, legen Sie dann für den Ordner in Outlook oder Outlook im Web ordnungsgemäß anzuzeigende **IsFolder** auf "true". Erforderlich.|

Geben Sie den **Namen** und **SourceUrl** -Parameter und alle schreibbaren [Verweis Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource) Eigenschaften im Textkörper Anforderung.



**Antworttyp**

Die [Anlage Verweis](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource).


**Beispiel für eine Anforderung**

Das folgende Beispiel fügt eine Anlage Verweis auf ein vorhandenes Ereignis. Die Anlage ist eine Verknüpfung zu einer Datei in OneDrive for Business.

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')/attachments
Content-Type: application/json

{
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"", 
    "Name": "Hydrangea picture", 
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg", 
    "ProviderType": "oneDriveBusiness", 
    "Permission": "Edit", 
    "IsFolder": "False" 
 }
```


**Beispielantwort**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
    "Id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
    "LastModifiedDateTime": "2016-03-22T22:27:20Z",
    "Name": "Hydrangea picture",
    "ContentType": null,
    "Size": 412,
    "IsInline": false,
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
    "ProviderType": "oneDriveBusiness",
    "ThumbnailUrl": null,
    "PreviewUrl": null,
    "Permission": "edit",
    "IsFolder": false
}
```


**Beispiel für eine Anforderung**

Das folgende Beispiel fügt eine Anlage Verweis in einem Anruf als Erstellen eines Ereignisses. Die Anlage ist eine Verknüpfung zu einer Datei in OneDrive for Business.

```
POST https://outlook.office.com/api/beta/me/events
Content-Type: application/json

{
  "Subject": "Plan Easter egg hunt!",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get organized for this weekend's gathering."
  },
  "Start": {
      "DateTime": "2016-03-25T10:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2016-03-25T11:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "randiw@contoso.onmicrosoft.com",
        "Name": "Randi Welch"
      },
      "Type": "Required"
    }
  ],
  "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"", 
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
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events/$entity",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAA4KZrrg==\"",
    "Id": "AAMkAGE1Mbs88AADggYEbAAA=",
    "CreatedDateTime": "2016-03-22T22:09:26.2918604Z",
    "LastModifiedDateTime": "2016-03-22T22:09:27.0754806Z",
    "ChangeKey": "mODEKWhc/Um6lA3uPm7PPAAA4KZrrg==",
    "Categories": [
    ],
    "OriginalStartTimeZone": "Pacific Standard Time",
    "OriginalEndTimeZone": "Pacific Standard Time",
    "ResponseStatus": {
        "Response": "Organizer",
        "Time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "040000008200E00074C5B7101A82E0080000000043FB607F8784D101000000000000000010000000B3A31CD7479252448ECE77242DE92587",
    "ReminderMinutesBeforeStart": 15,
    "IsReminderOn": true,
    "HasAttachments": true,
    "Subject": "Plan Easter egg hunt!",
    "Body": {
        "contentType": "html",
        "content": "<html>\r\n<body>\r\nLet's get organized for this weekend's gathering.\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "Let's get organized for this weekend's gathering.",
    "Importance": "normal",
    "Sensitivity": "normal",
    "Start": {
        "DateTime": "2016-03-25T10:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "End": {
        "DateTime": "2016-03-25T11:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Location": {
        "DisplayName": "",
        "Address": {
            "Type": "unknown"
        },
        "Coordinates": {
        }
    },
    "IsAllDay": false,
    "IsCancelled": false,
    "IsOrganizer": true,
    "Recurrence": null,
    "ResponseRequested": true,
    "SeriesMasterId": null,
    "ShowAs": "busy",
    "Type": "singleInstance",
    "Attendees": [
        {
            "Status": {
                "Response": "none",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "required",
            "EmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@contoso.onmicrosoft.com"
            }
        }
    ],
    "Organizer": {
        "EmailAddress": {
            "Name": "Dana Swope",
            "Address": "danas@contoso.onmicrosoft.com"
        }
    },
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADggYEbAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "OnlineMeetingUrl": null,
    "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADZ0CU9AAA%3D')/attachments",
    "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADZ0CU9AAABEgAQAGe4H1iqXwtLsrCCLLkDxqo=",
      "LastModifiedDateTime": null,
      "Name": Hydrangea picture,
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

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End beta content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist derzeit in der Beta-Version verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke der Artikel und select **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->



****


<a name="DeleteAttachments"> </a>
## <a name="delete-attachments"></a>Anlagen löschen

Löschen von Anlagen eines Ereignisses.

REST-API: [Löschen eine Anlage Ereignis (REST)](#DeleteAnEventAttachment)

<a name="DeleteAnEventAttachment"></a>
###<a name="delete-an-event-attachment-rest"></a>Löschen einer Anlage Ereignis (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

Die angegebene Anlage eines Ereignisses zu löschen. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource), [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)oder [Verweis Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)sein.

```no-highlight
DELETE https://outlook.office.com/api/beta/me/events/{event_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

**Beispiel für eine Anforderung**

```
DELETE https:/outlook.office.com/api/beta/me/events/AAMkAGE0MG4v1OAAA=/attachments/AAMkAGITG9yAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

Die angegebene Anlage eines Ereignisses zu löschen. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

**Beispiel für eine Anforderung**

```
DELETE https:/outlook.office.com/api/v2.0/me/events/AAMkAGE0MG4v1OAAA=/attachments/AAMkAGITG9yAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Die angegebene Anlage eines Ereignisses zu löschen. Das Attachment-Objekt kann eine [Dateianlage](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) oder [Element Anlage](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource).

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|event_id|string|Ereignis-ID.|
|attachment_id|string|Die Anlage-ID|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}",
    "requestUrl": "https:/outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=/attachments/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        },
        {
            "name": "event_id",
            "type": "string",
            "description": "The attachment ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        }
    ],
    "statusCode": 204

}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

<a name="GetReminders" > </a>
##Reminders erhalten möchten

Hier finden Sie eine Liste Ereignis Erinnerungen zwischen zwei Datumsangaben und Uhrzeiten aus einem Kalender.

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/ReminderView(StartDateTime='{DateTime}',EndDateTime='{DateTime}')
```
|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standard-Zeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|StartDateTime|string|Anfangs-Datum und Uhrzeit für zurückgegebene Erinnerungen.|
|EndDateTime|string|Das Enddatum und die Uhrzeit für zurückgegebene Erinnerungen.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header wurde nicht angegeben, wird der Zeitzone in UTC festgelegt.

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/ReminderView(StartDateTime='{DateTime}',EndDateTime='{DateTime}')
```
|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_Headerparameter_|
|Bevorzugen: |Outlook.TimeZone|Die Standard-Zeitzone für Ereignisse in der Antwort.|
|_URL-Parameter_|
|StartDateTime|string|Anfangs-Datum und Uhrzeit für zurückgegebene Erinnerungen.|
|EndDateTime|string|Das Enddatum und die Uhrzeit für zurückgegebene Erinnerungen.|

Verwenden Sie die _bevorzugen: outlook.timezone_ Kopfzeile an die Zeitzone für das Ereignis Start- und Enddatum zu verwendende Zeit in der Antwort.
Wenn das Ereignis in einer anderen Zeitzone erstellt wurde, werden die Anfangs- und Endzeiten an die angegebene Zeitzone angepasst.
[Diese Liste](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone) für den Namen der unterstützten Zeitzonen finden Sie. Wenn die _bevorzugen: outlook.timezone_ Header wurde nicht angegeben, wird der Zeitzone in UTC festgelegt.

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist nur für das Beta und v2. 0-Versionen verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke des Artikels und select **v2. 0** oder **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


<a name="SnoozeReminders"> </a>
##Erneut erinnern Erinnerungen

Erneut erinnern Sie eine Erinnerung für die Erinnerung bis zu einem neuen Zeitpunkt verschieben.

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events('{id}')/SnoozeReminder
```

|**Erforderliche Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Die ID des Ereignisses.|
|_Textkörper-Parameter_|
|NewReminderTime|[DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)|Neues Datum und Uhrzeit die Erinnerung ausgelöst.|

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events('{id}')/SnoozeReminder
```

|**Erforderliche Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Die ID des Ereignisses.|
|_Textkörper-Parameter_|
|NewReminderTime|[DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)|Neues Datum und Uhrzeit die Erinnerung ausgelöst.|

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist nur für das Beta und v2. 0-Versionen verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke des Artikels und select **v2. 0** oder **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

<a name="DismissReminders"> </a>
##Schließen Sie Erinnerungen

Dissmiss eine Erinnerung, das ausgelöst wurde.

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events({id})/DismissReminder
```

|**Erforderliche Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Die ID des Ereignisses.|


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events({id})/DismissReminder
```

|**Erforderliche Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Die ID des Ereignisses.|

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

Dieses Feature ist nur für das Beta und v2. 0-Versionen verfügbar. Verwenden Sie das Steuerelement, um weitere Informationen finden Sie in der oberen rechten Ecke des Artikels und select **v2. 0** oder **Beta**.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


<a name="GetCalendars"> </a>
##Abrufen von Kalendern

Sie können Abrufen einer Auflistung Kalender oder einen Kalender erhalten möchten.

REST-API: [Abrufen einer Auflistung Kalender (REST)](#GetCalendarCollection) | [Abrufen ein Kalenders (REST)](#GetCalendar)

Client-Bibliotheken: [Abrufen einer Auflistung Kalender oder einen Kalender (Client)](#GetCalendarsClient)

<a name="GetCalendarCollection"> </a>
###<a name="get-a-calendar-collection-rest"></a>Abrufen einer Auflistung Kalender (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Kalender des Benutzers abrufen (`calendars`) oder die Kalender aus einer bestimmten Kalendergruppe abzurufen.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
GET https://outlook.office.com/api/beta/me/calendars
GET https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}/calendars
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kennung der Kalender.|


**Beispiel für eine Anforderung**

```
https://outlook.office.com/api/beta/me/calendars
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
            "Id": "AAMkAGI2TGuLAAA=",
            "Name": "Calendar",
            "Color": "Auto",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendars
GET https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}/calendars
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kennung der Kalender.|

**Beispiel für eine Anforderung**

```
https://outlook.office.com/api/v2.0/me/calendars
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
            "Id": "AAMkAGI2TGuLAAA=",
            "Name": "Calendar",
            "Color": "Auto",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendars
GET https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}/calendars
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kennung der Kalender.|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+w==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
                "Name": "Calendar",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
            }
        ]
    }
}
```

**Antworttyp**

Der angeforderte [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) -Auflistung.

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="GetCalendar"> </a>
###<a name="get-a-calendar-rest"></a>Abrufen eines Kalenders (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Abrufen eines Kalenders nach ID. Sie können primären Kalender des Benutzers abrufen, indem Sie mit der `../me/calendar` Endpunkt.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/calendars/AAMkAGI2TGuLAAA=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
    "Id": "AAMkAGI2TGuLAAA=",
    "Name": "Calendar",
    "Color": "Auto",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/calendars/AAMkAGI2TGuLAAA=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
    "Id": "AAMkAGI2TGuLAAA=",
    "Name": "Calendar",
    "Color": "Auto",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+w==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
        "Name": "Calendar",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

**Antworttyp**

Der angeforderte [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource).

****

<a name="GetCalendarsClient"> </a>
###<a name="get-a-calendar-collection-or-a-calendar-client"></a>Rufen Sie eine Auflistung von Kalender oder einen Kalender (Client)

Kalender des Benutzers abzurufen. Verwenden Sie zum Kalender des Benutzers erhalten möchten, die `client.Me.Calendar` Kontextmenü-Eigenschaft. Wenn Sie einen anderen Kalender erhalten möchten, geben Sie die Kalender-ID als Index der **Calendars** -Auflistung an, oder verwenden Sie **GetById** -Methode.

Beispiel:`client.Me.Calendars[calendarId].ExecuteAsync()`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


**Hinweis** Kalender Websitesammlungen unterstützen Abfrageausdrücke wie **auswählen**, **OrderBy**und **durchführen**.

In diesem Beispiel wird die-Methode aufgerufen, [Ruft den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar" -->

```cs-i
var outlookClient = await CreateOutlookClientAsync("Calendar");
var calendars = await outlookClient.Me.Calendars
  .Take(10)
  .ExecuteAsync();

foreach(var calendar in calendars.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Calendar '{0}'.", calendar.Name);
}

```
```javascript-i
outlookClient.me.calendars.getCalendars().fetchAll(100).then(function(result) {
    result.forEach(function (calendar) {
        console.log('Calendar "' + calendar.name + '", URL ' + calendar.path)
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="CreateCalendars"> </a>
## <a name="create-calendars"></a>Kalender erstellen

REST-API: [Erstellen eines Kalenders (REST)](#CreateACalendar)

Client-Bibliotheken: [Erstellen eines Kalenders (Client)](#CreateCalendarsClient)

<a name="CreateACalendar"></a>
###<a name="create-a-calendar-rest"></a>Erstellen Sie einen Kalender (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Erstellen ein Kalenders in der Standardgruppe Kalender mithilfe der `../me/calendars` Kontextmenü, oder in einer bestimmten Gruppe durch das Veröffentlichen in der Gruppe `calendars` Endpunkt.


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/calendars
POST https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}/calendars
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kalender Gruppen-ID, wenn Sie die Kalender aus einer bestimmten Gruppe optimal nutzen.|
|_Textkörper-Parameter_|
|Name|string|Der Name der neuen Kalender.|
 

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/calendars
Content-Type: application/json

{
  "Name": "Social"
}

```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLHAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
  "Id": "AAMkAGE4xLHAAA=",
  "Name": "Social",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/calendars
POST https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}/calendars
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kalender Gruppen-ID, wenn Sie die Kalender aus einer bestimmten Gruppe optimal nutzen.|
|_Textkörper-Parameter_|
|Name|string|Der Name des neuen Kalenders.|
 

**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/calendars
Content-Type: application/json

{
  "Name": "Social"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLHAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
  "Id": "AAMkAGE4xLHAAA=",
  "Name": "Social",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/calendars
POST https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}/calendars
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calender_group_id|string|Die Kalender Gruppen-ID, wenn Sie die Kalender aus einer bestimmten Gruppe optimal nutzen.|
|_Textkörper-Parameter_|
|Name|string|Der Name des neuen Kalenders.|
 


```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 22
    },
    "parameterDetails": [],
    "requestBody": {
        "Name": "Social"
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLHAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLHAAA=",
        "Name": "Social",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



**Antworttyp**

Den neuen [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource).

****

<a name="CreateCalendarsClient"> </a>
### <a name="create-a-calendar-client"></a>Erstellen eines Kalenders (Client)

Erstellen Sie einen Kalender. Finden Sie unter [Create Ereignisse](#CreateEventsClient) für ein Beispiel zum Erstellen eines Ereignisses.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
Calendar newCal = new Calendar
{
    Name = "Personal"
};

// Add the calendar to the Calendars collection
await client.Me.Calendars.AddCalendarAsync(newCal);

// Get the ID of the calendar
string calendarId = newCal.Id;
```

<!-- ENDSECTION -->

****


<a name="UpdateCalendars"> </a>
## <a name="update-calendars"></a>Aktualisieren von Kalendern

REST-API: [Aktualisieren eines Kalenders (REST)](#UpdateACalendar)

Client-Bibliotheken: [Aktualisieren ein Kalenders (Client)](#UpdateCalendarsClient)

<a name="UpdateACalendar"></a>
###<a name="update-a-calendar-rest"></a>Aktualisieren eines Kalenders (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Ändern Sie den Namen eines Kalenders. **Name** ist die Eigenschaft nur schreibbare [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) .


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|
|_Textkörper-Parameter_|
|Name|string|Der neue Name des Kalenders.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/beta/me/calendars/AAMkAGE4xLIAAA=
Content-Type: application/json

{
  "Name": "Social events"
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLIAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
  "Id": "AAMkAGE4xLIAAA=",
  "Name": "Social events",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|
|_Textkörper-Parameter_|
|Name|string|Der neue Name des Kalenders.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/v2.0/me/calendars/AAMkAGE4xLIAAA=
Content-Type: application/json

{
  "Name": "Social events"
}
```

**Beispielantwort**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLIAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
  "Id": "AAMkAGE4xLIAAA=",
  "Name": "Social events",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|
|_Textkörper-Parameter_|
|Name|string|Der neue Name des Kalenders.|

```REST
{
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calender_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 29
    },
    "parameterDetails": [
        {
            "name": "calender_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA="
        }
    ],
    "requestBody": {
        "Name": "Social events"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
        "Name": "Social events",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



**Antworttyp**

Der aktualisierte [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource).

****

<a name="UpdateCalendarsClient"> </a>
### <a name="update-a-calendar-client"></a>Aktualisieren eines Kalenders (Client)

Ändern Sie den Namen eines Kalenders. **Name** ist die nur schreibbare Eigenschaft für einen Kalender.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die ID Kalender](#GetCalendars).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar by ID
ICalendar calendarToUpdate = await client.Me.Calendars[calendarId].ExecuteAsync();
calendarToUpdate.Name = "Family";

// Commit the change
await calendarToUpdate.UpdateAsync();

// Get the updated property
string newCalendarName = calendarToUpdate.Name;
```

<!-- ENDSECTION -->


Sie können mehrere Updates mithilfe der clientseitigen definieren und senden die Anforderungen alle gleichzeitig (diese batch) mit dem folgenden Muster:
1. Rufen Sie `UpdateAsync(true)` für jede Entität, die Sie aktualisieren möchten. Angeben von `true` registriert die Updates lokal auf dem Client, jedoch nicht auf dem Server bereitstellen.
2. Rufen Sie `client.Context.SaveChangesAsync()` lokal für die Bereitstellung aller Updates, die registriert sind.

****

<a name="DeleteCalendars"> </a>
## <a name="delete-calendars"></a>Löschen von Kalendern

Löschen eines Kalenders.

REST-API: [Löschen ein Kalenders (REST)](#DeleteACalendar)

Client-Bibliotheken: [Löschen eines Kalenders (Client)](#DeleteCalendarsClient)

<a name="DeleteACalendar"></a>
###<a name="delete-a-calendar-rest"></a>Löschen eines Kalenders (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
DELETE https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/calendars/AAMkAGE4xLIAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/calendars/AAMkAGE4xLIAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_id|string|Die Kalender-ID.|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calender_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calender_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA="
        }
    ],
    "statusCode": 204

}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->




****

<a name="DeleteCalendarsClient"> </a>
### <a name="delete-a-calendar-client"></a>Löschen eines Kalenders (Client)


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die ID Kalender](#GetCalendars).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar by ID
ICalendar calendarToDelete = await client.Me.Calendars[calendarId].ExecuteAsync();
    
// Delete the calendar
await calendarToDelete.DeleteAsync(false);
```

<!-- ENDSECTION -->

****

<a name="GetCalendarGroups"> </a>
## <a name="get-calendar-groups"></a>Kalendergruppen abrufen

Sie können eine Auflistung der Kalender oder [Abrufen einer Kalendergruppe](#GetCalendarGroup)abrufen.


**Hinweis** Outlook.com unterstützt nur die Kalender Standardgruppe zugänglich ist die `../me/calendars` Verknüpfung.


REST-API: [Abrufen einer Gruppe-Auflistung des Kalenders (REST)](#GetCalendarGroupCollection) | [Abrufen einer Kalendergruppe (REST)](#GetCalendarGroup)

Client-Bibliotheken: [Abrufen von Kalendergruppen (Client)](#GetCalendarGroupsClient)


****


<a name="GetCalendarGroupCollection"> </a>
###<a name="get-a-calendar-group-collection-rest"></a>Abrufen einer Gruppe-Auflistung des Kalenders (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Rufen Sie die Kalendergruppen in einem Postfach. 


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendargroups
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/calendargroups
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
            "Id": "AAMkAGI2TGuKAAA=",
            "Name": "My Calendars",
            "ClassId": "0006f0b7-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuMAAA=')",
            "Id": "AAMkAGI2TGuMAAA=",
            "Name": "Other Calendars",
            "ClassId": "0006f0b8-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A=="
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendargroups
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .

**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/calendargroups
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
            "Id": "AAMkAGI2TGuKAAA=",
            "Name": "My Calendars",
            "ClassId": "0006f0b7-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuMAAA=')",
            "Id": "AAMkAGI2TGuMAAA=",
            "Name": "Other Calendars",
            "ClassId": "0006f0b8-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendargroups
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
                "Name": "My Calendars",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
                "ClassId": "0006f0b7-0000-0000-c000-000000000046"
            },
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuMAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0/A==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuMAAA=",
                "Name": "Other Calendars",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A==",
                "ClassId": "0006f0b8-0000-0000-c000-000000000046"
            }
        ]
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**Antworttyp**

Der angeforderte [Kalendergruppe](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource) -Auflistung.

****


<a name="GetCalendarGroup"> </a>
###<a name="get-a-calendar-group-rest"></a>Abrufen einer Kalendergruppe (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.Read_
- _WL.calendars_
- _WL.Contacts\_Kalender_

Abrufen von Kalender Gruppen-ID


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/beta/me/calendargroups/AAMkAGI2TGuKAAA=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
    "Id": "AAMkAGI2TGuKAAA=",
    "Name": "My Calendars",
    "ClassId": "0006f0b7-0000-0000-c000-000000000046",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|


**Beispiel für eine Anforderung**

```
GET https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGI2TGuKAAA=
```

**Beispielantwort**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
    "Id": "AAMkAGI2TGuKAAA=",
    "Name": "My Calendars",
    "ClassId": "0006f0b7-0000-0000-c000-000000000046",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```

**Hinweis** Filtern, Sortieren und Paging-Parametern finden Sie unter [OData-Abfrageparametern](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams) .


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**Antworttyp**

Der angeforderte [Kalendergruppe](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource).

****

<a name="GetCalendarGroupsClient"> </a>
### <a name="get-calendar-groups-client"></a>Erste Kalendergruppen (Client)

Abrufen eines Benutzers Kalendergruppen. Um eine Gruppe von anderen Kalender erhalten möchten, geben Sie die Kalender-Gruppen-ID als der Index der Auflistung **CalendarGroups** oder verwenden Sie **GetById** -Methode.

Beispiel:`client.Me.CalendarGroups[calendarGroupId].ExecuteAsync()`


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


**Hinweis** Kalender Gruppe Websitesammlungen unterstützen Abfrageausdrücke wie **Wählen**, **OrderBy**und **Übernehmen**.

In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IPagedCollection<ICalendarGroup> calendarGroupsResults = await client.Me.CalendarGroups.ExecuteAsync();

// Get the ID of the first calendar group
string groupId = calendarGroupsResults.CurrentPage[0].Id;
```

<!-- ENDSECTION -->

****


<a name="CreateCalendarGroups"> </a>
## <a name="create-calendar-groups"></a>Kalendergruppen erstellen

Erstellen Sie eine Kalendergruppe. **Name** ist die nur schreibbare Eigenschaft für eine Kalendergruppe.


**Hinweis** Outlook.com unterstützt nur die Kalender Standardgruppe zugänglich ist die `../me/calendars` Verknüpfung. Sie können nicht in Outlook.com einem anderen Kalendergruppe erstellen.


REST-API: [Erstellen einer Kalendergruppe (REST)](#CreateACalendarGroup)

Client-Bibliotheken: [Erstellen einer Kalendergruppe (Client)](#CreateCalendarGroupsClient)

<a name="CreateACalendarGroup"></a>
###<a name="create-a-calendar-group-rest"></a>Erstellen einer Kalendergruppe (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_



<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/calendargroups
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-parameter_|
|_Textkörper-Parameter_|
|Name|string|Der Name der Gruppe "Kalender".|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/beta/me/calendargroups
Content-Type: application/json

{
  "Name": "Birthdays"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0M4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
  "Id": "AAMkAGE0M4xLGAAA=",
  "Name": "Birthdays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/calendargroups
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-parameter_|
|_Textkörper-Parameter_|
|Name|string|Der Name der Gruppe "Kalender".|


**Beispiel für eine Anforderung**

```
POST https://outlook.office.com/api/v2.0/me/calendargroups
Content-Type: application/json

{
  "Name": "Birthdays"
}
```

**Beispielantwort**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0M4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
  "Id": "AAMkAGE0M4xLGAAA=",
  "Name": "Birthdays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/calendargroups
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-parameter_|
|_Textkörper-Parameter_|
|Name|string|Der Name der Gruppe "Kalender".|


```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 23
    },
    "parameterDetails": [],
    "requestBody": {
        "Name": "Birthdays"
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
        "Name": "Birthdays",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
        "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**Antworttyp**

Die neue [Kalendergruppe](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource).


****

<a name="CreateCalendarGroupsClient"> </a>
### <a name="create-a-calendar-group-client"></a>Erstellen einer Kalendergruppe (Client)


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [den Outlook Services Client erhalten hat](..\api\use-outlook-rest-api.md#GetClient).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
CalendarGroup newCalendarGroup = new CalendarGroup
{
    Name = "Business"
};

// Add it to the CalendarGroups collection
await client.Me.CalendarGroups.AddCalendarGroupAsync(newCalendarGroup);

// Get the ID of the calendar group
string calendarGroupId = newCalendarGroup.Id;
```

<!-- ENDSECTION -->


****


<a name="UpdateCalendarGroups"> </a>
## <a name="update-calendar-groups"></a>Kalendergruppen aktualisieren

REST-API: [Aktualisieren einer Kalendergruppe (REST)](#UpdateACalendarGroup)

Client-Bibliotheken: [Aktualisieren eine Kalendergruppe (Client)](#UpdateCalendarGroupsClient)

<a name="UpdateACalendarGroup"></a>
### <a name="update-a-calendar-group-rest"></a>Aktualisieren einer Kalendergruppe (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_

Ändern Sie den Namen einer Gruppe Kalender. **Name** ist die Eigenschaft nur schreibbare [Kalendergruppe](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource) .


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|
|_Textkörper-Parameter_|
|Name|string|Der Name der Kalendergruppe der aktualisierten.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/beta/me/calendargroups/AAMkAGE0M4xLGAAA=
Content-Type: application/json

{
  "Name": "Holidays"
}
```

**Beispielantwort**

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0MGM4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
  "Id": "AAMkAGE0MGM4xLGAAA=",
  "Name": "Holidays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|
|_Textkörper-Parameter_|
|Name|string|Der Name der Kalendergruppe der aktualisierten.|


**Beispiel für eine Anforderung**

```
PATCH https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGE0M4xLGAAA=
Content-Type: application/json

{
  "Name": "Holidays"
}
```

**Beispielantwort**

```
{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0MGM4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
  "Id": "AAMkAGE0MGM4xLGAAA=",
  "Name": "Holidays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|
|_Textkörper-Parameter_|
|Name|string|Der Name der Kalendergruppe der aktualisierten.|


```REST
 {
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA="
        }
    ],
    "requestBody": {
        "Name": "Holidays"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
        "Name": "Holidays",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
        "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

**Antworttyp**

Die aktualisierte [Kalendergruppe](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource).

****

<a name="UpdateCalendarGroupsClient"> </a>
### <a name="update-a-calendar-group-client"></a>Aktualisieren einer Kalendergruppe (Client)

Ändern Sie den Namen einer Gruppe Kalender. **Name** ist die nur schreibbare Eigenschaft für eine Kalendergruppe.


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die Gruppen-ID für Kalender](#GetCalendarGroups).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar group by ID
ICalendarGroup groupToUpdate = await client.Me.CalendarGroups[groupId].ExecuteAsync();
groupToUpdate.Name = "Contoso";

// Commit the change
await groupToUpdate.UpdateAsync();

// Get the updated property
string newCalendarGroupName = groupToUpdate.Name;
```

<!-- ENDSECTION -->


Sie können mehrere Updates mithilfe der clientseitigen definieren und senden die Anforderungen alle gleichzeitig (diese batch) mit dem folgenden Muster:
1. Rufen Sie `UpdateAsync(true)` für jede Entität, die Sie aktualisieren möchten. Angeben von `true` registriert die Updates lokal auf dem Client, jedoch nicht auf dem Server bereitstellen.
2. Rufen Sie `client.Context.SaveChangesAsync()` lokal für die Bereitstellung aller Updates, die registriert sind.


****


<a name="DeleteCalendarGroups"> </a>
## <a name="delete-calendar-groups"></a>Kalendergruppen löschen

Löschen einer Kalendergruppe.


**Hinweis** Outlook.com unterstützt nur die Kalender Standardgruppe zugänglich ist die `../me/calendars` Verknüpfung. Diese Kalendergruppe nicht gelöscht.


REST-API: [Löschen einer Kalendergruppe (REST)](#DeleteACalendarGroup)

Client-Bibliotheken: [Löschen einer Kalendergruppe (Client)](#DeleteCalendarGroupsClient)

<a name="DeleteACalendarGroup"></a>
###<a name="delete-a-calendar-group-rest"></a>Löschen einer Kalendergruppe (REST)

_**Mindestens erforderliche Bereich**: einer der folgenden:_
- _https://Outlook.Office.com/calendars.ReadWrite_
- _WL.Calendars\_aktualisieren_
- _WL.Events\_erstellen_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|


**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/beta/me/calendargroups/AAMkAGE0MGM4xLGAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|

**Beispiel für eine Anforderung**

```
DELETE https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGE0MGM4xLGAAA=
```

**Beispielantwort**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|calendar_group_id|string|Die Kennung der Kalender.|


```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA="
        }
    ],
    "statusCode": 204

}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="DeleteCalendarGroupsClient"> </a>
### <a name="delete-a-calendar-group-client"></a>Löschen einer Kalendergruppe (Client)


**Aufmerksamkeit** Wenn Sie Postfachdaten auf Outlook.com zugreifen, keine verwenden Sie die Clientbibliotheken und direkte Anrufe bei der REST-API.


In diesem Beispiel wird davon ausgegangen Sie bereits [haben Sie den Outlook-Client](..\api\use-outlook-rest-api.md#GetClient) und [haben Sie die Gruppen-ID für Kalender](#GetCalendarGroups).

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar group by ID
ICalendarGroup groupToDelete = await client.Me.CalendarGroups[groupId].ExecuteAsync();

// Delete the group
await groupToDelete.DeleteAsync(); 
```

<!-- ENDSECTION -->

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelt.


- [Erste Schritte mit e-Mail-Nachrichten, Kalender und Kontakte REST-APIs](http://dev.outlook.com/RestGettingStarted).
  
- Verwenden Sie die interaktive [API Sandbox](http://apisandbox.msdn.microsoft.com/)mit Office-REST-APIs.
    
- Soll Beispiele werden? [Wir haben sie](..\howto\starter-projects-and-code-samples.md).
    

Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Outlook-REST-API für das Outlook Developer Center](http://dev.outlook.com/RestGettingStarted/Overview)

- [Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)
    
- [Office 365-app-Authentifizierung und Ressource Autorisierung](..\howto\common-app-authentication-tasks.md)
    
- [Registrieren Sie Ihre app mit Azure AD manuell, sodass es auf Office 365-APIs zugreifen können](..\howto\add-common-consent-manually.md)
  
- [Mail-API-Referenz](..\api\mail-rest-operations.md)
  
- [Kontakte-API-Referenz](..\api\contacts-rest-operations.md)

- [Aufgabe REST-API (Preview)](..\api\task-rest-operations.md)

- [OneDrive-API](https://dev.onedrive.com/)

- [Ermittlung REST-Dienst-API-Referenzen für Vorgänge](..\api\discovery-service-rest-operations.md)

- [Resource-Referenz für die e-Mail-Nachrichten, Kalender, Kontakte und Aufgabe REST-APIs](..\api\complex-types-for-mail-contacts-calendar.md)



[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefilteringhtml)]

