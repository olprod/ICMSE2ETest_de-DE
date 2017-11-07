
# <a name="microsoft-graph-frequently-asked-questions-faqs"></a>Microsoft Graph häufig gestellte Fragen (FAQs)

## <a name="what-platforms-are-supported-by-microsoft-graph-api"></a>Welche Plattformen werden von Microsoft Graph-API unterstützt?
<!--
Apps can use the Microsoft Graph API to perform create, read, update, and delete (CRUD) operations on data sources and entities, giving them seamless access to work data. 

**Ease of use--one endpoint, all Office 365 data under one roof**

You can use the API in four steps:
1.  Select your programming language and development environment.
2.  Build your app.
3.  Optionally, host your app in Microsoft Azure or any cloud platform you choose.
4.  Authenticate your users by using single sign-on with Azure AD.

As a developer you can use the API to create custom apps that access and interact with all the richness of enterprise and productivity data--users, groups, organizational contacts, files, folders, mail, calendar, insights and relationships--and build apps across all mobile, web, and desktop platforms. No matter your development platform or tools. Using a single service endpoint to access those entities and data. And a single authentication flow.  -->

Sie können:

<!--Just like in Office 365 APIs, Office 365 unified endpoint API  allows you to build apps using any development environment of your choice:  -->

- Verwenden Sie jeder Entwicklungsumgebung, die Sie kennen, wie .NET, PHP, Java, Python oder Ruby
- Verwenden Sie eine beliebige Programmiersprache, Entwicklungsplattform und Hostingumgebung
- Erstellen einer app, die der API mit jeder Web-Sprache, einschließlich JavaScript, HTML5, Python, Ruby, PHP und ASP.NET greift auf  
- Verwenden Sie die IDE Ihrer Wahl, ob das Visual Studio Eclipse, Android Studio, Xcode oder etwas anderes gewählte ist
- Hosten Sie Ihre apps in Microsoft Azure oder einer beliebigen Cloudplattform
- Entwickeln von apps für universelle Windows iOS, Android, oder auf einem anderen Geräteplattform
- Aufrufen der API aus Office-Add-ins (früher apps für Office) oder SharePoint-Add-ins (früher apps for SharePoint)
 


## <a name="why-use-microsoft-graph-api"></a>Gründe für die Verwendung von Microsoft Graph-API

Nehmen wir an, dass programmgesteuert abrufen Dateien eines Benutzers, Profilbild, und suchen den Manager der Person ein, die diese Datei in Ihrer Organisation zuletzt bearbeitet werden soll. Da die Informationen in mehrere Dienste Azure Active Directory gespeichert wird, umfasst SharePoint und Exchange die Aufgabe mehrere Schritte mit Office 365-APIs: 

1. Verwendung der Discovery-Dienst finden Sie die verschiedenen Dienstendpunkte 
2. Bestimmen Sie die URL der die Dienste, denen Ihre apps für Office 365 herstellen möchten
3. Klicken Sie dann erwerben Sie und verwalten Sie das Zugriffstoken für jeden Dienst und stellen Sie direkt die Anforderung an den Dienst

Nun können Sie die Verwendung von Microsoft Graph-API zum Ausführen des gleichen komplexen Vorgangs über einen einzelnen Endpunkt für den REST-API verwenden. Sie müssen nicht ermitteln und Navigieren von einem anderen Endpunkt für jeden Dienst, erwerben und verwalten separate Zugriffstoken für jeden Dienst, beschäftigen sich mit Silo Services und verschiedener Datenmodell.

##<a name="sample-queries"></a>Beispielabfragen

Das folgende Beispiel zeigt der aktuelle Modell für die Interaktion mit Office 365-API mit unterschiedlichen Dienstendpunkten und wie viel einfacher Dies wird mit Microsoft Graph-API.

**Unterschiedliche Dienstendpunkten**

|   **Vorgang**                  |  **API**                          |  **Service-Endpunkt** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| Ermitteln von Dienstendpunkten für Office 365-API               |     `Discovery Service`           | _https://_ **API.Office.com** _/Discovery/v1.0/Me/Services_ |
| Abrufen von Benutzern           |     `Azure AD Graph API` | _https://_ **Graph.Windows.NET** _/contoso.com/users?api-Version=2013-04-05_|
| Rufen Sie Nachricht Auflistung aus dem Posteingang       |     `Office 365 API`           | _https://_ **Outlook.Office365.com** _/API/v1.0/Me/Messages_  |
| Joes Dateien abrufen   |     `Office 365 API`  | _https://_ **Contoso-my.sharepoint.com**_ /_Personal/Joe_contoso_com/api/v1.0/files_ |


