MS. TocTitle: Abschnitte REST-API-Referenz für Titel: Abschnitte REST-API-Referenz Beschreibung: Verweisen auf die Interaktion mit der REST-API Abschnitte, die Zugriff auf den Abschnitten in einem Office 365 Education-Mandanten bereitstellt.
MS. ContentId: 3805c218-e0c7-48e9-b458-448563ff7ae4 ms.topic: Verweis (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]


# <a name="sections-rest-api-reference"></a>Abschnitte REST-API-Referenz
    
 _**Gilt für:** Office 365-Schulung_
<p class="previewnote">In dieser Dokumentation behandelt Features, die derzeit in der Vorschau werden. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>



<a name="Overview"> </a>Office 365 Education-APIs Hilfe Extrahieren von Daten aus Ihrem Office 365-Mandanten zu dem von Microsoft Schule Daten Sync in der Cloud synchronisiert wurden. Diese Ergebnisse liefern Informationen zu schulen, Abschnitte, Lehrer, Schüler und konferenzlisten. Jede Klasse in der School wird als Abschnitt dargestellt. Die Abschnitte REST-API bietet Zugriff auf Abschnitt Entitäten in Office 365 für Bildungseinrichtungen Mandanten.

Die API basiert auf Microsoft Azure Active Directory und OAuth zum [Authentifizieren von Anwendungen an](..\howto\common-app-authentication-tasks.md).
 
Zugriff auf die Abschnitte REST-API aus Ihrer Anwendung müssen Sie [ihn in Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)registrieren.
Sie müssen auch verwalten Authentifizierungstoken als auch die richtige URL und Abfragen entsprechend Ihren Anforderungen zu erstellen. Die unten stehenden Beispiele können zur Unterstützung bei der Erstellung von den Abfragen verwendet werden.

<!-- Add Extension Properties and Data-Model-->

## <a name="all-sections-rest-api-operations"></a>Alle Abschnitte REST-API-Vorgänge

<a name="SectionOperations"></a> Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations) in Azure Active Directory dargestellt. Sie können in den Abschnitten abrufen, die in einem Mandanten, der Studenten und Lehrer, die Teil der einzelnen Abschnitte sind und Schule Details, denen zu ein Abschnitt gehört verfügbar sind.


[Abschnitten erhalten](#GetSections) | [Abrufen eines Abschnitts Schule](#GetSectionsSchool) | [Schüler innerhalb eines Abschnitts](#GetSectionStudents) | [Abrufen Lehrer innerhalb eines Abschnitts](#GetSectionTeachers) 


## <a name="use-the-sections-rest-api"></a>Verwenden Sie in den Abschnitten REST-API

Zur Interaktion mit der REST-API von Abschnitten, senden Sie HTTP GET-Anfragen.

Alle Abschnitte REST-API-Anforderungen mithilfe der folgenden Stamm-URL:

`https://graph.windows.net/{tenant_id}/groups`

`{tenant_id}`ist die eindeutige ID oder den Mandanten Azure Active Directory-Domäne. Sie können die Tenant_id in einer der folgenden Methoden angeben:
- Die Objekt-ID (GUID) des Mandanten. Beispiel: `https://graph.windows.net/95b43ae0-0554-4cc5-8c22-fe219dc31156/`.
- Einen überprüften Domänennamen für den Mandanten; Beispiel: `https://graph.windows.net/contoso.onmicrosoft.com/`.
- Die `myOrganization` Alias. Dieses Alias aufgelöst wird, die dem Mandanten des (basierend auf dem Bearer Token in der Anforderung gesendet); angemeldeten Benutzers beispielsweise `https://graph.windows.net/myorganization/`. 

In der folgenden Beispiele verwenden wir die `tenant_id = 95b43ae0-0554-4cc5-8c22-fe219dc31156`.

Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)in Azure Active Directory dargestellt. Extension-Attribute für die unified Gruppen hinzufügen Education-spezifische Informationen.  
Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_CourseNumber` Attribut enthält die Anzahl der Kurs eines Abschnitts.

**Hinweis** Alle Anforderungen sind erforderlich zum Angeben einer `api-version` in der URL-Abfragezeichenfolge. Die Abschnitte REST-API erfordert Version 1.5 oder höher, mit Ausnahme eine Schule eines Abschnitts erfordern die Version als erste `beta`. Beispiel: `https://graph.windows.net/{tenant_id}/groups?api-version=1.5`.   

## <a name="section-attributes"></a>Abschnittsattribute

