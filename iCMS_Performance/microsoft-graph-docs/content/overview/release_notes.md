# <a name="microsoft-graph-release-notes-and-known-issues"></a>Microsoft Graph Anmerkungen zu dieser Version und bekannte Probleme

Dieser Artikel enthält Informationen zu den neuen Features für Entwickler, die in der November 2015 Version der Microsoft Graph-API verfügbar sind und bekannte Probleme, denen sollten Sie berücksichtigen. 


## <a name="ga-features-in-microsoft-graph-api"></a>GA-Features in Microsoft Graph-API

Die folgenden Microsoft Graph-API-Funktionen sind im Allgemeinen verfügbar:

* Benutzer
* Gruppen
* Dateien
* E-Mails
* Kalender
* Persönliche Kontakte 
* Erstellen, lesen, aktualisieren und Löschen von Operationen (CRUD)
* Cross-Origin Resource sharing (CORS) zu unterstützen.

    
## <a name="preview-features-in-microsoft-graph-api"></a>Preview-Features in Microsoft Graph-API

Die folgenden Features von Microsoft Graph-API Preview sind verfügbar:

* Hinweise 
* Aufgaben
* Excel
* Kontakte
* Organisatorische Kontakte
* Anwendungen
* Dienstprinzipale
* Directory-Erweiterungen
* Webhooks
* Einblicke in die und Beziehungen: um Trends und Arbeiten mit
* Gruppen instant Zugriff auf Inhalt nach der Erstellung
* Zusammengeführt Authentifizierungsmodell für Persönliche Konten arbeiten und Schule Konten. Obgleich dies eine Vorschaufunktion ist, steht auf beide die `/v1.0` und `/beta` Versionen.


## <a name="microsoft-graph-known-issues"></a>Microsoft Graph – bekannte Probleme

Die folgenden sind Probleme mit der Microsoft Graph bekannt.

### <a name="users"></a>Benutzer
#### <a name="no-instant-access-after-creation"></a>Kein instant Zugriff nach der Erstellung
Benutzer können direkt über eine BEREITSTELLUNG in der Benutzerentität für erstellt werden. Eine Office 365-Lizenz muss zunächst ein Benutzer zugewiesen werden, um Zugriff auf Office 365-Diensten zu erhalten. Aufgrund der verteilten Art des Diensts, selbst dann, kann es 15 Minuten dauern, bis die Dateien, Nachrichten und Ereignisse Entitäten stehen für die Verwendung für diesen Benutzer, über die Microsoft Graph-API. Während dieser Zeit erhält apps 404 HTTP-Fehlerantwort. 

#### <a name="photo-restrictions"></a>Foto-Einschränkungen
Lesen und Aktualisieren von Fotos eines Benutzers-Profil ist nur möglich, ob der Benutzer über ein Postfach verfügt.  Darüber hinaus alle Fotos, *möglicherweise* zuvor gespeichert wurden mithilfe der **ThumbnailPhoto** -Eigenschaft (mit der Office 365 unified API Vorschau oder im Azure AD-Diagramm oder über die Synchronisierung des Active Directory verbinden) wird nicht mehr über die Microsoft Graph Benutzer Foto-Eigenschaft zugegriffen werden.  Fehler beim Lesen oder aktualisieren ein Foto ergibt sich in diesem Fall in den folgenden Fehler:

```javascript
    {
      "error": {
        "code": "ErrorNonExistentMailbox",
        "message": "The SMTP address has no mailbox associated with it."
      }
    }
```

 > **HINWEIS**: darauffolgenden GA, speichern und Abrufen von benutzerfotos Profil werden aktiviert werden, selbst wenn der Benutzer verfügt nicht über ein Postfach, und dieser Fehler sollten nicht mehr angezeigt.

#### <a name="default-contacts-folder"></a>Standardordner Kontakte

In der `/v1.0` Version `GET /me/contactFolders` enthält keinen des Benutzers Standardordner Kontakte. 

