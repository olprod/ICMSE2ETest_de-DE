<<<<<<< HEAD ms. TocTitle: Office 365-API-Referenz Titel: Office 365-API-Referenz Beschreibung: Suchen Sie nach Office 365-API-Referenzen und Informationen zur REST und Client Library-APIs, zur Interaktion mit e-Mails, Kontakte und Kalenderdaten, Dateien und Discovery-Dienst.
MS. ContentId: 6736150c-641e-4e1b-bcc0-6cce0996779d ms.topic: Verweis (API) ms.date: 21 April 2016=======
---
MS. TOCTitle: Titel der Office 365-API-Referenz: Office 365-API-Referenz Beschreibung: Suchen Sie nach Office 365-API-Referenzen und Informationen über REST und Client Bibliotheks-APIs.
MS. ContentId: 6736150c-641e-4e1b-bcc0-6cce0996779d ms.date: 20 September 2016
>>>>>>> Staging

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="office-365-api-reference"></a>Office 365-API-Referenz 
    
 _**Gilt für:** Exchange Online | Office 365 | OneDrive for Business_

<<<<<<< KOPF
<a name="p-classpreviewnotethis-documentation-covers-features-that-are-currently-in-preview-for-information-about-working-with-preview-features-see-preview-developer-features-on-the-office-365-platformhowtoplatform-development-preview-features-overviewmdp"></a><p class="previewnote">In dieser Dokumentation behandelt Features, die derzeit in der Vorschau werden. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>
=======
[!INCLUDE [Use Microsoft Graph](../includes/use-msgraph-note.md)]

Die Office 365-APIs können Sie bieten Zugriff auf Ihre Kunden Office 365 Daten, einschließlich der Dinge, die sie – ihre e-Mail, Kalender, Kontakte, Benutzer und Gruppen, Dateien und Ordner – alle direkt in Ihrer app selbst wichtig sind. 
            
Sie können die Office 365-APIs aus Lösungen über alle Mobile, Web und desktop-Plattformen zugreifen. Unabhängig davon, Ihre Entwicklungsplattform oder Tools. Damit, ob Sie Webanwendungen mithilfe von .NET, PHP, Java, Python oder Ruby Schienenfahrzeugen oder Erstellen von apps für universelle Apps für Windows, iOS erstellen Android, oder auf einem anderen Geräteplattform Ihrer Wahl ist.
    
### <a name="office-365-sdks-make-app-development-easier"></a>Office 365-SDKs vereinfachen app-Entwicklung

Sie können Programmieren direkt die REST-APIs interagieren mit Office 365, schreiben und Verwalten von Code, um die Verwaltung von Authentifizierungstoken, erstellen die korrekten URLs und Abfragen für die API, die Sie zugreifen, möchten und andere Aufgaben. Die Office 365-SDKs für Visual Studio, Eclipse und Android Studio oder Xcode, einer Verringerung die Komplexität des Codes Sie auf der Office 365-APIs zugreifen schreiben müssen.

