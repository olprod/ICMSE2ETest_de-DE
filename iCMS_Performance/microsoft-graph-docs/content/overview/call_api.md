# <a name="calling-microsoft-graph"></a>Aufrufen von Microsoft Graph

###<a name="call-microsoft-graph-api-service-via-rest"></a>Rufen Sie Microsoft Graph-API-Dienst über REST
Zugriff und zum Bearbeiten einer Ressource Microsoft Graph-API-aufrufen und anzugeben, die mit einer der folgenden Vorgänge Ressource URLs für die Ressource.   

- GET
- POST
- PATCH
- PUT
- DELETE 

Alle Anfragen von Microsoft Graph-API verwenden Sie das folgende einfache URL-Muster:

```
    https://graph.microsoft.com/{version}/{resource}?[odata_query_parameters]
```

Für diese URL:

- `https://graph.microsoft.com`ist der Endpunkt Microsoft Graph-API
- `{version}`Beispielsweise ist die Zielversion Service `v1.0` oder `beta`.
- `{resource}`ist die Ressource Segment oder den Pfad, wie
  - `users`, `groups`, `devices`, `organization`
  - Der Alias `me`, die in der angemeldeten Benutzers aufgelöst wird
   - Die Ressourcen, die wie zu einem Benutzer gehören `me/events`, `me/drive` oder`me/messages`
  - Der Alias `myOrganization`, die in den Mandanten des angemeldeten Benutzers Organisation aufgelöst wird
- `[odata_query_parameters]`Stellt zusätzliche OData-Abfrageparametern wie `$filter` und`$select` 

Darüber hinaus können Sie den Mandanten als Teil Ihrer Anforderung angeben, die optional und nicht erforderlich ist. Bei Verwendung `me`, den Mandanten nicht angeben. Eine Zusammenfassung der allgemeine Anforderungen sind in der [Übersicht über die](overview.md)verfügbaren.

###<a name="microsoft-graph-api-metadata"></a>Microsoft Graph-API-Metadaten
Das Dokument Service ($metadata) wird am Stamm Service veröffentlicht. Beispielsweise können Sie das Dokument Dienst über die folgenden URLs für die 1.0 und Beta anzeigen.

Microsoft Graph-API `v1.0` Metadaten.
```
    https://graph.microsoft.com/v1.0/$metadata
```
Microsoft Graph-API `beta` Metadaten.
```
    https://graph.microsoft.com/beta/$metadata
```

Die Metadaten können Sie Entitäten, Entitätstypen und legt, komplexe Typen und Enumerationen, die Microsoft Graph REST-API finden Sie unter. Verwenden die Metadaten und Drittanbietertools immer leicht zugänglich sind, können Sie serialisierten Objekte erstellen und generieren Clientbibliotheken für die vereinfachte Verwendung der REST-API.  

Eine URL für die Ressource wird durch das Microsoft Graph Entitätsdatenmodell bestimmt. Aufgabenebene ist im Metadatenschema Entität ($metadata) erläutert. 

Der Pfad URL Ressourcennamen, Abfrageparameter und Aktionsparameter und Werte sind Groß-/Kleinschreibung nicht beachtet. Allerdings werden Werte, die Sie zuweisen, Entity-IDs und andere Werte base64-codierte Groß-/Kleinschreibung beachtet.

Im folgenden Abschnitt werden einige grundlegende Muster Aufrufe programming an der API angezeigt.

###<a name="navigation-from-a-set-to-a-member"></a>Navigationsbereich aus einem Satz an einen member

Um die Informationen über einen Benutzer anzuzeigen, erhalten Sie die `User` Entität aus der `users` -Auflistung, um den betreffenden Benutzer anhand des Bezeichners identifiziert eine HTTPS GET-Anforderung mit. Für eine `User` Entität, entweder die `id` oder `userPrincipalName` Eigenschaft als Bezeichner verwendet werden kann. Die folgende Beispiel für eine Anforderung verwendet die `userPrincipalName` Wert als Id des Benutzers. 

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com HTTP/1.1
Authorization : Bearer <access_token>
```

Bei erfolgreicher sollten Sie 200 OK-Antwort mit der Benutzer Ressource Darstellung in der Nutzlast erhalten, wie folgt aussehen:

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 982

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "id": "c95e3b3a-c33b-48da-a6e9-eb101e8a4205",
    "city": "Redmond",
    "country": "USA",
    "department": "Help Center",
    "displayName": "John Doe",
    "givenName": "John",
    "userPrincipalName": "Johndoe@contoso.onmicrosoft.com",

    ... 
}
```


