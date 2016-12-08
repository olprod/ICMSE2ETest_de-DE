MS. TocTitle: Education Attribute Title: Education Attribute Beschreibung: Verweisen auf welche Attribute von Education-REST-APIs, die Zugriff auf die Schulen, Abschnitte, Schüler und Lehrer in einem Office 365 Education-Mandanten bietet auf Sie zukommt.
MS. ContentId: 1f51d3a9-0ab7-4654-a15d-689e0880ebfb ms.topic: Verweis (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="education-attributes"></a>Education-Attribute
    
 _**Gilt für:** Office 365-Schulung_
<p class="previewnote">Diese Dokumentation behandelt Features, die derzeit in der Vorschau enthalten sind. Informationen über das Arbeiten mit Features Preview finden Sie unter [Funktionen der Preview für Entwickler auf der Office 365-Plattform](..\howto\platform-development-preview-features-overview.md).</p>


<a name="Overview"> </a>Office 365 Education-APIs Hilfe Extrahieren von Daten aus Ihrem Office 365-Mandanten zu dem von Microsoft Schule Daten Sync in der Cloud synchronisiert wurden. Diese Ergebnisse liefern Informationen zu schulen, Abschnitte, Lehrer, Schüler und konferenzlisten.

[Attribute Schule](#SchoolAttributes) | [Abschnittsattribute](#SectionAttributes) | [Student Attribute](#StudentAttributes) | [Lehrer Attribute](#TeacherAttributes)

## <a name="school-attributes"></a>Schule Attribute

<a name="SchoolAttributes"></a> Schulen werden als [Einheiten](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx) in Azure Active Directory dargestellt. Sie können Abrufen die Schulen, die in einem Mandanten verfügbar sind und auch erhalten die Abschnitte, Schüler und Lehrer, die jede Schule Entität gehören.
Die systemeigene Attribute zusammen mit der Erweiterungsattribute auf administrative Einheit enthalten alle erforderliche Informationen zu der Schule. 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**Attribut**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|`displayName`|Erforderlich|Name der Schule|
|`{prefix}_SyncSource_SchoolId`|Erforderlich|Eindeutige ID der Schule von der SI zugewiesen wurde|
|`{prefix}_SchoolNumber`|Optional|ID, die in der Regel in Berichten angezeigt werden|
|`{prefix}_SchoolNationalCenterFor EducationStatisticsId`|Optional|Vom NCES zugeordnete-ID|
|`{prefix}_StateId`|Optional|ID des Berichterstattungsstruktur durch den Status zugewiesen|
|`{prefix}_LowestGrade`|Optional|Niedrigste Stufe der Schule {Pre-K, K, 1 bis 12, andere}|
|`{prefix}_HighestGrade`|Optional|Höchster Qualität der Schule {Pre-K, K, 1 bis 12, andere}|
|`{prefix}_SchoolPrincipalSyncSourceId`|Optional|SIS-ID des Prinzipals School|
|`{prefix}_SchoolPrincipalName`|Optional|Name des Prinzipals School|
|`{prefix}_SchoolPrincipalEmail`|Optional|E-Mail für den Prinzipal School|
|`{prefix}_Address`|Optional|Straße der Schule|
|`{prefix}_City`|Optional|Ort der Schule|
|`{prefix}_State`|Optional|Status der Schule|
|`{prefix}_Country`|Optional|Land des Berichterstattungsstruktur|
|`{prefix}_Zip`|Optional|Postleitzahl der Schule|
|`{prefix}_Phone`|Optional|Wenden Sie sich an der Schule Phone|
|`{prefix}_SchoolZone`|Optional|Region/Zone, der die Schule|
|`{prefix}_AnchorId`|Interne|Anker-ID wird intern verwendet, um jede Schule eindeutig zu identifizieren.|
|`{prefix}_ObjectType`|Interne|Der Objekttyp für eine Schule ist 'School'|
|`{prefix}_SyncSource`|Interne|Die Quelle der diese Informationen von der school|


**** 


## <a name="section-attributes"></a>Abschnittsattribute

<a name="SectionAttributes"></a> Abschnitte werden als [Unified Groups](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations) in Azure Active Directory dargestellt. Sie können in den Abschnitten ab, die stehen in einen Mandanten, der Studenten und Lehrer, die Teil jedes Abschnitts sind und Schule Details, denen zu ein Abschnitt gehört. Die systemeigene Attribute zusammen mit der Extension-Attribute für die unified Gruppen enthalten alle erforderliche Informationen zu den Abschnitt. 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**Attribut**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|`displayName`|Erforderlich|Anzeigename des Abschnitts|
|`{prefix}_SectionId`|Erforderlich|Eindeutige ID für diesen Abschnitt, der von der SI zugewiesen|
|`{prefix}_SectionNumber`|Optional|Anzahl für diesen Abschnitt durch die Bezirk/Schule zugewiesen|
|`{prefix}_SectionName`|Erforderlich|Name des Abschnitts|
|`{prefix}_TermId`|Optional|SIS Ausdrucks-ID des Abschnitts|
|`{prefix}_TermName`|Optional|Begriff Name zugeordnet ist in diesem Abschnitt (zurückgreifen, Winter,: Spirale, Sommer usw.).|
|`{prefix}_TermStartDate`|Optional|Startdatum für den Ausdruck des Abschnitts|
|`{prefix}_TermEndDate`|Optional|Enddatum des Ausdrucks des Abschnitts|
|`{prefix}_SchoolId`|Erforderlich|Schule SIS-ID des Abschnitts|
|`{prefix}_CourseId`|Optional|ID für diesen Kurs, der von der SI zugewiesen|
|`{prefix}_CourseName`|Optional|Name des Kurses|
|`{prefix}_CourseDescription`|Optional|Beschreibung für den Kurs|
|`{prefix}_CourseNumber`|Optional|Nummer der Kurs von der Bezirk/Schule|
|`{prefix}_CourseSubject`|Optional|In diesem Abschnitt der Betreff|
|`{prefix}_Period`|Optional|Eine kombinierte Zeichenfolge aller Zeiträume für den Abschnitt.|
|`{prefix}_AnchorId`|Interne|Anker-ID wird zur eindeutigen Identifizierung jedes Abschnitts intern verwendet.|
|`{prefix}_ObjectType`|Interne|Der Objekttyp für eine Schule ist 'Abschnitt'|
|`{prefix}_SyncSource`|Interne|Die Quelle der diese Informationen für den Abschnitt|


**** 


## <a name="student-attributes"></a>Student-Attribute

<a name="StudentAttributes"></a> Kursteilnehmer als Benutzer in Azure Active Directory dargestellt werden. Sie können die Informationen des aktuellen Studenten, die angemeldet ist rufen Sie und auch die Schule und Abschnitte, denen der Student gehört. Die systemeigene Attribute zusammen mit der Extension-Attribute auf dem Benutzer enthalten alle erforderliche Informationen zu den Teilnehmern. 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**Attribut**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|`mailNickname`|Erforderlich|Eindeutiger Alias des Studenten in das Verzeichnis|
|`userPrincipalName`|Erforderlich|Offizielle E-Mail-Adresse des Studenten|
|`givenName`|Erforderlich|Vorname des Studenten|
|`surName`|Erforderlich|Nachname des Studenten|
|`{prefix}_MiddleName`|Optional|Vorname des Studenten|
|`{prefix}_SyncSource_StudentId`|Erforderlich|Eindeutige ID des Studenten zugewiesen wurde von der SI|
|`{prefix}_SyncSource_SchoolId`|Erforderlich|ID der Schule Student|
|`{prefix}_Email`|Optional|Student persönliche E-Mail-Adresse|
|`{prefix}_StateId`|Optional|Durch den Status der Student zugewiesene Nummer|
|`{prefix}_StudentNumber`|Optional|Nummer der Student mithilfe der Disctrict/School|
|`{prefix}_MailingAddress`|Optional|Postanschrift des Studenten|
|`{prefix}_MailingCity`|Optional|Ort des Studenten|
|`{prefix}_MailingState`|Optional|Bundesland des Studenten|
|`{prefix}_MailingZip`|Optional|Mailing Zip Student|
|`{prefix}_MailingLatitude`|Optional|Die Breite der e-Mail-Adresse|
|`{prefix}_MailingLongitude`|Optional|Longiture der e-Mail-Adresse|
|`{prefix}_MailingCountry`|Optional|– Land Student|
|`{prefix}_ResidenceAddress`|Optional|US-Bundesstaates Adresse Student|
|`{prefix}_ResidenceCity`|Optional|US-Bundesstaates, Stadt Student|
|`{prefix}_ResidenceState`|Optional|US-Bundesstaates Zustand des Studenten|
|`{prefix}_ResidenceZip`|Optional|US-Bundesstaates Zip Student|
|`{prefix}_ResidenceLatitude`|Optional|Breitengrad der US-Bundesstaates-Adresse|
|`{prefix}_ResidenceLongitude`|Optional|Longiture der US-Bundesstaates, Adresse|
|`{prefix}_ResidenceCountry`|Optional|US-Bundesstaates, Land Student|
|`{prefix}_Gender`|Optional|Geschlecht des Studenten|
|`{prefix}_DateOfBirth`|Optional|Geburtsdatum Student|
|`{prefix}_Grade`|Optional|Note Ebene des Studenten|
|`{prefix}_EnglishLanguageLearnersStatus`|Optional|Englische Teilnehmern Status|
|`{prefix}_FederalRace`|Optional|Federal Racebedingung für die Schüler|
|`{prefix}_GraduationYear`|Optional|Einteilung Jahr für Kursteilnehmer|
|`{prefix}_StudentStatus`|Optional|Status des Studenten. {Vorab registrierten, aktiv, übertragene skalierten, angehaltenen, abgestufte, Historische, inaktiv und usw..}|
|`{prefix}_AnchorId`|Interne|Anker-ID wird intern verwendet, um Studenten eindeutig zu identifizieren.|
|`{prefix}_ObjectType`|Interne|Der Objekttyp für eine Schule ist 'Student'|


**** 


## <a name="teacher-attributes"></a>Lehrer-Attribute

<a name="TeacherAttributes"></a> Lehrer werden als Benutzer in Azure Active Directory dargestellt. Sie erhalten die Attribute der aktuellen Lehrer, die angemeldet ist, und die Schule und Abschnitte der Lehrer ist ein Mitglied. Die systemeigene Attribute zusammen mit der Extension-Attribute auf dem Benutzer enthalten alle erforderliche Informationen zu der Schulungsleiter. 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**Attribut**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|`mailNickname`|Erforderlich|Eindeutiger Alias eines Lehrers im Verzeichnis|
|`userPrincipalName`|Erforderlich|Offizielle E-Mail-Adresse eines Lehrers|
|`givenName`|Erforderlich|Vornamen eines Lehrers|
|`surName`|Erforderlich|Nachname eines Lehrers|
|`{prefix}_MiddleName`|Optional|Vornamen eines Lehrers|
|`{prefix}_SyncSource_TeacherId`|Erforderlich|Eindeutige ID eines Lehrers wie von der SI zugewiesen.|
|`{prefix}_SyncSource_SchoolId`|Erforderlich|ID des Berichterstattungsstruktur der der Schulungsleiter|
|`{prefix}_StateId`|Optional|State-ID-Zertifizierung Anzahl der Schulungsleiter|
|`{prefix}_TeacherNumber`|Optional|Nummer der Schulungsleiter mithilfe der Bezirk/School|
|`{prefix}_TeacherStatus`|Optional|Lehrer Status {aktiv, klicken Sie auf Übernehmen, hier nicht mehr usw.. }|
|`{prefix}_Email`|Optional|Lehrer persönliche E-Mail|
|`{prefix}_Title`|Optional|Titel für den Lehrer|
|`{prefix}_TeacherQualification`|Optional|Qualifikation eines Lehrers|
|`{prefix}_AnchorId`|Interne|Anker-ID wird zur eindeutigen Identifizierung jedes Lehrer intern verwendet.|
|`{prefix}_ObjectType`|Interne|Der Objekttyp für eine Schule ist 'Lehrer'|


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Einige der anderen Education-bezogene Ressourcen, denen Sie interessiert sein könnten

- Verwenden der [Schulen Rest Vorgänge](..\api\school-rest-operations.md) Access Schule Informationen

- Abschnitt Zugriffsinformationen, die mit den [Abschnitten Rest-Vorgänge](..\api\section-rest-operations.md)

- Verwenden der [Studenten Rest Vorgänge](..\api\student-rest-operations.md) Student Zugriffsinformationen

- Verwenden der [Lehrer Rest Vorgänge](..\api\teacher-rest-operations.md) Lehrer Zugriffsinformationen 


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
    
