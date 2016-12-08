# <a name="user-resource-type"></a>Ressourcentyp für Benutzer

Stellt ein Azure AD-Benutzerkonto an. Erbt vom [DirectoryObject](directoryobject.md).


## <a name="methods"></a>Methoden
| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Benutzer erhalten](../api/user_get.md) | [Benutzer](user.md) |Lesen Sie Eigenschaften und Beziehungen des Benutzerobjekts.|
|[Benutzer aktualisieren](../api/user_update.md) | [Benutzer](user.md) |User-Objekt zu aktualisieren. |
|[Benutzer löschen](../api/user_delete.md) | Keine |User-Objekt zu löschen. |
|[Listennachrichten](../api/user_list_messages.md) |[Nachricht](message.md) -Auflistung| Rufen Sie alle Nachrichten im Postfach des angemeldeten Benutzers.|
|[Erstellen der Nachricht](../api/user_post_messages.md) |[Nachricht](message.md)| Erstellen Sie eine neue Nachricht durch das Veröffentlichen in der Nachrichten-Auflistung.|
|[Liste mailFolders](../api/user_list_mailfolders.md) |[MailFolder](mailfolder.md) -Auflistung| Rufen Sie die e-Mail-Ordner-Auflistung im Stammordner des angemeldeten Benutzers. |
|[Erstellen von mailFolder](../api/user_post_mailfolders.md) |[MailFolder](mailfolder.md)| Erstellen Sie eine neue MailFolder, durch die Veröffentlichung auf der MailFolders-Auflistung.|
|[sendMail](../api/user_sendmail.md)|Keine|Sendet die Nachricht im Textkörper Anforderung angegeben.|
|[List-Ereignisse](../api/user_list_events.md) |[Ereignissammlung](event.md)| Rufen Sie eine Liste der Ereignisobjekte im Postfach des Benutzers. Die Liste enthält Einzelinstanz Besprechungen und Series-Master.|
|[Ereignis erstellen](../api/user_post_events.md) |[Ereignis](event.md)| Erstellen Sie ein neues Ereignis, indem Sie das Veröffentlichen in der Auflistung Ereignisse.|
|[Liste Kalender](../api/user_list_calendars.md) |[Kalender](calendar.md) -Auflistung| Rufen Sie eine Auflistung der Calendar-Objekt.|
|[Kalender erstellen](../api/user_post_calendars.md) |[Kalender](calendar.md)| Erstellt einen neuen Kalender durch die Veröffentlichung auf der Calendars-Auflistung.|
|[Liste calendarGroups](../api/user_list_calendargroups.md) |[CalendarGroup](calendargroup.md) -Auflistung| Rufen Sie eine Auflistung der CalendarGroup-Objekts.|
|[Erstellen von calendarGroup](../api/user_post_calendargroups.md) |[CalendarGroup](calendargroup.md)| Erstellen einer neuen CalendarGroup Buchen der CalendarGroups-Auflistung.|
|[Liste calendarView](../api/user_list_calendarview.md) |[Ereignissammlung](event.md)| Rufen Sie eine Auflistung der Ereignis-Objekts.|
|[Liste Kontakte](../api/user_list_contacts.md) |[Kontakt](contact.md) -Auflistung| Rufen Sie eine Kontakte-Auflistung aus dem Standardordner Kontakte des angemeldeten Benutzers.|
|[Kontakt erstellen](../api/user_post_contacts.md) |[Kontakt](contact.md)| Erstellen Sie einen neuen Kontakt durch die Veröffentlichung auf die Kontakte-Auflistung.|
|[Liste contactFolders](../api/user_list_contactfolders.md) |[ContactFolder](contactfolder.md) -Auflistung| Rufen Sie die Kontaktordner-Auflistung im Standardordner Kontakte des angemeldeten Benutzers.|
|[ContactFolder erstellen](../api/user_post_contactfolders.md) |[ContactFolder](contactfolder.md)| Erstellen Sie eine neue ContactFolder, indem Sie das Veröffentlichen in der ContactFolders-Auflistung.|
|[Liste directReports](../api/user_list_directreports.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Benutzer und Kontakte dieses Berichts für den Benutzer aus der Navigationseigenschaft DirectReports.|
|[Listen-manager](../api/user_list_manager.md) |[directoryObject](directoryobject.md) | Abrufen Sie der, oder wenden Sie also Manager aus der Navigationseigenschaft Manager des Benutzers.|
|[Liste Mitglied](../api/user_list_memberof.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Gruppen und Directory Rollen, die der Benutzer ein direktes Mitglied in der Navigationseigenschaft Mitglied ist.|
|[Liste ownedDevices](../api/user_list_owneddevices.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Geräte, die vom Benutzer aus der OwnedDevices Navigation-Eigenschaft gehören.|
|[Liste ownedObjects](../api/user_list_ownedobjects.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Directory-Objekte, die vom Benutzer aus der OwnedObjects Navigation-Eigenschaft gehören.|
|[Liste registeredDevices](../api/user_list_registereddevices.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Geräte, die für den Benutzer aus der Navigationseigenschaft RegisteredDevices Retistered sind.|
|[Liste createdObjects](../api/user_list_createdobjects.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Directory-Objekte, die vom Benutzer aus der Navigationseigenschaft CreatedObjects erstellt.|
|[assignLicense](../api/user_assignlicense.md)|[Benutzer](user.md)|Hinzufügen oder Entfernen von Abonnements für den Benutzer. Sie können auch aktivieren und deaktivieren bestimmte Pläne ein Abonnement zugeordnet.|
|[checkMemberGroups](../api/user_checkmembergroups.md)|Zeichenfolgenauflistung|Überprüfen Sie die Mitgliedschaft in einer Liste von Gruppen. Die Überprüfung ist transitiv.|
|[getMemberGroups](../api/user_getmembergroups.md)|Zeichenfolgenauflistung|Zurückgeben Sie aller Gruppen, denen der Benutzer Mitglied ist. Die Überprüfung ist transitiv.|
|[getMemberObjects](../api/user_getmemberobjects.md)|Zeichenfolgenauflistung| Zurückgeben Sie aller Gruppen und Directory Rollen, denen der Benutzer Mitglied ist. Die Überprüfung ist transitiv. |
|[reminderView](../api/user_reminderview.md)|[Reminder](reminder.md) -Auflistung|Geben Sie eine Liste der kalendererinnerungen innerhalb der Anfangs- und Endzeiten angegeben zurück.|



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Mich-Seite|String|Eine Freihandform Texteingabefeld für den Benutzer selbst beschreiben.|
|accountEnabled|Boolean| **true,** Wenn das Konto aktiviert ist. anderenfalls **false**. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. $Filter unterstützt.    |
|assignedLicenses|[AssignedLicense](assignedlicense.md) -Auflistung|Die Lizenzen, die dem Benutzer zugewiesen sind. Nicht auf NULL festgelegt.            |
|assignedPlans|[AssignedPlan](assignedplan.md) -Auflistung|Die Pläne, die dem Benutzer zugewiesen sind. Schreibgeschützt. Nicht auf NULL festgelegt. |
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Ort|String|Stadt ein, in denen der Benutzer befindet. $Filter unterstützt.|
|Land|String|Land/Region in das sich der Benutzer befindet; "USA" oder "UK". $Filter unterstützt.|
|Abteilung|String|Der Name für die Abteilung, in der der Benutzer arbeitet. $Filter unterstützt.|
|displayName|String|Der Name im Adressbuch für den Benutzer angezeigt. Dies ist in der Regel die Kombination aus den Vornamen des Benutzers, mittleren ersten und letzten Namen. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt und kann nicht während des Updates deaktiviert werden. Unterstützt $filter und $orderby.|
|Vorname|String|Dem angegebenen Namen (Vorname) des Benutzers. $Filter unterstützt.|
|hireDate|DateTimeOffset|Das Einstellungsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|id|String|Der eindeutige Bezeichner für den Benutzer. Geerbt von [DirectoryObject](directoryobject.md). -Taste. Nicht auf NULL festgelegt. Schreibgeschützt.|
|Interessen|Zeichenfolgenauflistung|Eine Liste der Benutzer ihre Interessen zu beschreiben.|
|jobTitle|String|Position des Benutzers. $Filter unterstützt.|
|Mail|String|Die SMTP-Adresse für den Benutzer "jeff@contoso.onmicrosoft.com". Read-Only. $Filter unterstützt.|
|mailNickname|String|E-Mail-Alias für den Benutzer. Diese Eigenschaft muss angegeben werden, wenn ein Benutzer erstellt wird. $Filter unterstützt.|
|mobilePhone|String|Die Anzahl der primären Mobiltelefon für den Benutzer.|
|MeineWebsite|String|Die URL für den Benutzer persönliche Websites.|
|officeLocation|String|Der Standort des Büros des Benutzers direkt Unternehmens.|
|onPremisesImmutableId|String|Diese Eigenschaft wird verwendet, um eine lokale Active Directory-Benutzerkontos auf ihre Azure Active Directory-Benutzerobjekt zuzuordnen. Diese Eigenschaft muss angegeben werden, wenn ein neues Benutzerkonto im Diagramm erstellen, wenn Sie eine verbunddomäne für die Benutzereigenschaft **UserPrincipalName** (UPN) verwenden. **Wichtig:** Die **$** **_** Zeichen verwendet werden, wenn Sie diese Eigenschaft festlegen. $Filter unterstützt.                            |
|onPremisesLastSyncDateTime|DateTimeOffset|Gibt das letzte Mal an dem das Objekt mit dem lokalen Verzeichnis synchronisiert wurde. Beispiel: "2013-02-16T03:04:54Z". Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Um Mitternacht UTC 1 Jan 2014 würde beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|onPremisesSecurityIdentifier|String|Enthält die lokale Sicherheits-ID (SID) für den Benutzer, der lokal in der Cloud synchronisiert wurde. Schreibgeschützt.|
|onPremisesSyncEnabled|Boolean| **true,** Wenn dieses Objekt aus einem lokalen Verzeichnis synchronisiert ist. **false,** Wenn dieses Objekt ursprünglich aus einem lokalen Verzeichnis synchronisiert wurde, aber nicht mehr synchronisiert ist. **null,** Wenn dieses Objekt nie aus einem lokalen Verzeichnis (Standard) synchronisiert wurden. Schreibgeschützt |
|passwordPolicies|String|Kennwortrichtlinien für den Benutzer angibt. Dieser Wert ist eine Enumeration mit einem möglichen Wert wird "DisableStrongPassword", wodurch schwächere Kennwörter als die Standardrichtlinie angegeben werden. "DisablePasswordExpiration" kann auch angegeben. Die beiden können zusammen angegeben werden. Beispiel: "DisablePasswordExpiration, DisableStrongPassword".|
|passwordProfile|[PasswordProfile](passwordprofile.md)|Gibt das Kennwort Profil des Benutzers. Das Profil enthält das Kennwort des Benutzers. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Das Kennwort im Profil muss als von der **PasswordPolicies** -Eigenschaft angegebenen Mindestanforderungen erfüllen. Standardmäßig ist ein sicheres Kennwort erforderlich.|
|pastProjects|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre letzten Projekte aufgelistet werden.|
|Postleitzahl|String|Die Postleitzahl für die Adresse des Benutzers. Die Postleitzahl ist spezifisch für Land/Region des Benutzers. In den USA enthält dieses Attribut die Postleitzahl.|
|preferredLanguage|String|Die bevorzugte Sprache des Benutzers. Führen Sie die ISO 639-1-Code sollte; beispielsweise "En-US".|
|preferredName|String|Den bevorzugten Namen für den Benutzer.|
|provisionedPlans|[ProvisionedPlan](provisionedplan.md) -Auflistung|Die Pläne, die für die Benutzer bereitgestellt werden. Schreibgeschützt. Nicht auf NULL festgelegt. |
|Proxyadressen|Zeichenfolgenauflistung|Beispiel: `["SMTP: bob@contoso.com", "smtp: bob@sales.contoso.com"]` **any** -Operator ist für Filterausdrücke auf mehrwertige Eigenschaften erforderlich. Schreibgeschützt, nicht NULL-Werte zulässt. $Filter unterstützt.          |
|Aufgaben|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre Aufgaben aufgelistet werden.|
|Schulen|Zeichenfolgenauflistung|Eine Liste für den Benutzer zum Aufzählen der Schulen, die sie besucht haben.|
|Fähigkeiten|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre Kenntnisse aufgelistet werden.|
|Zustand|String|Bundesland oder Kanton für die Adresse des Benutzers. $Filter unterstützt.|
|streetAddress|String|Die Straße Ort des Unternehmens des Benutzers.|
|Nachname|String|Der Nachname des Benutzers (Familie oder Nachnamen). $Filter unterstützt.|
|usagelocation-Wert angegeben|String|Ein zweistelligen Ländercode (ISO 3166 standard). Erforderlich für Benutzer, die aufgrund von gesetzliche Vorgabe So überprüfen Sie die Verfügbarkeit von Diensten in Ländern Lizenzen zugewiesen werden.  Beispiele: "US", "JP" und "GB". Nicht auf NULL festgelegt. $Filter unterstützt.|
|userPrincipalName|String|Der Benutzerprinzipalname (UPN) des Benutzers. Der Benutzerprinzipalname ist ein Internet-Schreibweise Anmeldenamen für den Benutzer anhand der Internetstandard RFC 822. Standardmäßig sollte dies der Name des Benutzers e-Mail zuordnen. Das Standardformat ist alias@domain, wobei Domäne muss vorhanden sein, in dem Mandanten Auflistung der überprüften Domänen. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Die überprüften Domänen für den Mandanten können über die **VerifiedDomains** -Eigenschaft der [Organisation](organization.md)zugegriffen werden. Unterstützt $filter und $orderby.
|userType|String|Ein String-Wert, der zum Klassifizieren Benutzertypen in Ihrem Verzeichnis, beispielsweise "Members" und "Gast" verwendet werden kann. $Filter unterstützt.          |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|calendar|[Kalender](calendar.md)|Primären Kalender des Benutzers. Schreibgeschützt.|
|calendarGroups|[CalendarGroup](calendargroup.md) -Auflistung|Kalendergruppen des Benutzers. Schreibgeschützt. NULL-Werte zulässt.|
|calendarView|[Ereignissammlung](event.md)|Die Kalenderansicht für den Kalender. Schreibgeschützt. NULL-Werte zulässt.|
|Kalender|[Kalender](calendar.md) -Auflistung|Kalender des Benutzers. Schreibgeschützt. NULL-Werte zulässt.|
|contactFolders|[ContactFolder](contactfolder.md) -Auflistung|Des Benutzers kontaktiert Ordner. Schreibgeschützt. NULL-Werte zulässt.|
|Kontakte|[Kontakt](contact.md) -Auflistung|Die Kontakte des Benutzers. Schreibgeschützt. NULL-Werte zulässt.|
|createdObjects|[DirectoryObject](directoryobject.md) -Auflistung|Directory-Objekte, die vom Benutzer erstellt wurden. Schreibgeschützt. NULL-Werte zulässt.|
|directReports|[DirectoryObject](directoryobject.md) -Auflistung|Die Benutzer und Kontakte, die an den Benutzer melden. (Die Benutzer und Kontakte, die ihre Manager-Eigenschaft, die auf diesen Benutzer festgelegt haben.) Schreibgeschützt. NULL-Werte zulässt. |
|Laufwerk|[Laufwerk](drive.md)|OneDrive des Benutzers. Schreibgeschützt.|
|Ereignisse|[Ereignissammlung](event.md)|Ereignisse des Benutzers. Standardmäßig wird unter dem Standardkalender Ereignisse anzeigen. Schreibgeschützt. NULL-Werte zulässt.|
|inferenceClassification | [inferenceClassification](inferenceClassification.md) | Relevanz Klassifizierung Nachrichten des Benutzers basierend auf explizite Bezeichnungen, welche Überschreibung abgeleitet Relevanz oder Bedeutung. |
|mailFolders|[MailFolder](mailfolder.md) -Auflistung| E-Mail-Ordner des Benutzers. Schreibgeschützt. NULL-Werte zulässt.|
|Vorgesetzter|[directoryObject](directoryobject.md)|Der Benutzer oder Kontakt, den Vorgesetzten des Benutzers ist. Schreibgeschützt. (HTTP-Methoden: GET, PUT, zu LÖSCHEN.)|
|Mitglied|[DirectoryObject](directoryobject.md) -Auflistung|Gruppen und Directory Rollen, denen der Benutzer Mitglied ist. Schreibgeschützt. NULL-Werte zulässt.|
|Nachrichten|[Nachricht](message.md) -Auflistung|Die Nachrichten in einem Postfach oder Ordner. Schreibgeschützt. NULL-Werte zulässt.|
|ownedDevices|[DirectoryObject](directoryobject.md) -Auflistung|Geräte, die vom Benutzer gehören. Schreibgeschützt. NULL-Werte zulässt.|
|ownedObjects|[DirectoryObject](directoryobject.md) -Auflistung|Directory-Objekte, die vom Benutzer gehören. Schreibgeschützt. NULL-Werte zulässt.|
|Foto|[profilePhoto](profilephoto.md)| Profil-Foto des Benutzers. Schreibgeschützt.|
|registeredDevices|[DirectoryObject](directoryobject.md) -Auflistung|Geräte, die registriert sind für den Benutzer. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "appRoleAssignments",
    "calendar",
    "calendarGroups",
    "calendarView",
    "calendars",
    "contactFolders",
    "contacts",
    "createdObjects",
    "directReports",
    "drive",
    "events",
    "joinedGroups",
    "mailFolders",
    "manager",
    "memberOf",
    "messages",
    "oauth2PermissionGrants",
    "ownedDevices",
    "ownedObjects",
    "photo",
    "registeredDevices"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.user"
}-->

```json
{
  "aboutMe": "string",
  "accountEnabled": true,
  "assignedLicenses": [{"@odata.type": "microsoft.graph.assignedLicense"}],
  "assignedPlans": [{"@odata.type": "microsoft.graph.assignedPlan"}],
  "birthday": "String (timestamp)",
  "businessPhones": ["string"],
  "city": "string",
  "companyName": "string",
  "country": "string",
  "department": "string",
  "displayName": "string",
  "givenName": "string",
  "hireDate": "String (timestamp)",
  "id": "string (identifier)",
  "interests": ["string"],
  "jobTitle": "string",
  "mail": "string",
  "mailNickname": "string",
  "mobilePhone": "string",
  "mySite": "string",
  "officeLocation": "string",
  "onPremisesImmutableId": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "string",
  "onPremisesSyncEnabled": true,
  "passwordPolicies": "string",
  "passwordProfile": {"@odata.type": "microsoft.graph.passwordProfile"},
  "pastProjects": ["string"],
  "postalCode": "string",
  "preferredLanguage": "string",
  "preferredName": "string",
  "provisionedPlans": [{"@odata.type": "microsoft.graph.provisionedPlan"}],
  "proxyAddresses": ["string"],
  "responsibilities": ["string"],
  "schools": ["string"],
  "skills": ["string"],
  "state": "string",
  "streetAddress": "string",
  "surname": "string",
  "usageLocation": "string",
  "userPrincipalName": "string",
  "userType": "string",

  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarGroups": [{ "@odata.type": "microsoft.graph.calendarGroup" }],
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "calendars": [ {"@odata.type": "microsoft.graph.calendar"} ],
  "contacts": [ { "@odata.type": "microsoft.graph.contact" } ],
  "contactFolders": [ { "@odata.type": "microsoft.graph.contactFolder" } ],
  "createdObjects": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "directReports": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [ { "@odata.type": "microsoft.graph.event" } ],
  "inferenceClassification": { "@odata.type": "microsoft.graph.inferenceClassification" },
  "mailFolders": [ { "@odata.type": "microsoft.graph.mailFolder" } ],
  "manager": { "@odata.type": "microsoft.graph.directoryObject" },
  "memberOf": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "messages": [ { "@odata.type": "microsoft.graph.message" } ],
  "ownedDevices": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "registeredDevices": [ { "@odata.type": "microsoft.graph.directoryObject" } ]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
