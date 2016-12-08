# <a name="microsoft-graph-permission-scopes"></a>Microsoft Graph berechtigungsbereiche

Das Microsoft Graph macht OAuth 2.0-berechtigungsbereiche, die zur Steuerung des Zugriffs auf Daten eine app hat verwendet werden. Als Entwickler konfigurieren Sie Ihre app mit der berechtigungsbereiche für den Zugriff, den es erforderlich sind. In der Regel erfolgt dies über das Portal Azure. Anmeldung Benutzer oder Administratoren erhalten Gelegenheit, um Ihre app Zugriff auf ihre Daten mit den berechtigungsbereiche ermöglichen Ihnen konfigurierte stimmen. Aus diesem Grund sollten Sie die berechtigungsbereiche, die am wenigsten bieten Ebene der von Ihrer app benötigten Berechtigungen. Weitere Informationen zum Konfigurieren von Berechtigungen für Ihre app und über den Vorgang des Zustimmung finden Sie unter [Integration von Clientanwendungen mit Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/).


##<a name="permission-scope-concepts"></a>Berechtigung Bereich Konzepte

###<a name="app-only-vs-delegated-scopes"></a>Nur-App-im Vergleich zu delegierte Bereiche
Berechtigungsbereiche können entweder nur-app- oder delegierte sein. Nur-App-Bereiche (auch bekannt als app-Rollen) erteilen die Berechtigungen angeboten vom Gültigkeitsbereich die vollständigen Satz app. Nur-App-Bereiche werden in der Regel von apps verwendet, die als Dienst ausgeführt werden soll, ohne dass eine angemeldeten Benutzers vorhanden sind. Delegierte berechtigungsbereiche sind für apps, denen ein Benutzer bei anmeldet. Bereiche delegieren die Rechte des angemeldeten Benutzers für die app ermöglicht die app als den angemeldeten Benutzer fungieren. Werden die tatsächlichen Berechtigungen für die app die geringsten Kombination (die Schnittmenge) Berechtigungen gewährt durch den Bereich und die vom angemeldeten Benutzer zur Verfügung stehen. Beispielsweise wenn des berechtigungsumfangs delegierte Berechtigungen zum Schreiben aller Verzeichnisobjekte gewährt, aber der Benutzer angemeldet hat Berechtigungen nur für ihre eigenen Benutzerprofil aktualisieren, werden die app nur können Profil des angemeldeten Benutzers, aber keine anderen Objekte geschrieben.

###<a name="full-and-basic-profiles-for-users-and-groups"></a>Vollständige und grundlegende Profile für Benutzer und Gruppen
Die vollständige Profil (oder Profile) eines Benutzers oder einer Gruppe enthält alle deklarierten Eigenschaften für die Entität. Da das Profil möglicherweise sensible Verzeichnisinformationen oder personenbezogene Informationen (PII) enthalten, einschränken mehrere Bereiche app Zugriff auf eine begrenzte Auswahl von Eigenschaften als ein einfaches Profil bezeichnet. Für Benutzer, basic Profile enthält nur die folgenden Eigenschaften: Name, vor-und Nachname, Foto anzeigen und e-Mail-Adresse. Für Gruppen enthält das grundlegende Profil nur den Anzeigenamen. 

<!---   <a name="msg_perm_details"> </a>  -->

##<a name="permission-scope-details"></a>Details zum Umfang der Berechtigung
Sie müssen Ihrer app, um die erforderlichen Berechtigungen zum Zugriff auf die Microsoft Graph-API-Ressourcen haben konfigurieren. Die Berechtigungen sind auf einzelne Ressourcen für die Rechte zum Lesen, schreiben oder von beiden Schritte durchführen beschränkt. 

