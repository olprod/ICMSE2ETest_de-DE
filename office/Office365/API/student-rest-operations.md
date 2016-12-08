MS. TocTitle: Studenten REST-API-Referenz Titel: Studenten REST-API-Referenz Beschreibung: Verweisen auf die Interaktion mit der Studenten-REST-API, die Zugriff auf die Teilnehmer in einem Office 365 Education-Mandanten bereitstellt.
MS. ContentId: aec1e56a-081d-4214-b441-9039b8341a9e ms.topic: Verweis (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="students-rest-api-reference"></a>Kursteilnehmer REST API-Referenz
    
 _**Gilt für:** Office 365-Schulung_
<p class="previewnote">In dieser Dokumentation behandelt Features, die derzeit in der Vorschau werden. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>


<a name="Overview"> </a>Office 365 Education-APIs Hilfe Extrahieren von Daten aus Ihrem Office 365-Mandanten, der von Microsoft Schule Data Sync in der Cloud synchronisiert wurden. Diese Ergebnisse enthalten Informationen zu schulen, Abschnitte, Lehrer, Schüler und Teilnehmerliste Informationen. Der Studenten-REST-API bietet Zugriff auf Student Entitäten in Office 365 für Bildungseinrichtungen Mandanten.

Die API basiert auf Microsoft Azure Active Directory und OAuth zum [Authentifizieren von Anwendungen an](..\howto\common-app-authentication-tasks.md).
 
Um die Kursteilnehmer REST API in Ihre Anwendung zuzugreifen, müssen Sie [ihn in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)registriert.
Sie müssen auch verwalten Authentifizierungstoken als auch die richtige URL und Abfragen entsprechend Ihren Anforderungen zu erstellen. Die unten stehenden Beispiele können zur Unterstützung bei der Erstellung von den Abfragen verwendet werden.

<!-- Add Extension Properties and Data-Model-->

## <a name="all-students-rest-api-operations"></a>Alle Studenten REST-API-Vorgänge

<a name="StudentOperations"></a> Kursteilnehmer als Benutzer in Azure Active Directory dargestellt werden. Sie können die Informationen, die angemeldet ist, im aktuellen Student rufen Sie und auch die Schule und Abschnitte, denen der Student gehört.


[Abrufen des aktuellen Benutzers](#GetCurrentUser) | [Schule der einen Schüler abrufen](#GetStudentSchool) | [Abschnitte einen Schüler erhalten möchten](#GetStudentSections) 


## <a name="use-the-students-rest-api"></a>Verwenden der Studenten-REST-API

Zur Interaktion mit der Studenten-REST-API, senden Sie HTTP GET-Anfragen.

Wenn der angemeldete Benutzer einen Schüler ist, verwenden alle Studenten REST-API-Anforderungen die folgenden Stamm-URL:

`https://graph.windows.net/me`

Studenten werden als Benutzer in Azure Active Directory dargestellt. Extension-Attribute auf die Benutzer fügen Student-spezifische Informationen hinzu.  
Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_Grade` Attribut enthält die Qualität des Studenten.

**Hinweis** Alle Anforderungen sind erforderlich zum Angeben einer `api-version` in der URL-Abfragezeichenfolge. Der Studenten-REST-API ist Version 1.5 oder höher erforderlich. Beispiel: `https://graph.windows.net/me?api-version=1.5`.   

## <a name="student-attributes"></a>Student-Attribute

Die Beschreibung der Attribute, die an die Informationen zu den Teilnehmern erkennen sind: [Student-Attribute](education-rest-attributes.md#StudentAttributes)

****

<a name="GetCurrentUser"> </a>
##<a name="get-current-user"></a>Abrufen des aktuellen Benutzers

Sie erhalten gegenwärtig angemeldeten Benutzer- und Kontrollkästchen, wenn der Benutzer einen Schüler ist.

```no-highlight
GET https://graph.windows.net/me?api-version=1.5
```

```REST
[!INCLUDE [students_api_get_current_user.json](./_data/students_api_get_current_user.json)]
```

 **Antworttyp**

Der aktuelle Benutzer angemeldet.

###<a name="check-if-student"></a>Überprüfen Sie, ob Kursteilnehmer

Eine aktuelle angemeldeten Benutzer möglicherweise eine Student, Lehrer oder nicht Education Benutzer (beispielsweise Verwaltungsmitarbeiter). Sie können überprüfen, ob der Benutzer einen Schüler innerhalb der Anwendung ist. Abfrage für die `Education_ObjectType` Extension-Attribut gleich `Student`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

****

<a name="GetStudentSchool"> </a>
##<a name="get-school-of-a-student"></a>Abrufen von Schule der einen Schüler

Schulen werden als [Einheiten](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx)in Azure Active Directory dargestellt. Extension-Attribute auf diesen administrativen Einheiten fügen School-spezifische Informationen hinzu. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade` Attribut die höchste Qualität für diese Schule enthält.

Sie können die Schule Student angemeldete Benutzer abrufen, indem Abrufen der Mitgliedschaft dieses Studenten und Filtern Sie Sie anschließend auf die `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'` und`objectType == 'AdministrativeUnit'`

###<a name="get-student-membership"></a>Abrufen der Student-Mitgliedschaft

Sie können die Mitgliedschaft in der Student angemeldete Benutzer mithilfe der folgenden Abfrage abrufen.


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```


 **Antworttyp**

Die Antwort enthält mehrere Gruppen, DirectoryRoles und/oder AdministrativeUnits ein, die der Student ein Mitglied ist.

###<a name="filter-for-school"></a>Filter für Schule

Sie können die Schule der einen Schüler abrufen, indem Sie Filterung anhand `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'` und `objectType == 'AdministrativeUnit'`.


**** 

<a name="GetStudentSection"> </a>
##<a name="get-section-of-a-student"></a>Erhalten Sie im Abschnitt einen Schüler

Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)in Azure Active Directory dargestellt. Extension-Attribute für die unified Gruppen hinzufügen im Abschnitt-spezifische Informationen. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_CourseName` Attribut enthält den Kursnamen für den Abschnitt.

###<a name="get-student-membership"></a>Abrufen der Student-Mitgliedschaft

Sie können die Mitgliedschaft in der Student mithilfe der folgenden Abfrage abrufen.


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```

 **Antworttyp**

Die Antwort enthält mehrere Gruppen, DirectoryRoles und/oder AdministrativeUnits aus, die der Student ein Mitglied ist.

###<a name="filter-for-section"></a>Filter für Abschnitt

Erhalten Sie einen Schüler Abschnitt Filterung anhand `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Section'` und `objectType == 'Group'`.

**** 

<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Einige der anderen Education-bezogene Ressourcen, denen Sie interessiert sein könnten

- Verwenden der [Schulen Rest Vorgänge](..\api\school-rest-operations.md) Zugriff Schule Informationen

- Verwenden der [Abschnitte Rest Vorgänge](..\api\section-rest-operations.md) im Abschnitt Zugriffsinformationen

- Verwenden der [Lehrer Rest Vorgänge](..\api\teacher-rest-operations.md) Lehrer Zugriffsinformationen 

- Attribut Beschreibungen sind verfügbar unter [Education-Attribute](..\api\education-rest-attributes.md)


Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelt.


- Sind Sie bereit für den Einstieg? Starten Sie, indem [das Einrichten Ihrer Umgebung](..\howto\setup-development-environment.md), und checken Sie unsere [ersten app exemplarischen Vorgehensweise](..\howto\getting-started-Office-365-APIs.md).

- Verwenden Sie die Office 365-APIs verwenden die interaktive [API Sandkasten](http://apisandbox.msdn.microsoft.com/)aus.
    
- Soll Beispiele werden? [Wir haben sie](..\howto\starter-projects-and-code-samples.md).
    

Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)
    
- [Office 365-app-Authentifizierung und Ressource Autorisierung](..\howto\common-app-authentication-tasks.md)
    
- [Registrieren Sie Ihre app mit Azure AD manuell, sodass es auf Office 365-APIs zugreifen können](..\howto\add-common-consent-manually.md)
  
- [Mail-API-Referenz](..\api\mail-rest-operations.md)
  
- [Kalender-API-Referenz](..\api\calendar-rest-operations.md)

- [Dateien API-Referenz](..\api\files-rest-operations.md)

- [Ermittlung REST-Dienst-API-Referenzen für Vorgänge](..\api\discovery-service-rest-operations.md)

- [Resource-Referenz für die e-Mail-Nachrichten, Kalender und Kontakte REST-APIs](..\api\complex-types-for-mail-contacts-calendar.md)
    