Die Microsoft Graph-API verwenden, müssen Sie zuerst ermitteln Dienstendpunkten und klicken Sie dann durchlaufen verschiedene Endpunkte um Dateien eines Benutzers, e-Mail und so weiter zu erhalten. Sie müssen nur zur Interaktion mit einem einzelnen REST-URL-Namespace _**graph.microsoft.com**_ist.

**Microsoft Graph-API**

|   **Vorgang**                  |  **API**                          |  **Service-Endpunkt** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| Ermitteln von Dienstendpunkten für Office 365-API                |     `Microsoft Graph`           | Nicht erforderlich |
| Abrufen von Benutzern           |     `Microsoft Graph` | _https://_ **Graph.Microsoft.com** _/v1.0/contoso.onmicrosoft.com/Users_ |
| Rufen Sie die Nachricht-Auflistung aus dem Posteingang       |     `Microsoft Graph`           | _https://_ **Graph.Microsoft.com** _/v1.0/Me/Messages_  |
| Abrufen Joes Dateien   |     `Microsoft Graph `  | _https://_ **Graph.Microsoft.com** _/v1.0/Me/Drive/Root/Children_ |


## <a name="whatre-the-benefits-of-using-microsoft-graph-api"></a>Was sind die Vorteile der Verwendung von Microsoft Graph-API?

Einige der Vorteile der Verwendung von Microsoft Graph-API lauten wie folgt:

**Erleben Sie konsistent und optimierte Developer Verarbeiten von Microsoft Cloud services**

-   Einzelner Namespace für alle Endpunkte. Es ist nicht erforderlich für die Ermittlung der Service-Endpunkt.
-   Ein Token auf alle Ressourcen zugreifen
-   Integrierte und direkte Navigation zwischen derzeit Silo-Diensten (beispielsweise die Abteilung und-Verwaltung Kette des Benutzers, der ein bestimmtes Dokument verfasst get)
-   Nur müssen eine einzige API verwenden festgelegt, d. h., nur für Microsoft Graph-API verwenden, um auf mehrere Dienste eine Verbindung herstellen
-   Einheitliche und erweiterte REST-API und Entitäten über die Office-Plattform 
-   Benennen von konsistenten-Eigenschaft und Schemas für Personen, einschließlich der Navigationseigenschaften zwischen Entitäten

**Aktivieren Sie produktivere Work-Life Erfahrungen mit Office**

-   Kontextbezogene Inhalte. Beispielsweise Suchen von Dokumenten nach Gruppe, Project, Team oder trends
-   Kontextbezogene Benutzer Beziehungen. Beispielsweise können Sie Benutzer, indem Sie Gruppenmitgliedschaft Interesse, Kenntnisse und Erfahrung finden.  Sie können auch Organigramms Beziehung abrufen.

**Aktivieren Sie beim Entwickeln von apps in einer beliebigen Programmiersprache auf allen Plattformen**

-   Development Tools und Ressourcen für alle Entwickler. Sie können von jeder Plattform und Sprache entwickeln 
-   Mobile Entwicklung für alle Plattformen mithilfe von open Technologien  
-   Keine Notwendigkeit zur keine besonderen Exchange, SharePoint oder Azure AD-Kenntnisse greifen Sie auf Microsoft Graph-API-Entitäten

<!---<a name="msg_v2auth"> </a>-->

## <a name="does-microsoft-graph-api-support-v20-app-authentication-endpoint"></a>Wird Microsoft Graph-API v2. 0-app-Authentifizierung Endpunkt unterstützt?

Ja. Weitere Informationen finden Sie [unter Verwendung des v2 Authentifizierung Endpunktes authentifizieren Microsoft Graph Endpunkte](http://graph.microsoft.io/docs/authorization/converged_auth).



  > Ihr Feedback ist uns sehr wichtig. Verbinden Sie mit uns in Kontakt auf [Stapelüberlauf](http://stackoverflow.com/questions/tagged/office365). Markieren Sie Ihre Fragen mit [MicrosoftGraph] und [office365].








