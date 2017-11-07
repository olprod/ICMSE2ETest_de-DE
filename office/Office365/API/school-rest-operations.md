MS. TocTitle: Schulen REST-API-Referenz Titel: Schulen REST-API-Referenz Beschreibung: Verweisen auf die Interaktion mit der Schulen REST-API, die Zugriff auf die Schulen in einem Office 365 Education-Mandanten bereitstellt.
MS. ContentId: 35003e02-c4b1-4702-9d86-b6a7718e9fa8 ms.topic: Verweis (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]




# <a name="schools-rest-api-reference"></a>Schulen REST-API-Referenz
    
 _**Gilt für:** Office 365-Schulung_
<p class="previewnote">In dieser Dokumentation behandelt Features, die derzeit in der Vorschau werden. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>


<a name="Overview"> </a>Office 365 Education-APIs Hilfe Extrahieren von Daten aus Ihrem Office 365-Mandanten zu dem von Microsoft Schule Daten Sync in der Cloud synchronisiert wurden. Diese Ergebnisse liefern Informationen zu schulen, Abschnitte, Lehrer, Schüler und konferenzlisten. Schulen REST-API bietet Zugriff auf Schule Entitäten in Office 365 für Bildungseinrichtungen Mandanten.

Die API basiert auf Microsoft Azure Active Directory und OAuth zum [Authentifizieren von Anwendungen an](..\howto\common-app-authentication-tasks.md).
 
Um die Schulen REST-API in Ihrer Anwendung zuzugreifen, müssen Sie [ihn in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)registrieren.
Sie müssen auch verwalten Authentifizierungstoken als auch die richtige URL und Abfragen entsprechend Ihren Anforderungen zu erstellen. Die unten stehenden Beispiele können zur Unterstützung bei der Erstellung von den Abfragen verwendet werden.

<!-- Add Extension Properties and Data-Model-->

## <a name="all-schools-rest-api-operations"></a>Alle Schulen REST-API-Vorgänge

<a name="SchoolOperations"></a> Schulen werden als [Einheiten](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx) in Azure Active Directory dargestellt. Sie können die Schulen, die in einem Mandanten verfügbar sind abrufen und möchten auch die Abschnitte, Schüler und Lehrer, die jede Entität Schule gehören.