Die [Office Developer Tools für Visual Studio](http://aka.ms/OfficeDevToolsForVS2013) enthalten SDKs, die .NET bereitstellen und JavaScript-Bibliotheken, die Text fließt um die Office 365-REST-Dienste, und geben Sie sogar noch einfacher zu Ihrer Office 365-Daten herstellen. Die SDKs stehen für ASP.NET MVC, ASP.NET Web Forms, WPF, Windows Forms, Universal App, Cordova und Xamarin Projekttypen in Visual Studio. 

Für Android Entwickler ist das Android SDK für Eclipse und Android Studio jetzt auch im Allgemeinen verfügbar.  Finden Sie unter der [Office 365 SDK für Android](https://github.com/OfficeDev/Office-365-SDK-for-Android). 
>>>>>>> Staging

Für iOS-apps unterstützt die iOS SDK für Xcode (Preview) Objective-C und Swift Sprachen in [Xcode 6](https://developer.apple.com/xcode/). Finden Sie im [Office 365-SDK für iOS](https://github.com/OfficeDev/Office-365-SDK-for-iOS)aus. 


<!--
<a href="#bk_groups"><img alt="Groups API (preview) icon" src="office/office365/api/images/O365APIs_REST_Reference_icons_groups.png" /></a>
-->

<!--
<a href="#bk_mail" id="Mail">
    <img title="Mail API" src="http://i.imgur.com/qhjA7Qy.png" onmouseover="this.src='http://i.imgur.com/s5rJ51y.png'" onmouseout="this.src='http://i.imgur.com/qhjA7Qy.png'" />
</a>
<a href="#bk_contacts" id="Contacts">
    <img title="Contacts API" src="http://i.imgur.com/xJbLQcp.png" onmouseover="this.src='http://i.imgur.com/idZpJmq.png'" onmouseout="this.src='http://i.imgur.com/xJbLQcp.png'" />
</a>
<a href="#bk_calendar" id="Calendar">
    <img title="Calendar API" src="http://i.imgur.com/dKrWDZ2.png" onmouseover="this.src='http://i.imgur.com/9D0eQGe.png'" onmouseout="this.src='http://i.imgur.com/dKrWDZ2.png'" />
</a>
-->


## <a name="batching-outlook-rest-requests-preview"></a>Batchverarbeitung von Outlook-REST-Anforderungen (Preview)

[Senden von Outlook-REST-Anforderungen in batches](..\api\batch-outlook-rest-requests.md)


## <a name="outlook-task"></a>Outlook-Aufgabe
[Aufgabe API](..\api\task-rest-operations.md)

**Task-Vorgänge** &nbsp; 
 [Erstellen Aufgaben](..\api\task-rest-operations.md#CreateTasks) | [Aufgaben abrufen](..\api\task-rest-operations.md#GetTasks) | [Aktualisieren von Vorgängen](..\api\task-rest-operations.md#UpdateTasks) | [Löschen von Vorgängen](..\api\task-rest-operations.md#DeleteTasks) | 
[Ausführen von Aufgaben](..\api\task-rest-operations.md#CompleteTasks) | [Synchronisieren Vorgänge oder Aufgabenordner](..\api\task-rest-operations.md#SyncTasks) 


**Aufgabe Ordner Vorgänge** &nbsp; 
 [Aufgabenordner erstellen](..\api\task-rest-operations.md#CreateTaskFolders) | [Aufgabenordner abrufen](..\api\task-rest-operations.md#GetTaskFolders) | [Aktualisieren Aufgabenordner](..\api\task-rest-operations.md#UpdateTaskFolders) | 
[Aufgabenordner löschen](..\api\task-rest-operations.md#DeleteTaskFolders) | [Synchronisieren Vorgänge oder Aufgabenordner](..\api\task-rest-operations.md#SyncTasks) 


**Aufgabe Gruppe Vorgänge** &nbsp; 
 [Erstellen Vorgangsgruppen](..\api\task-rest-operations.md#CreateTaskGroups) | [Vorgangsgruppen abrufen](..\api\task-rest-operations.md#GetTaskGroups) | [Aktualisieren Vorgangsgruppen](..\api\task-rest-operations.md#UpdateTaskGroups) | 
[Vorgangsgruppen löschen](..\api\task-rest-operations.md#DeleteTaskGroups)


<a name="bk_people"> </a>

##<a name="outlook-people-preview"></a>Outlook Personen (Preview)

[Personen API](..\api\people-rest-operations.md)

**Navigieren:** &nbsp;  
 [Browsing](..\api\people-rest-operations.md#BrowsePeople) | [Paging](..\api\people-rest-operations.md#BrowsePaging) | 
[Sortierung](..\api\people-rest-operations.md#BrowseSort) | [Einschränken des Zugriffs durch](..\api\people-rest-operations.md#BrowsePageSize) |
[auswählen](..\api\people-rest-operations.md#BrowseSelecting) | [Filtern](..\api\people-rest-operations.md#BrowseFiltering) |
[Filtern und auswählen](..\api\people-rest-operations.md#BrowseSelectingAndFiltering)

**Suche:** &nbsp; 
 [Thema auswählen](..\api\people-rest-operations.md#SearchTopic) |
[Filtern eine Suche](..\api\people-rest-operations.md#SearchFilter) |
[Fuzzy-Suche](..\api\people-rest-operations.md#FuzzySearch)



## <a name="office-365-data-extensions"></a>Erweiterungen für Office 365-Daten

[Daten Extensions API](..\api\extensions-rest-operations.md)

**Erweiterungen für Dateitypen öffnen:** &nbsp; [Erstellen in vorhandenen Element](..\api\extensions-rest-operations.md#CreateExtensionInExistingItem) | [erstellen, mit neues Element](..\api\extensions-rest-operations.md#CreateExtensionInNewItem) |
[Abrufen](..\api\extensions-rest-operations.md#GetExtension) | [Element erweitert abrufen](..\api\extensions-rest-operations.md#GetExpandedExtension) |
[Update](..\api\extensions-rest-operations.md#UpdateExtension) | [Löschen](..\api\extensions-rest-operations.md#DeleteExtension)


## <a name="outlook-extended-properties"></a>Outlook erweiterte Eigenschaften

[Erweiterte Eigenschaften API](..\api\extended-properties-rest-operations.md)

**Erweiterte Eigenschaften**  &nbsp;  [Erstellen in vorhandenen item](..\api\extended-properties-rest-operations.md#CreateExtendedPropertyInExistingItem) | 
[erstellen, mit neues Element](..\api\extended-properties-rest-operations.md#CreateExtendedPropertyInNewItem) | 
[Element erweitert abrufen](..\api\extended-properties-rest-operations.md#GetExpandedExtendedProperty) | 
[Filter](..\api\extended-properties-rest-operations.md#GetItemByFilteringExtendedProperty)



<a name="bk_mail"> </a>

##<a name="outlook-mail"></a>Outlook-mail

[Mail-API](..\api\mail-rest-operations.md) 

**Nachrichten:** &nbsp; [Abrufen](..\api\mail-rest-operations.md#Getmessages) | [Erstellen und senden](..\api\mail-rest-operations.md#Sendmessages) |
 [Antworten auf](..\api\mail-rest-operations.md#Replytomessages) | [Weiterleiten](..\api\mail-rest-operations.md#Forwardmessages) |
 [Update](..\api\mail-rest-operations.md#Updatemessages) | [Löschen](..\api\mail-rest-operations.md#DeleteMessages) |
 [verschieben oder kopieren](..\api\mail-rest-operations.md#MoveCopymessages)

**Anlagen:**&nbsp;  [Abrufen](..\api\mail-rest-operations.md#GetAttachments) |
 [Erstellen](..\api\mail-rest-operations.md#CreateAttachments) | [Löschen](..\api\mail-rest-operations.md#DeleteAttachments)

**Ordner:**&nbsp;  [Abrufen](..\api\mail-rest-operations.md#GetFolders) | [Erstellen](..\api\mail-rest-operations.md#CreateFolders) | [Update](..\api\mail-rest-operations.md#UpdateFolders) |
 [Löschen](..\api\mail-rest-operations.md#DeleteFolders) | [verschieben oder kopieren](..\api\mail-rest-operations.md#MoveCopyFolders)


<a name="bk_contacts"> </a>

##<a name="outlook-contacts"></a>Outlook-Kontakte

[Kontakte-API](..\api\contacts-rest-operations.md)

**Kontakte:**&nbsp;  [Abrufen](..\api\contacts-rest-operations.md#GetContacts) | [Erstellen](..\api\contacts-rest-operations.md#CreateContacts) |
 [Update](..\api\contacts-rest-operations.md#UpdateContacts) | [Löschen](..\api\contacts-rest-operations.md#DeleteContacts) 
 

**Wenden Sie sich an Ordnern:**&nbsp;  [Abrufen](..\api\contacts-rest-operations.md#GetContactFolders)


<a name="bk_calendar"> </a>

##<a name="outlook-calendar"></a>Outlook-Kalender

[Kalender-API](..\api\calendar-rest-operations.md)

**Kalenderansicht:**  &nbsp;  [Abrufen](..\api\calendar-rest-operations.md#GetCalendarView) | [Sync](..\api\calendar-rest-operations.md#SyncCalendarView)

**Ereignisse:** &nbsp; [Abrufen](..\api\calendar-rest-operations.md#GetEvents) | [Sync](..\api\calendar-rest-operations.md#SyncCalendarView) |
 [Erstellen](..\api\calendar-rest-operations.md#CreateEvents) |
 [Update](..\api\calendar-rest-operations.md#UpdateEvents) | [reagieren](..\api\calendar-rest-operations.md#RespondToEvents) | 
 [Löschen](..\api\calendar-rest-operations.md#DeleteEvents)  

**Anlagen:** &nbsp; 
 [Get](..\api\calendar-rest-operations.md#GetAttachments) | [Create](..\api\calendar-rest-operations.md#reateAttachments) |
 [Delete](..\api\calendar-rest-operations.md#DeleteAttachments)
 
 **Erinnerungen:** &nbsp; 
  [Abrufen](..\api\calendar-rest-operations.md#GetReminders) | 
 [erneut erinnern](..\api\calendar-rest-operations.md#SnoozeReminders) | 
 [Schließen](..\api\calendar-rest-operations.md#DismissReminders)

**Kalender:** &nbsp; [Abrufen](..\api\calendar-rest-operations.md#GetCalendars) |
 [Erstellen](..\api\calendar-rest-operations.md#CreateCalendars) | [Update](..\api\calendar-rest-operations.md#UpdateCalendars) |
 [Löschen](..\api\calendar-rest-operations.md#DeleteCalendars)  

**Kalender-Gruppen:**&nbsp;   [Abrufen](..\api\calendar-rest-operations.md#GetCalendarGroups) |
 [Erstellen](..\api\calendar-rest-operations.md#CreateCalendarGroups) | [Update](..\api\calendar-rest-operations.md#UpdateCalendarGroups) |
 [Löschen](..\api\calendar-rest-operations.md#DeleteCalendarGroups)



##<a name="resource-reference-for-the-mail-calendar-contacts-and-task-apis"></a>Resource-Referenz für die E-Mail, Kalender, Kontakte und Task-APIs

[Resource-Verweis](..\API\complex-types-for-mail-contacts-calendar.md) 
 
 **Entitäten:** &nbsp; [Kalender](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) |
 [CalendarGroup](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource) | [Kontakt](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource) |
 [ContactFolder](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource) | [Ereignis](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) |
 [EventMessage](..\api\complex-types-for-mail-contacts-calendar.md#EventMessageResource) | [Erweiterte Eigenschaften](..\api\complex-types-for-mail-contacts-calendar.md#ExtendedProperties) | 
 [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) | [Ordner](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource) |
 [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource) | [Nachricht](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) |
 [Aufgabe (Preview)](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource) | [TaskFolder (Preview)](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource) | 
 [Projektgruppe beschäftigt (Preview)](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource) | 
 [Benutzer](..\api\complex-types-for-mail-contacts-calendar.md#UserResource)   
 
 **Komplexe Typen:** &nbsp; [Attendee](..\api\complex-types-for-mail-contacts-calendar.md#Attendee) | 
 [AttendeeBase](..\api\complex-types-for-mail-contacts-calendar.md#AttendeeBase) (Preview) |  [AttendeeAvailability](..\api\complex-types-for-mail-contacts-calendar.md#AttendeeAvailability) (Vorschau) |  [DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZoneBeta)  | 
  [EmailAddress](..\api\complex-types-for-mail-contacts-calendar.md#EmailAddress) | 
 [GeoCoordinates](..\api\complex-types-for-mail-contacts-calendar.md#GeoCoordinates) | 
 [ItemBody](..\api\complex-types-for-mail-contacts-calendar.md#ItemBody)  | 
 [Speicherort](..\api\complex-types-for-mail-contacts-calendar.md#Location) (Preview) |  [LocationConstraint](..\api\complex-types-for-mail-contacts-calendar.md#LocationConstraint) (Vorschau) |  [MeetingTimeCandidate](..\api\complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidate) (Vorschau) |  [PatternedRecurrence](..\api\complex-types-for-mail-contacts-calendar.md#PatternedRecurrence)  | 
  [Physikalische Adresse](..\api\complex-types-for-mail-contacts-calendar.md#PhysicalAddress) | 
 [Empfänger](..\api\complex-types-for-mail-contacts-calendar.md#Recipient) | 
 [RecurrencePattern](..\api\complex-types-for-mail-contacts-calendar.md#RecurrencePattern) | 
 [RecurrenceRange](..\api\complex-types-for-mail-contacts-calendar.md#RecurrenceRange) | 
 [ResponseStatus](..\api\complex-types-for-mail-contacts-calendar.md#ResponseStatus) | 
 [TimeConstraint](..\api\complex-types-for-mail-contacts-calendar.md#TimeConstraint) (Preview) |  [Zeitrahmen](..\api\complex-types-for-mail-contacts-calendar.md#TimeSlot) (Vorschau) |  [Zeitstempel](..\api\complex-types-for-mail-contacts-calendar.md#TimeStamp) (Vorschau)    
 
 
 **Abfrageparametern OData:** &nbsp; [$search](..\api\complex-types-for-mail-contacts-calendar.md#Search) | 
 [$filter](..\api\complex-types-for-mail-contacts-calendar.md#Filter) | [$select](..\api\complex-types-for-mail-contacts-calendar.md#Select) | 
 [$orderby](..\api\complex-types-for-mail-contacts-calendar.md#OrderBy) | [$top und $skip](..\api\complex-types-for-mail-contacts-calendar.md#TopSkip)  | 
 $erweitern | [$count](..\api\complex-types-for-mail-contacts-calendar.md#Count)   

<a name="bk_notify"> </a>

##<a name="outlook-notifications"></a>Outlook-Benachrichtigungen

[Pushbenachrichtigungen API](../api/notify-rest-operations.md)

[Streaming Benachrichtigungen API](../api/notify-streaming-rest-operations.md) (Vorschau)


<a name="bk_photo"> </a>

##<a name="outlook-user-photo"></a>Outlook-benutzerfoto

[Benutzerfoto API](../api/photo-rest-operations.md)
 

<a name="bk_discovery"> </a>

##<a name="discovery-service"></a>Suchdienst

[Discovery-Dienst-API](..\api\discovery-service-rest-operations.md)

[Anfängliches anmelden](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsInitialsignin) |
 [Discover bestimmte Dienste](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsDiscoverspecificservices) | [Hier erfahren Sie, welche Dienste erkannt werden.](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsLearnwhatservicesarediscoverable)


<a name="bk_files"> </a>

##<a name="files"></a>Dateien

[OneDrive-API](https://dev.onedrive.com/)


<a name="bk_video"> </a>

##<a name="video"></a>Video 

[Video-API](../api/video-rest-operations.md)

**Video Portal:** &nbsp;  
   [Informationen abrufen](..\api\video-rest-operations.md#GetPortalInformation)
  
**Kanäle:** &nbsp;  
   [Informationen abrufen](..\api\video-rest-operations.md#GetChannelsInfo) 
  
**Video-Informationen:** &nbsp;  
   [Abrufen](..\api\video-rest-operations.md#GetVideoInfo) | [video-Metadaten aktualisieren](..\api\video-rest-operations.md#UpdateVideo) 
  
**Videos:** &nbsp;  
   [Hochladen](..\api\video-rest-operations.md#UploadVideos) | [Löschen](..\api\video-rest-operations.md#DeleteVideos) 

##<a name="api-resource-and-service-endpoints-of-office-365-operated-by-21vianet"></a>API-Ressource und ein Service Endpoints von Office 365 handelt, das von 21Vianet
[API-Endpunkten von Office 365 handelt, das von 21Vianet](..\api\o365-china-endpoints.md)

##<a name="office-365-management-apis"></a>APIs für die Verwaltung von Office 365
[Erste Schritte](https://msdn.microsoft.com/library/office/dn707383.aspx) | [Communications-Dienst-API (Preview)](https://msdn.microsoft.com/EN-US/library/dn707386.aspx) | [Management-API-Referenz (Preview)](https://msdn.microsoft.com/library/office/mt227394.aspx) | [-Berichterstattungswebdienst](https://msdn.microsoft.com/en-us/library/office/jj984325.aspx) 

##<a name="additional-resources"></a>Weitere Ressourcen

###<a name="api-sandbox"></a>Sandkasten-API
[Erkunden Sie die Office 365-APIs in dieser interaktiven Konsole](http://apisandbox.msdn.microsoft.com/)

###<a name="rest-api-response-status-codes"></a>REST-API Antwortcodes status

[HTTP-Antwortstatuscodes](..\howto\http-response-status-codes.md)


<<<<<<< KOPF
<!--
**Get started:** &nbsp; <a href="setup-development-environment?aspnet"> ASP.NET MVC apps </a> | <a href="setup-development-environment?javascript"> JavaScript web apps </a> | <a href="setup-development-environment?iOS"> iOS </a> | <a href="setup-development-environment?android"> Android </a>
-->


<a name="get-started-nbsp-aspnet-mvc-appshowtogetting-started-office-365-apismdaspnet-javascript-web-appshowtogetting-started-office-365-apismdjavascript-ioshowtogetting-started-office-365-apismdios-androidhowtogetting-started-office-365-apismdandroid"></a>**Steigen:** &nbsp; [ASP.NET MVC-apps](..\howto\getting-started-Office-365-APIs.md?aspnet) | [JavaScript Web apps](..\howto\getting-started-Office-365-APIs.md?javascript) | [iOS](..\howto\getting-started-Office-365-APIs.md?iOS) | [Android](..\howto\getting-started-Office-365-APIs.md?android)  
=======
###<a name="office-365-platform-overview"></a>Office 365-Plattform (Übersicht)
>>>>>>> Staging

[Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md) | [Einrichten Ihrer Entwicklungsumgebung für Office 365](..\howTo\setup-development-environment.md) 

[Erste Schritte mit Office 365APIs](..\howto\getting-started-Office-365-APIs.md) 

###<a name="office-365-permission-scopes"></a>Office 365-Berechtigungsbereiche
[Details zu allen berechtigungsbereiche für Office 365](..\howto\application-manifest.md)

###<a name="microsoft-partner-center-api-reference"></a>Microsoft Partner Center-API-Referenz
Partner können mithilfe der [REST-API für CSP Commerce](https://msdn.microsoft.com/en-us/library/partnercenter/dn974944.aspx) Kundenkonten erstellen, verwalten Customer-Benutzerprofilen in die Microsoft-Commerce-Webplattform, und erwerben und Verwalten von Aufträgen und Abonnements von Microsoft-Produkten für ihre Kunden. 



