MS. TocTitle: Lehrer REST-API-Referenz für Titel: Lehrer REST-API-Referenz Beschreibung: Verweisen auf die Interaktion mit der REST-API Lehrer, die Zugriff auf die Lehrer in einem Office 365 Education-Mandanten bereitstellt.
MS. ContentId: 80124eb7-1af4-44d3-94d4-ec60afe0f254 ms.topic: Verweis (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="teachers-rest-api-reference"></a>Lehrer REST-API-Referenz
    
 _**Gilt für:** Office 365-Schulung_
<p class="previewnote">Diese Dokumentation behandelt Features, die derzeit in der Vorschau enthalten sind. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>


<a name="Overview"> </a>Office 365 Education-APIs Hilfe Extrahieren von Daten aus Ihrem Office 365-Mandanten zu dem von Microsoft Schule Daten Sync in der Cloud synchronisiert wurden. Diese Ergebnisse liefern Informationen zu schulen, Abschnitte, Lehrer, Schüler und Teilnehmerliste Informationen. Lehrer REST-API bietet Zugriff auf Lehrer Entitäten in Office 365-Schulung.

Die API basiert auf Microsoft Azure Active Directory und OAuth zum [Authentifizieren der Anwendung Anforderungen](..\howto\common-app-authentication-tasks.md).
 
Um die Lehrer REST-API in Ihrer Anwendung zuzugreifen, müssen Sie [ihn in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)registrieren.
Sie müssen auch Authentifizierungstoken verwalten sowie die richtige URL und Abfragen entsprechend Ihren Anforderungen zu erstellen. Die unten stehenden Beispiele können zur Unterstützung bei der Erstellung von den Abfragen verwendet werden.

<!-- Add Extension Properties and Data-Model-->

## <a name="all-teachers-rest-api-operations"></a>Alle Lehrer REST-API-Vorgänge

<a name="TeacherOperations"></a> Lehrer werden als Benutzer in Azure Active Directory dargestellt. Sie erhalten die Attribute der aktuellen Lehrer, die angemeldet ist, und die Schule und Abschnitte der Lehrer ist ein Mitglied.


[Abrufen des aktuellen Benutzers](#GetCurrentUser) | [Schule der Lehrer abrufen](#GetTeacherSchool) | [Abschnitte der Lehrer abrufen](#GetTeacherSections) 


## <a name="use-the-teachers-rest-api"></a>Verwenden Sie die Lehrer-REST-API

Zur Interaktion mit der REST-API Lehrer, senden Sie HTTP GET-Anfragen.

Ist der angemeldete Benutzer Lehrer, verwenden alle Lehrer REST API Anforderungen folgenden Stamm-URL:

`https://graph.windows.net/me`

Lehrer werden als Benutzer in Azure Active Directory dargestellt. Extension-Attribute auf die Benutzer fügen Lehrer-spezifische Informationen hinzu.  
Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_TeacherNumber` Attribut enthält die Lehrer Anzahl der Lehrer.

**Hinweis** Alle Anforderungen sind erforderlich, um das Angeben eines `api-version` im URL-Abfragezeichenfolge. Lehrer REST-API ist Version 1.5 oder höher erforderlich. Beispiel: `https://graph.windows.net/me?api-version=1.5`.   

## <a name="teacher-attributes"></a>Lehrer-Attribute

Die Beschreibung der Attribute, die Informationen zu der Schulungsleiter erkennen an: [Lehrer Attribute](education-rest-attributes.md#TeacherAttributes)

****

<a name="GetCurrentUser"> </a>
##<a name="get-current-user"></a>Abrufen des aktuellen Benutzers

Sie können die gegenwärtig angemeldeten Benutzer, und überprüfen Sie, wenn der Benutzer einen Lehrer ist abrufen.

```no-highlight
GET https://graph.windows.net/me?api-version=1.5
```

```REST
[!INCLUDE [teachers_api_get_current_user.json](./_data/teachers_api_get_current_user.json)]
```

 **Antworttyp**

Der aktuelle Benutzer angemeldet.

###<a name="check-if-teacher"></a>Überprüfen Sie, ob Lehrer

Eine aktuelle angemeldeten Benutzer möglicherweise eine Student, Lehrer oder nicht Education-Benutzer (beispielsweise Verwaltungsmitarbeiter). Sie können überprüfen, ob der Benutzer einen Lehrer innerhalb der Anwendung ist. Suchen Sie nach der `Education_ObjectType` Extension-Attribut gleich `Teacher`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Teacher'
```

****

<a name="GetTeacherSchool"> </a>
##<a name="get-school-of-a-teacher"></a>Abrufen von Lehrer school

Schulen werden als [Einheiten](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx)in Azure Active Directory dargestellt. Extension-Attribute auf diesen administrativen Einheiten fügen School-spezifische Informationen hinzu. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade` Attribut enthält den höchsten Note für diese Schule.

Sie können die Schule eines Lehrers angemeldete Benutzer abrufen, indem Abrufen der Mitgliedschaft, Lehrer und Filtern Sie Sie anschließend auf die `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'` und`objectType == 'AdministrativeUnit'`

###<a name="get-teacher-membership"></a>Lehrer Mitgliedschaft abrufen

Sie können die Mitgliedschaft in der Schulungsleiter angemeldete Benutzer mithilfe der folgenden Abfrage abrufen.


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```


 **Antworttyp**

Die Antwort enthält mehrere Gruppen, DirectoryRoles und/oder AdministrativeUnits, die die Lehrer ein Mitglied ist.

###<a name="filter-for-school"></a>Filter für School

Sie können Schule der Lehrer abrufen, indem Sie die Filterung auf `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'` und `objectType == 'AdministrativeUnit'`.


**** 

<a name="GetTeacherSection"> </a>
##<a name="get-section-of-a-teacher"></a>Erhalten Sie im Abschnitt Lehrer

Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)in Azure Active Directory dargestellt. Extension-Attribute für die Gruppen unified hinzufügen im Abschnitt-spezifische Informationen an. Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_CourseName` Attribut enthält den Kursnamen für den Abschnitt.

###<a name="get-teacher-membership"></a>Lehrer Mitgliedschaft abrufen

Sie können die Mitgliedschaft in der Schulungsleiter mithilfe der folgenden Abfrage abrufen.


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```

 **Antworttyp**

Die Antwort enthält mehrere Gruppen, DirectoryRoles und/oder AdministrativeUnits, das die Lehrer ein Mitglied ist.

###<a name="filter-for-section"></a>Filter für Abschnitt

Sie können im Abschnitt Lehrer abrufen, indem Sie Filter auf `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Section'` und `objectType == 'Group'`.

**** 

<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Einige der anderen Education-bezogene Ressourcen, denen Sie interessiert sein könnten

- Verwenden der [Schulen Rest Vorgänge](..\api\school-rest-operations.md) Access Schule Informationen

- Abschnitt Zugriffsinformationen, die mit den [Abschnitten Rest-Vorgänge](..\api\section-rest-operations.md)

- Verwenden der [Studenten Rest Vorgänge](..\api\student-rest-operations.md) Student Zugriffsinformationen

- Attribut Beschreibungen sind verfügbar unter [Education-Attribute](..\api\education-rest-attributes.md)


Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelte Problem zu.


- Sind Sie bereit für den Einstieg? Starten Sie, indem [das Einrichten Ihrer Umgebung](..\howto\setup-development-environment.md), und checken Sie unsere [ersten app exemplarischen Vorgehensweise](..\howto\getting-started-Office-365-APIs.md).

- Verwenden Sie die Office 365-APIs verwenden die interaktive [API Sandkasten](http://apisandbox.msdn.microsoft.com/).
    
- Soll Beispiele werden? [Wir haben sie](..\howto\starter-projects-and-code-samples.md).
    

Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Übersicht über die bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)
    
- [Office 365-app-Authentifizierung und Ressource Autorisierung](..\howto\common-app-authentication-tasks.md)
    
- [Registrieren Sie Ihre app mit Azure AD manuell, sodass es auf Office 365-APIs zugreifen können](..\howto\add-common-consent-manually.md)
  
- [Mail API-Referenz](..\api\mail-rest-operations.md)
  
- [Kalender-API-Referenz](..\api\calendar-rest-operations.md)

- [Dateien API-Referenz](..\api\files-rest-operations.md)

- [Ermittlung REST-Dienst-API-Referenzen für Vorgänge](..\api\discovery-service-rest-operations.md)

- [Resource-Referenz für die e-Mail-Nachrichten, Kalender und Kontakte REST-APIs](..\api\complex-types-for-mail-contacts-calendar.md)
    