In den folgenden Tabellen Listen die berechtigungsbereiche Microsoft Graph-API und erläutert wird der Zugriff von jedem. 
- Die Spalte **Bereich** enthält den Bereichsnamen an. Bereichsnamen nehmen Sie sich das Formular resource.operation.constraint. beispielsweise Group.ReadWrite.All. Wenn die Einschränkung "All" ist, wird der Bereich der app die Möglichkeit zum Ausführen des Vorgangs (Lesen/Schreiben) auf allen die angegebenen Ressourcen (Gruppe) in das Verzeichnis gewährt. andernfalls lässt der Bereich nur den Vorgang für das Profil des angemeldeten Benutzers. Bereiche können eingeschränkten Berechtigungen für den angegebenen Vorgang gewähren finden Sie in der Spalte **Beschreibung** Einzelheiten.
- Die Spalte **Berechtigung** zeigt, wie der Bereich im Azure Portal angezeigt wird. 
- Spalte **Beschreibung** beschreibt den vollständigen Satz von Berechtigungen mithilfe des Bereichs. Für delegierte Bereiche werden die tatsächliche Zugriffsberechtigungen für die app die geringsten Kombination (Schnittpunkt) der Zugriff erteilt werden, indem Sie den Bereich und die Rechte des angemeldeten Benutzers. 
- Entsprechend gibt an, ob die Berechtigungen des Administrators Zustimmung erforderlich sind, werden die Bereiche gruppiert.

  > **Hinweis**: Siehe [Versionshinweise](http://graph.microsoft.io/docs/overview/release_notes) für `v1.0` und `beta` Berechtigung Bereich Einschränkungen.
  
###<a name="permissions-requiring-administrators-consent"></a>Berechtigungen anfordern der Zustimmung des Administrators

|   **Bereich**                  |  **Berechtigung für Azure-Verwaltungsportal**                          |  **Beschreibung** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| _User.Read.All_                |     `Read all user's full profiles`           | Identisch mit User.ReadBasic.All, mit der Ausnahme, dass die app zum Lesen von vollständigen Profils aller Benutzer in der Organisation und beim Lesen der Navigationseigenschaften können wie Manager und Mitarbeiter. Das vollständige Profil beinhaltet alle deklarierten Eigenschaften der Entität **Benutzer** . Um die Gruppen zu lesen, denen ein Benutzer Mitglied ist, wird die app auch Group.Read.All oder Group.ReadWrite.All erfordern. |
| _User.ReadWrite.All_           |     `Read and write all user's full profiles` | Ermöglicht die app zum Lesen und Schreiben aller Benutzerprofileigenschaften, Berichte und Manager von anderen Benutzern in Ihrer Organisation, im Namen des angemeldeten Benutzers. |
| _Directory.Read.All_           |     `Read directory data`                     | Ermöglicht die app zum Lesen von Daten im Verzeichnis Ihrer Organisation, wie Benutzern, Gruppen und apps. |
| _Directory.ReadWrite.All_      |     `Read and write directory data`           | Ermöglicht die app zum Lesen und Schreiben von Daten in das Verzeichnis der Organisation, wie Benutzer und Gruppen.  Lässt keine Benutzer oder eine Gruppe löschen. Es nicht zulassen die app, um Benutzern oder Gruppen zu löschen oder Zurücksetzen von Benutzerkennwörtern. |
| _Directory.AccessAsUser.All_   |     `Access directory as the signed-in user`  | Ermöglicht die app an den gleichen Zugriff auf Informationen im Verzeichnis befindet wie der Benutzer angemeldet haben.|
| _Group.Read.All_ |    `Read all groups` | Ermöglicht die app Listengruppen und deren Eigenschaften und alle Gruppenmitgliedschaften im Namen des angemeldeten Benutzers vertraut zu machen.  Außerdem können die app zum Lesen von Kalender, Unterhaltungen, Dateien und andere Inhalte Gruppe für alle Gruppen die angemeldeten Benutzers zugreifen kann. |
| _Group.ReadWrite.All_ |    `Read and write all groups`| Die app Gruppen erstellen und alle Gruppeneigenschaften und Mitgliedschaften im Namen des angemeldeten Benutzers lesen können.  Darüber hinaus können Gruppenbesitzer zum Verwalten von ihren Gruppen und Mitglieder hinzu, die Gruppe Inhalte zu aktualisieren. |


###<a name="permissions-not-requiring-administrators-consent"></a>Berechtigungen, die keine erfordern Zustimmung des Administrators

|   **Bereich**    |  **Berechtigung für Azure-Verwaltungsportal**   |  **Beschreibung** |
|:---------------|:------------------|:-----------------|
| _User.Read_       |    `Sign-in and read user profile` | Ermöglicht es Benutzern, die app anmelden, und die app im Profil des angemeldeten Benutzer lesen können. Das vollständige Profil beinhaltet alle deklarierten Eigenschaften der Entität Benutzer. Die app kann nicht Navigationseigenschaften wie Manager oder Mitarbeiter gelesen werden. Außerdem können die app, lesen die folgenden grundlegenden Firmeninformationen des angemeldeten Benutzers (über das **TenantDetail** -Objekt): Mandanten-ID, Anzeigename Mandanten und überprüften Domänen.|
| _User.ReadWrite_ |    `Read and write access to user profile` | Ermöglicht die app zum Lesen von Ihrem Profil. Darüber hinaus können die app so aktualisieren Sie Ihre Profilinformationen in Ihrem Namen. |
| _User.ReadBasic.All_ |    `Read all user's basic profiles` | Ermöglicht die app zum Lesen von basic Profile aller Benutzer in der Organisation im Namen des angemeldeten Benutzers. Die folgenden Eigenschaften umfassen eine grundlegende Benutzerprofil: Name, vor-und Nachname, Foto anzeigen und e-Mail-Adresse. Zum Lesen von Gruppen, denen ein Benutzer Mitglied ist, wird die app auch Group.Read.All oder Group.ReadWrite.All erforderlich.| 
| _Mail.Read_ |    `Read user mail` | Ermöglicht die app zum Lesen von e-Mail in Benutzerpostfächer. |
| _Mail.ReadWrite_ |    `Read and write access to user mail` | Ermöglicht die app zu erstellen, lesen, aktualisieren und Löschen von e-Mail in Benutzerpostfächer. Schließt keine Berechtigung zum Senden von e-Mail-Nachrichten.|
| _Mail.Send_ |    `Send mail as a user` | Ermöglicht die app als Benutzer in der Organisation e-Mail-Nachrichten senden. |
| _Calendars.Read_ |    `Read user calendars`  | Ermöglicht die app beim Lesen von Ereignissen im Benutzerkalender an.|
| _Calendars.ReadWrite_ |    `Have full access to user calendars`  | Ermöglicht die app zu erstellen, lesen, aktualisieren und löschen Ereignisse im Benutzerkalender an. |
| _Contacts.Read_ |    `Read user contacts`  | Die app Benutzerkontakte lesen können. |
| _Contacts.ReadWrite_ |    `Have full access to user contacts`  | Ermöglicht die app zu erstellen, lesen, aktualisieren und Löschen von Kontakten für Benutzer. |
| _Files.Read_ |    `Read user files and files shared with user` | Ermöglicht die app zum Lesen von Dateien und Dateien, die gemeinsam mit dem Benutzer des angemeldeten Benutzers.| 
| _Files.ReadWrite_ |   `Have full access to user files and files shared with user` | Ermöglicht die app zu lesen, erstellen, aktualisieren und Löschen von Dateien und Dateien, die gemeinsam mit dem Benutzer des angemeldeten Benutzers. |
| _Files.ReadWrite.Selected_ |    `Read and write files that the user selects` | Ermöglicht die app zum Lesen und Schreiben von Dateien, dass der Benutzer wählt. Die app hat Zugriff für einige Stunden, nachdem der Benutzer eine Datei auswählt. |
| _Files.Read.Selected_ |    `Read files that the user selects`  | Ermöglicht die app zum Lesen von Dateien, die der Benutzer wählt. Die app hat Zugriff für einige Stunden, nachdem der Benutzer eine Datei auswählt. |
| _Sites.Read.All_ |    `Read items in all site collections` | Ermöglicht der Anwendung zum Lesen von Dokumenten und Listenelementen in allen Websitesammlungen im Namen des angemeldeten Benutzers. |
| _OpenID_ |    `Sign users in`(Vorschau) | Können Benutzer zur Anmeldung bei der app mit ihrer Arbeit oder Schule Konten und ermöglicht die grundlegende Benutzerprofilinformationen finden Sie unter-app.|
| _offline_access_ |    `Access user's data anytime`(Vorschau) | Ermöglicht die app zum Lesen und Aktualisieren von Benutzerdaten, auch wenn sie zurzeit nicht von der app verwendet werden.|

###<a name="app-only-permissions-requiring-administrators-consent"></a>Nur-App-Berechtigungen anfordern der Zustimmung des Administrators

|   **Bereich**    |  **Berechtigung für Azure-Verwaltungsportal**   |  **Beschreibung** |
|:---------------|:------------------|:-----------------|
| _Mail.Read_       |    `Read mail in all mailboxes` | Ermöglicht die app zum Lesen von e-Mails in allen Postfächern ohne eine angemeldeten Benutzers.|
| _Mail.ReadWrite_ |    `Read and write mail in all mailboxes` | Ermöglicht die app zu erstellen, lesen, aktualisieren und Löschen von e-Mail-Nachrichten in allen Postfächern ohne eine angemeldeten Benutzers. Schließt keine Berechtigung zum Senden von e-Mail-Nachrichten. |
| _Mail.Send_ |    `Send mail as any user` | Die app als beliebiger Benutzer ohne einen angemeldeten Benutzer e-Mail-Nachrichten senden können. | 
| _Calendars.Read_ |    `Read calendars in all mailboxes` | Ermöglicht die app beim Lesen von Ereignissen für alle Kalender, ohne dass ein Benutzer angemeldet. |
| _Calendars.ReadWrite_ |    `Read and write calendars in all mailboxes` | Ermöglicht die app zu erstellen, lesen, aktualisieren und Löschen von Ereignissen für alle Kalender, ohne dass ein Benutzer angemeldet.|
| _Contacts.Read_ |    `Read contacts in all mailboxes` | Ermöglicht die app zum Lesen von alle Kontakte in allen Postfächern ohne eine angemeldeten Benutzers. |
| _Contacts.ReadWrite_ |    `Read and write contacts in all mailboxes`  |Ermöglicht die app zu erstellen, lesen, aktualisieren und löschen Sie alle Kontakte in allen Postfächern ohne eine angemeldeten Benutzers.|
| _User.ReadBasic.All_ |    `Read all users' basic profiles`  | Ermöglicht die app eine grundlegende Gruppe von Benutzerprofileigenschaften von anderen Benutzern in Ihrer Organisation ohne eine angemeldeten Benutzers gelesen. Enthält Anzeigename, vor-und Nachname, Fotos und Abwesenheitsnotiz.|
| _User.Read.All_ |    `Read all users' full profiles` | Ermöglicht die app die vollständige Gruppe von Benutzerprofileigenschaften, Gruppenmitgliedschaft, Berichte und Managern anderer Benutzer in Ihrer Organisation, ohne dass ein angemeldeten Benutzer gelesen.| 
| _User.ReadWrite.All_ |   `Read and write all users' full profiles` | Ermöglicht die app zum Lesen und Schreiben aller Benutzerprofileigenschaften, Gruppenmitgliedschaft, Berichte und Manager von anderen Benutzern in Ihrer Organisation, ohne dass ein Benutzer angemeldet.|


##<a name="preview"></a>Vorschau
###<a name="permissions-not-requiring-administrators-consent-preview"></a>Berechtigungen, die keine erfordern des Administrators Zustimmung (Preview)

|   **Bereich**    |  **Berechtigung für Azure-Verwaltungsportal**   |  **Beschreibung** |
|:---------------|:------------------|:-----------------|
| _Tasks.ReadWrite_ |    `Create, read, update and delete user tasks and plans`(Vorschau) | Ermöglicht die app zu erstellen, lesen, aktualisieren und Löschen von Aufgaben und Pläne (und diese Aufgaben), zugewiesen oder der angemeldeten Benutzer freigegeben werden.|
| _People.Read_ |    `Read users' relevant people lists`(Vorschau) | Ermöglicht die app eine bewerteter Liste der entsprechenden Personen des angemeldeten Benutzers zu lesen. Die Liste enthält die lokalen Kontakten, Kontakte aus für soziale Netzwerke, Ihrer Organisation Verzeichnis und Personen von letzte Kommunikation (wie e-Mail und Skype).|
| _People.ReadWrite_ |    `Read and write users' relevant people lists`(Vorschau) | Ermöglicht die app erstellen, lesen und Schreiben in die Rangfolge Liste der entsprechenden Personen des angemeldeten Benutzers. Die Liste enthält die lokalen Kontakten, Kontakte aus für soziale Netzwerke, Ihrer Organisation Verzeichnis und Personen von letzte Kommunikation (wie e-Mail und Skype).|
| _Notes.Create_ |    `Create pages in users' notebooks`(Vorschau) | Ermöglicht die app zum Lesen die Titel der Abschnitte und Notizbücher und Erstellen neuer Seiten, Notebooks und Abschnitte im Namen des angemeldeten Benutzers.|
| _Notes.ReadWrite.CreatedByApp_ |    `Limited notebook access`(Vorschau) | Ermöglicht die app die Titel der Abschnitte und Notizbücher lesen, erstellen Sie neue Seiten im Namen des angemeldeten Benutzers. Außerdem können die app zum Lesen und Aktualisieren von Seiten von der app erstellt wurden. |
| _Notes.Read_ |    `Read user notebooks`(Vorschau) | Ermöglicht die app zum Anzeigen der Titel der OneNote-Notizbücher und Abschnitte und alle Seiten im Namen des angemeldeten Benutzers zu lesen. Kennwortgeschützte Abschnitte kann nicht anzeigen. |
| _Notes.ReadWrite_ |    `Read and write user notebooks`(Vorschau) | Ermöglicht die app die Titel der Abschnitte und Notizbücher lesen, alle Seiten lesen, Schreiben von allen Seiten und Erstellen neuer Seiten im Namen des angemeldeten Benutzers.  Es kann nicht auf kennwortgeschützte Abschnitte zugreifen. |
| _Notes.Read.All_ |    `Read all notebooks that the user can access`(Vorschau) | Ermöglicht die app lesen Sie den Inhalt aller Notizbücher und Abschnitte, in denen der angemeldeten Benutzer zugreifen kann.   Kennwortgeschützte Abschnitte nicht gelesen. |
| _Notes.ReadWrite.All_ |    `Read and write notebooks that the user can access`(Vorschau) | Ermöglicht die app zum Lesen und schreiben den Inhalt aller Notizbücher und Abschnitte, in denen der angemeldeten Benutzer zugreifen kann.  Es kann nicht auf kennwortgeschützte Abschnitte zugreifen.|


<!-- -->

##<a name="permission-scope-scenarios"></a>Berechtigung Bereich Szenarien
Nachfolgend sind einige app-Szenarien mit den `User` und `Group` Ressourcen und ihre entsprechenden erforderlich Bereiche. In der folgenden Tabelle zeigt die berechtigungsbereiche einer App Ausführen bestimmter Vorgänge werden benötigt. Notiz, die in einigen Fällen wird die Möglichkeit der app für einige Operationen hängt ab, ob die Berechtigungsbereich nur-app- oder delegierte ist und, im Fall von delegierten berechtigungsbereiche, auf die Rechte des angemeldeten Benutzers. 

###<a name="access-scenarios-using-the-user-resource-and-the-required-scopes"></a>Verwenden der User-Ressource und die erforderlichen Bereiche Access-Szenarien

| **App-Aufgaben im Zusammenhang mit Benutzer**   |  **Erforderliche Bereiche** | **Berechtigungen für Azure-Verwaltungsportal** |
|:-------------------------------|:---------------------|:---------------|
| App möchte zum Lesen von anderer Benutzer grundlegende Informationen (nur Anzeigename und Bild), beispielsweise in einer Entnahme Erfahrung Personen anzeigen   | _User.ReadBasic.All_  |  `Read all user's basic profiles` |
| Möchte, dass die App vollständig Benutzerprofil lesen für Benutzer (Siehe Mitarbeiter, und Manager usw.) signiert  | _User.Read_ | `Enable sign-in and read user profile`|
| Möchte, dass die App vollständig Benutzerprofil lesen Sie alle Benutzer  | _User.Read.All_ |  `Read all user's full profiles`   |
| App möchte zum Lesen von Dateien, e-Mail und Ihren Kalender Informationen für den angemeldeten Benutzer  | _User.Read_, _Files.Read_, _Mail.Read_, _Calendar.Read_ | `Enable sign-in and read user profile`, `Read users' files`,  `Read user mail`,  `Read user calendars` |
| App möchte des angemeldeten Benutzers (Mein) Dateien gelesen und Dateien, dass andere Benutzer mit dem angemeldeten Benutzer (me) freigegeben haben. | _User.Read_, _Files.Read_, _Sites.Read.All_ | `Enable sign-in and read user profile`, `Read users' files`,  `Read items in all site collections` |
| App möchte zum Lesen und Schreiben vollständige Benutzerprofil für angemeldeten Benutzer   | _User.ReadWrite_ | `Read and write access to user profile` |
| App möchte das Lesen und Schreiben vollständige Benutzerprofil alle Benutzer    | _User.ReadWrite.All_ | `Read and write all user's full profiles` |
| App möchte lesen und Schreiben von Dateien, e-Mail und Ihren Kalender Informationen für den angemeldeten Benutzer    | _User.ReadWrite_, _Files.ReadWrite_, _Mail.ReadWrite_, _Calendar.ReadWrite_  |  `Read and write access to user profile`,  `Read and write access to user profile`,  `Read and write access to user mail`, `Have full access to user calendars` |
   

###<a name="access-scenarios-using-the-group-resource-and-the-required-scopes"></a>Access-Szenarien mit der Group-Ressource und die erforderlichen Bereiche
    
| **App-Aufgaben im Zusammenhang mit Gruppe**  |  **Erforderliche Bereiche** |  **Berechtigungen für Azure-Verwaltungsportal** |
|:-------------------------------|:---------------------|:---------------|
| App möchte zum Lesen von grundlegenden Gruppeninformationen (nur Anzeigename und Bild), beispielsweise zum Anzeigen in einer Gruppe Entnahme Erfahrung  | _Group.Read.All_  | `Read all groups`|
| Lesen Sie den gesamten Inhalt in allen unified Gruppen, darunter Dateien, Unterhaltungen möchte App.  Auch für die Anzeige von Gruppenmitgliedschaften, Gruppenmitgliedschaften, aktualisiert werden muss (Wenn Besitzer).  |  _Group.Read.All_ | `Read items in all site collections`, `Read all groups`|
| App möchte das Lesen und Schreiben aller Inhalte in allen unified Gruppen, darunter Dateien, Unterhaltungen.  Es muss auch einblenden Gruppenmitgliedschaften und Gruppenmitgliedschaften, aktualisiert werden (Wenn Besitzer).  |  _Group.ReadWrite.All_, _Sites.ReadWrite.All_ |  `Read and write all groups`, `Edit or delete items in all site collections` |
| App möchte Gruppe (Suchen) eine einheitliche ermitteln. Es kann der Benutzer zum Suchen nach einer bestimmten Gruppe, und wählen aus der Aufzählungsliste um den Benutzer die Gruppe "Leistungsprotokollbenutzer" ermöglichen.     | _Group.ReadWrite.All_ | `Read and write all groups`|
| Möchte, dass die App eine Gruppe durch AAD Diagramm erstellen |   _Group.ReadWrite.All_ | `Read and write all groups`|
 

<!---   ##Additional Resources##


- [Authenticate Microsoft Graph endpoints using the v2.0 app model preview](authenticate-MSGraph-using-v2.md )
- [Hands on lab: Deep dive into the Office 365 unified API](http://dev.office.com/hands-on-labs/4585) -->