###<a name="projection-from-an-entity-to-properties"></a>Projektion eine Entität auf Eigenschaften
Abrufen nur Biographische Daten des Benutzers wie des Benutzers _über mich_ Beschreibung und deren Fertigkeiten angegeben festlegen, können Sie die vorherige Anforderung die $select Abfrageoption hinzufügen. Beispielsweise

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com?$select=displayName,aboutMe,skills HTTP/1.1
Authorization : Bearer <access_token>
```

Die erfolgreiche Antwort gibt die 200 OK-Status und Nutzlast mit der folgenden Syntax:

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 169

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "aboutMe": "A cool and nice guy.",
    "displayName": "John Doe",
    "skills": [
        "n-Lingual",
        "public speaking",
        "doodling"
    ]
}
```

Hier wird anstelle der gesamten-Eigenschaft in der `user` Entität, nur die `aboutMe`, `displayName` und `skills` Eigenschaften zurückgegeben werden.

###<a name="traversal-to-another-resource-via-relationship"></a>Durchqueren an eine andere Ressource über Beziehung
Ein Manager enthält ein `directReports` Beziehung mit den anderen Benutzern seine reporting. Um die Liste der die direkten Vorgesetzten eines Benutzers abgefragt, können Sie die folgenden HTTPS GET-Anforderung an das vorgesehene Ziel über Beziehung durchqueren navigieren. 

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com/directReports HTTP/1.1
Authorization : Bearer <access_token>
```

Die erfolgreiche Antwort gibt die 200 OK-Status und Nutzlast im folgenden Format:

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 152
    
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects/$entity",
    "@odata.type": "#microsoft.graph.user",
    "id": "c37b074d-fe9d-4e68-83ad-b4401d3be174",
    "department": "Sales & Marketing",
    "displayName": "Bonnie Kearney",

    ...
}
```

Ebenso können Sie eine Beziehung zum Navigieren zu verwandten Ressourcen folgen. Beispielsweise die `user => messages` Beziehung ermöglicht das Diagramm durchqueren von einem Azure AD-Knoten an einen Exchange Online-Knoten. Die unter diesem Beispiel wird gezeigt, wie Sie dazu im Gespräch REST-API:


```no-highlight 
GET https://graph.microsoft.com/v1.0/me/messages HTTP/1.1
Authorization : Bearer <access_token>
```

    
Die erfolgreiche Antwort gibt die 200 OK-Status und Nutzlast mit der folgenden Syntax:


```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
odata-version: 4.0
content-length: 147
    
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('john.doe%40contoso.onmicrosoft.com')/Messages",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/me/messages?$top=1&$skip=1",
  "value": [
    {
      "@odata.etag": "W/\"FwAAABYAAABMR67yw0CmT4x0kVgQUH/3AAJL+Kej\"",
      "id": "<id-value>",
      "createdDateTime": "2015-11-14T00:24:42Z",
      "lastModifiedDateTime": "2015-11-14T00:24:42Z",
      "changeKey": "FwAAABYAAABMR67yw0CmT4x0kVgQUH/3AAJL+Kej",
      "categories": [],
      "receivedDateTime": "2015-11-14T00:24:42Z",
      "sentDateTime": "2015-11-14T00:24:28Z",
      "hasAttachments": false,
      "subject": "Did you see last night's game?",
      "body": {
        "ContentType": "HTML",
        "Content": "<content>"
      },
      "BodyPreview": "it was great!",
      "Importance": "Normal",
            
       ...
    }
  ]
}
```

###<a name="projection-from-entities-to-properties"></a>Projektion von Entitäten und Eigenschaften
Zusätzlich zur Projektion eine einzelne Entität auf seine Eigenschaften, Sie können auch anwenden der ähnliche `$select` Abfrageoption Entität-Auflistung auf diese an eine Auflistung von einige der zugehörigen Eigenschaften project. Der Name des angemeldeten Benutzers Laufwerk Elemente abgefragt werden soll, können Sie beispielsweise die folgenden HTTPS GET-Anforderung übermitteln:

```no-highlight 
GET https://graph.microsoft.com/v1.0/me/drive/root/children?$select=name HTTP/1.1
Authorization : Bearer <access_token>
```

Die erfolgreiche Antwort zurückgegeben eine 200 OK-Statuscode und Nutzlast mit den Namen und die Typen der freigegebenen Dateien, wie im folgenden Beispiel dargestellt:

```no-highlight 
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('john.doe%40contoso.onmicrosoft.com')/drive/root/children(name,type)",
  "value": [
    {
      "@odata.etag": "\"{896A8E4D-27BF-424B-A0DA-F073AE6570E2},2\"",
      "name": "Shared with Everyone"
    },
    {
      "@odata.etag": "\"{B39D5D2E-E968-491A-B0EB-D5D0431CB423},1\"",
      "name": "Documents"
    },
    {
      "@odata.etag": "\"{9B51EA38-3EE6-4DC1-96A6-230E325EF054},2\"",
      "name": "newFile.txt"
    }
  ]
}
```

###<a name="query-a-subset-of-users-with-the-filtering-query-option"></a>Abfrage eine Teilmenge der Benutzer mit der Abfrage Filteroption
Damit die Mitarbeiter in der eine bestimmte Position innerhalb einer Organisation ermittelt wird, können Sie aus der Users-Auflistung navigieren und geben Sie dann eine Abfrageoption $filter. Ein Beispiel ist wie folgt:

    
```no-highlight 
GET https://graph.microsoft.com/v1.0/users/?$filter=jobTitle+eq+%27Helper%27 HTTP/1.1
Authorization : Bearer <access_token>
```

Die erfolgreiche Antwort gibt die 200 OK-Statuscode und eine Liste der Benutzer mit der angegebenen Position (`'Helper'`), wie im folgenden Beispiel gezeigt:

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal;odata.streaming=true;IEEE754Compatible=false;charset=utf-8
odata-version: 4.0
content-length: 986

{
    "@odata.context": "https://graph.microsoft.com/v1.0/contoso.onmicrosoft.com/$metadata#users",
    "value": [
        {
            "id": "c95e3b3a-c33b-48da-a6e9-eb101e8a4205",
            "city": "Redmond",
            "country": "USA",
            "department": "Help Center",
            "displayName": "Jane Doe",
            "givenName": "Jane",
            "jobTitle": "Helper",
            ......
            "mailNickname": "Jane",
            "mobile": null,
            "otherMails": [
                "jane.doe@contoso.onmicrosoft.com"
            ],
            ......
            "surname": "Doe",
            "usageLocation": "US",
            "userPrincipalName": "help@contoso.onmicrosoft.com",
            "userType": "Member"
        },
        
        ...
    ]
}
```

###<a name="calling-odata-actions-or-functions"></a>Aufrufen von OData-Aktionen oder Funktionen
Die Microsoft Graph-API unterstützt außerdem OData-Aktionen und Funktionen, die Ressourcen zu bearbeiten. Die folgenden HTTPS-POST-Anforderung kann beispielsweise die angemeldeten Benutzers (`me`) eine e-Mail-Nachricht zu senden:
```no-highlight 
POST https://graph.microsoft.com/v1.0/me/microsoft.graph.sendMail HTTP/1.1
authorization: bearer <access_token>
content-type: application/json
content-length: 96

{
  "message": {
    "subject": "Meet for lunch?",
    "body": {
      "contentType": "Text",
      "content": "The new cafeteria is open."
    },
    "toRecipients": [
      {
        "emailAddress": {
          "address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "name": "menu.txt",
        "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "saveToSentItems": "false"
}
```

Die Anforderungsnutzlast enthält die Eingabe für die `microsoft.graph.sendMail` Aktion, die auch in der $metadata definiert ist.

Mit einem einzelnen unified Endpunkt vereinfacht das Microsoft Graph die Application programming Interface für in der Microsoft-Cloud-Dienste. Daher verschwinden die Grenzen der andernfalls Silo-Ed-Dienste. Als Entwickler app sind Sie nicht mehr erforderlich, um die Datenquellen an und benutzerdefinierte Schnittstellen zwischen verschiedenen Datenquellen zu implementieren. 