[Schulen abrufen](#GetSchools) | [Abschnitte innerhalb einer School Get](#GetSchoolSections) | [Schüler innerhalb einer Schule](#GetSchoolStudents) | [Lehrer innerhalb einer Schule abrufen](#GetSchoolTeachers) 


## <a name="use-the-schools-rest-api"></a>Verwenden Sie die Schulen REST-API

Zur Interaktion mit der REST-API Schulen, senden Sie HTTP GET-Anfragen.

Alle Schulen REST-API-Anforderungen mithilfe der folgenden Stamm-URL:

`https://graph.windows.net/{tenant_id}/administrativeUnits`

`{tenant_id}`ist die eindeutige ID oder den Mandanten Azure Active Directory-Domäne. Sie können die Tenant_id in einer der folgenden Methoden angeben:
- Die Objekt-ID (GUID) des Mandanten. Beispiel: `https://graph.windows.net/95b43ae0-0554-4cc5-8c22-fe219dc31156/`.
- Einen überprüften Domänennamen für den Mandanten; Beispiel: `https://graph.windows.net/contoso.onmicrosoft.com/`.
- Die `myOrganization` Alias. Dieses Alias aufgelöst wird, die dem Mandanten des (basierend auf dem Bearer Token in der Anforderung gesendet); angemeldeten Benutzers beispielsweise `https://graph.windows.net/myorganization/`. 

In der folgenden Beispiele verwenden wir die `tenant_id = 95b43ae0-0554-4cc5-8c22-fe219dc31156`.   

Schulen werden als Einheiten in Azure Active Directory dargestellt. Extension-Attribute auf die administrativen Einheiten fügen Education-spezifische Informationen hinzu.  
Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade` Attribut enthält die höchste Ebene der Klasse innerhalb der Schule.

**Hinweis** Alle Anforderungen sind erforderlich zum Angeben einer `api-version` in der URL-Abfragezeichenfolge. Der REST-API Schulen erfordert Version `beta`. Beispiel: `https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta`.   


## <a name="school-attributes"></a>Schule Attribute

Die Beschreibung der Attribute, die auf die Informationen über die Schule erkennen sind: [Schule Attribute](education-rest-attributes.md#SchoolAttributes)

****

<a name="GetSchools"> </a>
##<a name="get-schools"></a>Abrufen von Schulen

Sie können alle Schulen erhalten möchten, rufen Sie eine einzelne Schule indem dessen `object_id`, oder rufen Sie eine Auflistung von Schulen, die der Abfragefilter entsprechen.

<a name="GetAllSchools"> </a>
###<a name="get-all-schools"></a>Abrufen Sie aller Schulen

Rufen Sie alle Schulen, die in den Mandanten Azure Active Directory vorhanden sein.

```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta&$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'School'
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|

```REST
[!INCLUDE [schools_api_get_schools.json](./_data/schools_api_get_schools.json)]
```

 **Antworttyp**

Eine Auflistung von Schule Entitäten.


****


<a name="GetSchool"> </a>
###<a name="get-a-school"></a>Abrufen einer Schule

Abrufen eine Schule unter Verwendung der `object_id`.

```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}?api-version=beta
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID der Schule administrative Einheit in Azure Active Directory.|   

```REST
[!INCLUDE [schools_api_get_school_by_id.json](./_data/schools_api_get_school_by_id.json)]
```

 **Antworttyp**

Die angeforderte Schule Entität.


****

<a name="GetSchoolSections"> </a>
##<a name="get-sections-within-a-school"></a>Abschnitte innerhalb einer School Get

Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)in Azure Active Directory dargestellt. Extension-Attribute für die unified Gruppen hinzufügen im Abschnitt spezifische Informationen. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_CourseName` Attribut enthält den Kursnamen für den Abschnitt.

Sie können Abschnitte für eine bestimmte Schule abrufen, indem Sie Abfragen für Gruppen anhand ihrer Id Schule mit der `extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType` Attribut und die `extension_fe2174665583431c953114ff7268b7b3_Education_SyncSource_SchoolId` Attribut in der Abfrage zusammen.


```no-highlight
GET https://graph.windows.net/{tenant_id}/groups?api-version=1.5
        &$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'Section'%20
        and%20extension_fe2174665583431c953114ff7268b7b3_Education_SyncSource_SchoolId%20eq%20'{school_id}'
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|school_id|string|Die ID der Schule in Schule Informationen System (SIS).|   


```REST
[!INCLUDE [schools_api_get_sections_by_school_id.json](./_data/schools_api_get_sections_by_school_id.json)]
```

 **Antworttyp**

Eine Auflistung von Entitäten Abschnitt.

**** 

<a name="GetSchoolStudents"> </a>
##<a name="get-students-within-a-school"></a>Schüler innerhalb einer Schule

Studenten werden als Benutzer in Azure Active Directory dargestellt. Extension-Attribute auf die Benutzer fügen Student spezifische Informationen hinzu. Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_Grade` Attribut enthält die Student Note-Ebene.  

Sie können Studenten in einer bestimmten Schule, abrufen, indem Abrufen der Member der Schule administrative Einheit und Benutzer aus der resultierenden Auflistung innerhalb der Anwendung nicht Student herausfiltern.

###<a name="get-school-members"></a>Rufen Sie Schule Objektmember ab
```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}/members?api-version=beta
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID der Schule administrative Einheit in Azure Active Directory.|   


```REST
[!INCLUDE [schools_api_get_students_by_school_id.json](./_data/schools_api_get_students_by_school_id.json)]
```

 **Antworttyp**

Eine Auflistung von Benutzern.

###<a name="find-students"></a>Suchen Sie nach Studenten

Eine Auflistung von Benutzern möglicherweise Studenten, Lehrer und nicht Education-Benutzer (beispielsweise Verwaltungsmitarbeiter) enthalten. Sie können innerhalb der Anwendung die Auflistung nach unten zu Studenten filtern. Suchen Sie nach der `Education_ObjectType` Extension-Attribut gleich `Student`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

**** 

<a name="GetSchoolTeachers"> </a>
##<a name="get-teachers-within-a-school"></a>Erhalten Sie Lehrer innerhalb einer Schule

Lehrer werden als Benutzer in Azure Active Directory dargestellt. Extension-Attribute auf die Benutzer fügen Lehrer spezifische Informationen hinzu. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_TeacherNumber` -Attribut des Lehrers Lehrer Zahl enthält. 

Sie können Lehrer in einer bestimmten Schule abrufen, indem Abrufen der Member der Schule administrative Einheit und Benutzer aus der resultierenden Auflistung innerhalb der Anwendung nicht Lehrer herausfiltern.

###<a name="get-school-members"></a>Rufen Sie Schule Objektmember ab
```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}/members?api-version=beta
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID der Schule administrative Einheit in Azure Active Directory.|   


```REST
[!INCLUDE [schools_api_get_teachers_by_school_id.json](./_data/schools_api_get_teachers_by_school_id.json)]
```

 **Antworttyp**

Eine Auflistung von Benutzern.

###<a name="find-teachers"></a>Suchen Sie nach Lehrer

Eine Auflistung von Benutzern möglicherweise Studenten, Lehrer und nicht Education-Benutzer (beispielsweise Verwaltungsmitarbeiter) enthalten. Sie können die Auflistung nach unten zu Lehrer innerhalb der Anwendung zu filtern. Suchen Sie nach der `Education_ObjectType` Extension-Attribut gleich `Teacher`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Teacher'
```


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Einige der anderen Education-bezogene Ressourcen, denen Sie interessiert sein könnten

- Verwenden der [Abschnitte Rest Vorgänge](..\api\section-rest-operations.md) im Abschnitt Zugriffsinformationen

- Student Zugriffsinformationen, die mit der [Studenten-Rest-Vorgänge](..\api\student-rest-operations.md)

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
    