Ein Update wird zur Verfügung gestellt werden. In der Zwischenzeit können Sie die folgende Abfrage der [Liste Kontakte](http://graph.microsoft.io/docs/api-reference/v1.0/api/user_list_contacts) und der **ParentFolderId** -Eigenschaft zur Umgehung dieses Problems Sie die ID des Standardordners Kontakte abrufen:

```
GET https://graph.microsoft.com/v1.0/me/contacts?$top=1&$select=parentFolderId
```
In der obigen Abfrage:
1. `/me/contacts?$top=1`Ruft die Eigenschaften für einen [Kontakt](http://graph.microsoft.io/docs/api-reference/v1.0/resources/contact) in den Standardordner Kontakte ab.
2. Anfügen von `&$select=parentFolderId` gibt nur den Kontakt **ParentFolderId** -Eigenschaft, die die ID des Standardordners Kontakte gespeichert ist.

#### <a name="adding-and-accessing-ics-based-calendars-in-users-mailbox"></a>Hinzufügen von und Zugreifen auf ICS-basierte Kalender im Postfach des Benutzers
Derzeit ist teilweise Unterstützung für einen Kalender basierend auf einer Internet Kalender Abonnement (ICS):
* Sie können einen Kalender ICS-basierte ein Benutzerpostfach über die Benutzeroberfläche, aber nicht über die Microsoft Graph-API hinzufügen. 
* [Auflisten der Benutzer Kalender](http://graph.microsoft.io/docs/api-reference/v1.0/api/user_list_calendars) können Sie die Eigenschaften **Name**, **Farbe** und **Id** neben den [Kalender](http://graph.microsoft.io/docs/api-reference/v1.0/resources/calendar) im Kalender-Standardgruppe des Benutzers oder einer angegebenen Kalender-Gruppe, einschließlich keine ICS-basierte Kalender abgerufen. Sie können nicht gespeichert oder Zugriff auf die ICS-URL in der Ressource Kalender.
* Sie können auch [die Ereignisse aufgelistet](http://graph.microsoft.io/docs/api-reference/v1.0/api/calendar_list_events) , eines Kalenders ICS-basierte.

### <a name="groups"></a>Gruppen
#### <a name="policy"></a>Richtlinie
Verwenden von Microsoft Graph zum Erstellen, und nennen eine einheitliche Gruppe umgeht unified Gruppenrichtlinien, die über Outlook Web App konfiguriert sind. 

#### <a name="group-permission-scopes"></a>Gruppe berechtigungsbereiche
Das Microsoft Graph werden zwei berechtigungsbereiche (*Group.Read.All* und *Group.ReadWrite.All*) für den Zugriff auf Gruppen von APIs verfügbar gemacht.  Diese berechtigungsbereiche müssen von einem Administrator zugestimmt werden (die Wechsel zwischen Preview ist).  In der Zukunft möchten wir neue Bereiche für Gruppen hinzuzufügen, die von Benutzern zugestimmt werden kann.

#### <a name="adding-and-getting-attachments-of-group-posts"></a>Hinzufügen und Abrufen von Anlagen der Gruppe Beiträge
[Hinzufügen von](http://graph.microsoft.io/docs/api-reference/v1.0/api/post_post_attachments) Anlagen zur Gruppe Beiträge, [Auflisten](http://graph.microsoft.io/docs/api-reference/v1.0/api/post_list_attachments) und Abrufen von Anlagen der Gruppe Beiträge derzeit return die Fehlermeldung "die Anforderung OData wird nicht unterstützt." Hat ein Update für beide eingeführt wurden die `/v1.0` und `/beta` Versionen und am Ende des Januar 2016 zur Verfügung stehen soll.

### <a name="contacts"></a>Kontakte
* Nur persönliche Kontakte werden derzeit unterstützt. Organisatorische Kontakte werden derzeit nicht unterstützt `/v1.0`, aber finden Sie unter `/beta`.
* Mobiltelefon persönlichen Kontakt ist nicht für einen Kontakt zurückgegeben wird. Es wird in Kürze hinzugefügt werden. In der Zwischenzeit kann über Outlook-APIs zugegriffen werden.

### <a name="drives-files-and-content-streaming"></a>Laufwerke, Dateien und streaming-Inhalte
* Erste Time-Zugriff auf einen Benutzer Persönliche Laufwerk über das Microsoft Graph vor der Benutzer zugreift führt ihrer persönlichen Website über einen Browser zu einer Antwort 401.
* Hochladen und Herunterladen von Dateien (Dateien in Office-Gruppen, Laufwerke oder e-Mail-Anlagen) ist auf 4 MB beschränkt.

### <a name="functionality-available-only-in-existing-office-365-rest-apis"></a>Funktionalität, die nur in vorhandenen Office 365-REST-APIs verfügbar
#### <a name="synchronization"></a>Synchronisierung
Outlook, OneDrive und Azure AD-Synchronisierung-Funktionen (in Azure AD dies auch bekannt als differenzielle Abfrage ist) sind nicht verfügbar in `/v1.0` oder `/beta`.  Falls Ihre Anwendung Funktionen zur ereignisempfängersynchronisierung erfordert, fahren Sie mit den vorhandenen Office 365 und Azure AD-REST-APIs verwenden oder verwenden das neue Webhooks Preview-Feature für Ereignisse, Nachrichten und Kontakte über Microsoft Graph angeboten.

> **HINWEIS**: Es ist ein Ziel, die Lücke zwischen vorhandenen APIs und Microsoft Graph so schnell wie möglich, einschließlich der Synchronisierung zu schließen.

#### <a name="batching"></a>Batchverarbeitung
Batchverarbeitung wird von Microsoft Graph nicht unterstützt. Sie können allerdings den Outlook Beta Endpunkt und [Batch Outlook-REST-aufrufen](https://msdn.microsoft.com/en-us/office/office365/api/batch-outlook-rest-requests)verwenden. 

#### <a name="availability-in-china"></a>Verfügbarkeit in China
Der Microsoft Graph-Dienst ist von 21Vianet betrieben (und in China jetzt verfügbar). Überprüfen Sie weitere Informationen einschließlich Einschränkungen [Microsoft Graph unabhängigen Cloud-Bereitstellungen](http://graph.microsoft.io/docs/overview/deployments) .

#### <a name="service-actions-and-functions"></a>Service-Aktionen und Funktionen
`isMemberOf`und `getObjectsById` stehen nicht in Microsoft Graph

### <a name="microsoft-graph-permissions"></a>Microsoft Graph-Berechtigungen
Überprüfen Sie die [Berechtigung Bereiche Thema](http://graph.microsoft.io/docs/authorization/permission_scopes) für die neuesten Details zu unterstützten Microsoft Graph-Anwendung und delegierten Berechtigungen an.  Darüber hinaus stehen die folgenden Einschränkungen für `v1.0`:

|Berechtigung |   Berechtigungstyp | Einschränkung |  Alternative |
|-----------|-----------------|------------|--------------|
|_User.ReadWrite_| Delegiert	    | Nummer des Mobiltelefons kann nicht aktualisiert werden.|    Auch auswählen`Directory.AccessAsUser.All`| 
|_User.ReadWrite.All_|  Delegiert	|  Führen Sie alle CRUD-Vorgänge können nicht auf `User` als benutzerfoto HD und erweiterte Benutzerprofileigenschaften aktualisieren| Wählen Sie auch `Directory.ReadWrite.All` oder `Directory.AccessAsUser.All` Wenn Benutzer Löschung erforderlich ist.|
|_User.Read.All_|   Anwendung	 |Alle Lesevorgänge für andere Benutzer kann nicht ausgeführt werden.| Auch auswählen`Directory.Read.All`|
| _User.ReadWrite.All_ |    Anwendung	 |   Führen Sie alle CRUD-Vorgänge können nicht auf `User` als benutzerfoto HD und erweiterte Benutzerprofileigenschaften aktualisieren |    Wählen Sie auch`Directory.ReadWrite.All`. **HINWEIS**: Benutzer Löschung ist nicht möglich.|
|_Group.Read.All_   | Anwendung	 | Können nicht Gruppen oder Gruppenmitgliedschaften aufgelistet werden.  Gruppe Inhalte können für Office-Gruppen weiterhin gelesen werden.   | Auch auswählen`Directory.Read.All` |
|_Group.ReadWrite.All_  | Anwendung	   | Kann nicht Gruppen oder Gruppenmitgliedschaften aufzählen, Erstellen von Gruppen, Gruppenmitgliedschaften aktualisieren oder Löschen von Gruppen  Können weiterhin lesen und Aktualisieren von Inhalt für Office Gruppen gruppieren.   | Wählen Sie auch `Directory.ReadWrite.All`. **HINWEIS**: Gruppe löschen ist nicht möglich.|

Darüber hinaus stehen die folgenden `/beta` Einschränkungen:

|Berechtigung |   Berechtigungstyp | Einschränkung |  Alternative |
|-----------|-----------------|------------|--------------|
| _Group.ReadWrite.All_ | Delegiert	 | Kann nicht gelesen oder aktualisiert Planner Aufgaben bei der Office-Gruppen  | Auch auswählen`Tasks.ReadWrite`|
|_Tasks.ReadWrite_  | Delegiert	 | Keine lesen oder Aktualisieren von Vorgängen des angemeldeten Benutzers| Auch auswählen`Group.ReadWrite.All`|

### <a name="odata-related-limitations"></a>OData weiterführende Einschränkungen
* **Erweitern Sie $** Einschränkungen: 
 * Keine Unterstützung für`nextLink`
 * Keine Unterstützung für mehr als 1 Ebene der erweitern
 * Keine Unterstützung mit zusätzlichen Parameter (**$filter**, **$select**)
* Mehrere Namespaces werden nicht unterstützt.
* Ruft auf `$ref` und Casting ist auf Benutzer, Gruppen, Geräten, Dienstprinzipale und Anwendungen nicht unterstützt.
* `@odata.bind`wird nicht unterstützt.  Dies bedeutet, dass Entwickler ordnungsgemäß festgelegt nicht können die `Accepted` oder `RejectedSenders` für eine Gruppe.
* `@odata.id`ist nicht auf nicht-Kapselung Navigation (wie Nachrichten) vorhanden, wenn minimale Metadaten verwendet werden
* Filtern von Cross-Arbeitslast/Suche ist nicht verfügbar. 
* Volltextsuche (mit **$search**) ist nur für einige Entitäten, wie Nachrichten verfügbar.

  >  Ihr Feedback ist uns sehr wichtig. Verbinden Sie mit uns in Kontakt auf [Stapelüberlauf](http://stackoverflow.com/questions/tagged/office365). Markieren Sie Ihre Fragen mit [MicrosoftGraph] und [office365].

  
             .