Die Beschreibung der Attribute, die Hilfe bei der Identifizierung der Informationen im Abschnitt zur sind: [Abschnittsattribute](education-rest-attributes.md#SectionAttributes)

****

<a name="GetSections"> </a>
##<a name="get-sections"></a>Abrufen von Abschnitten

Sie können allen Abschnitten erhalten möchten, abrufen, indem Sie einen einzelnen Abschnitte seine `object_id`; oder Abrufen einer Auflistung der Abschnitte, die der Abfragefilter entsprechen.

<a name="GetAllSections"> </a>
###<a name="get-all-sections"></a>Abrufen Sie aller Abschnitte

Rufen Sie alle Abschnitte, die in den Mandanten Azure Active Directory vorhanden sind.

```no-highlight
GET https://graph.windows.net/{tenant_id}/groups?api-version=1.5&$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'Section'
```

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|

```REST
[!INCLUDE [sections_api_get_sections.json](./_data/sections_api_get_sections.json)]
```

 **Antworttyp**

Eine Auflistung von Entitäten Abschnitt.


****


<a name="GetSection"> </a>
###<a name="get-a-section"></a>Abrufen eines Abschnitts

Abrufen ein Abschnitts mithilfe der `object_id`.

```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}?api-version=1.5
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID der Abschnittsgruppe im in Azure Active Directory.|   


```REST
[!INCLUDE [sections_api_get_section_by_id.json](./_data/sections_api_get_section_by_id.json)]
```

 **Antworttyp**

Die angeforderte Abschnitt Entität.


****

<a name="GetSectionsSchool"> </a>
##<a name="get-school-of-a-section"></a>Abrufen eines Abschnitts school

Schulen werden als Einheiten in Azure Active Directory dargestellt. Extension-Attribute auf diesen administrativen Einheiten fügen School-spezifische Informationen hinzu. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade` Attribut die höchste Qualität für diese Schule enthält.

Sie erhalten die Schule, ein Abschnitt für administrative Einheiten von Abfragen zugeordnet ist, die `SchoolId` Eigenschaft von abgerufen `extension_fe2174665583431c953114ff7268b7b3_Education_SchoolId` Antwort von [einem Abschnitt erhalten möchten](#GetSection).


```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta
        &$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'School'%20
        and%20extension_fe2174665583431c953114ff7268b7b3_Education_SchoolId%20eq%20'{school_id}'
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|school_id|string|Die ID der Schule in Schule Informationen System (SIS).|   


```REST
[!INCLUDE [sections_api_get_school_for_section_id.json](./_data/sections_api_get_school_for_section_id.json)]
```

 **Antworttyp**

Eine Schule Entität.

**** 

<a name="GetSectionStudents"> </a>
##<a name="get-students-within-a-section"></a>Abrufen von Kursteilnehmer innerhalb eines Abschnitts

Studenten werden als Benutzer in Azure Active Directory dargestellt. Erweiterung Benutzerattribute fügen Student-spezifische Informationen hinzu. Beispielsweise die `extension_fe2174665583431c953114ff7268b7b3_Education_Grade` Attribut enthält die Student Note-Ebene.  

Sie können Studenten in einem bestimmten Abschnitt, abrufen, indem die Mitglieder der unified Gruppe im Abschnitt erste und Benutzer aus der resultierenden Auflistung innerhalb der Anwendung nicht Student herausfiltern.

###<a name="get-section-members"></a>Rufen Sie im Abschnitt Objektmember ab
```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}/members?api-version=1.5
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID der Abschnittsgruppe im in Azure Active Directory.|   


```REST
[!INCLUDE [sections_api_get_students_by_section_id.json](./_data/sections_api_get_students_by_section_id.json)]
```

 **Antworttyp**

Eine Auflistung von Benutzern.

###<a name="find-students"></a>Suchen Sie nach Studenten

Eine Auflistung von Benutzern möglicherweise Studenten, Lehrer und nicht Education-Benutzer (beispielsweise Verwaltungsmitarbeiter) enthalten. Sie können eine Auflistung nach unten zu Studenten nur innerhalb der Anwendung filtern. Abfrage für die `Education_ObjectType` Extension-Attribut gleich `Student`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

**** 

<a name="GetSectionTeachers"> </a>
##<a name="get-teachers-within-a-section"></a>Abrufen von Lehrer innerhalb eines Abschnitts

Lehrer werden als Benutzer in Azure Active Directory dargestellt. Erweiterung Benutzerattribute fügen Lehrer-spezifische Informationen hinzu. Beispielsweise das `extension_fe2174665583431c953114ff7268b7b3_Education_TeacherNumber` -Attribut des Lehrers Lehrer Zahl enthält. 

Sie können Lehrer in einem bestimmten Abschnitt, abrufen, indem Abrufen der Member der unified Gruppe im Abschnitt und Benutzer aus der resultierenden Auflistung, in der Anwendung nicht Lehrer herausfiltern.

###<a name="get-section-members"></a>Rufen Sie im Abschnitt Objektmember ab
```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}/members?api-version=1.5
```


|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|tenant_id|string|Der Azure Active Directory-Mandanten-ID oder Domänennamen.|
|object_id|string|Die Objekt-ID, die in Azure Active Directory-Gruppe.|   


```REST
[!INCLUDE [sections_api_get_teachers_by_section_id.json](./_data/sections_api_get_teachers_by_section_id.json)]
```

 **Antworttyp**

Eine Auflistung von Benutzern.

###<a name="find-teachers"></a>Suchen Sie nach Lehrer

Eine Auflistung von Benutzern möglicherweise Studenten, Lehrer und nicht Education-Benutzer (beispielsweise Verwaltungsmitarbeiter) enthalten. Sie können in der Anwendung die Auflistung nach unten zu nur Lehrer, filtern. Abfrage für die `Education_ObjectType` Extension-Attribut gleich `Teacher`.

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Teacher'
```


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Einige der anderen Education-bezogene Ressourcen, denen Sie interessiert sein könnten

- Verwenden der [Schulen Rest Vorgänge](..\api\school-rest-operations.md) Zugriff Schule Informationen

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
    
