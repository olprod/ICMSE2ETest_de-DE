


# <a name="overview-of-microsoft-graph"></a>Übersicht über Microsoft Graph

Microsoft Graph (zuvor aufgerufene Office 365 unified-API) stellt mehrere APIs von Microsoft Cloud Services über einen einzelnen REST-API-Endpunkt (**https://graph.microsoft.com**). Das Microsoft Graph können Sie früher schwierige oder komplexe Abfragen in einfache Navigation aktivieren. 
 
Die Microsoft Graph bietet Ihnen:

- Einen einheitlichen API-Endpunkt für den Zugriff auf aggregierte Daten aus mehreren Microsoft Cloud Services in einer einzelnen Antwort 
- Nahtlose Navigation zwischen Entitäten und die Beziehungen zwischen diesen 
- Zugriff auf Intelligence und Insights stammen aus der Microsoft-cloud

Und all das Verwenden einer einzelnen Authentifizierungstoken.

Die API können Sie feste Entitäten wie Benutzer, Gruppen, e-Mail, Nachrichten, Kalender, Aufgaben und Notizen, die von Diensten wie Outlook, OneDrive, Azure Active Directory, Planner, OneNote und andere Benutzer zugreifen. Sie können auch berechnete Beziehungen ermöglicht durch das Office-Diagramm (nur für kommerzielle Benutzer) abrufen, wie die Liste der Benutzer aus, denen Sie mit arbeiten oder die Dokumente, um Sie Trend.

Microsoft Graph werden zwei Endpunkte verfügbar gemacht. Ein Endpunkt im Allgemeinen /v1.0 und /beta eine Vorschau-Endpunkt.  Sie können in Ihrer Produktion Applikationen jedoch nicht /beta /v1.0 verwenden.  Die Preview-Endpunkt /beta ist, in dem wir bieten die neuesten Funktionen für Entwickler zum experimentieren, und geben Sie Feedback-APIs in Beta können jederzeit ändern und sind nicht für den Produktionseinsatz bereit.

<!--<a name="msg_queries"> </a>-->

##<a name="common-queries"></a>Allgemeine Abfragen

Es folgen einige Beispiele für allgemeine Abfragen mithilfe von Microsoft Graph-API:

| **Vorgang** | **Service-Endpunkt** |
|:--------------------------|:----------------------------------------|
|   Mein Profil ABRUFEN |    `https://graph.microsoft.com/v1.0/me` |
|   Meine Dateien ABRUFEN|   `https://graph.microsoft.com/v1.0/me/drive/root/children` |
|   Mein Foto ABRUFEN     | `https://graph.microsoft.com/v1.0/me/photo/$value` |
|   Meine e-Mail-Nachrichten erhalten MÖCHTEN |   `https://graph.microsoft.com/v1.0/me/messages` |
|   Hohe Priorität e-Mail erhalten MÖCHTEN | `https://graph.microsoft.com/v1.0/me/messages?$filter=importance%20eq%20'high'` |
|   Meinen Kalender ABRUFEN |   `https://graph.microsoft.com/v1.0/me/calendar` |
|   Mein Manager ABRUFEN  | `https://graph.microsoft.com/v1.0/me/manager` |
|   ABRUFEN Sie so ändern Sie die Datei foo.txt letzten Benutzer |  `https://graph.microsoft.com/v1.0/me/drive/root/children/foo.txt/lastModifiedByUser` |
|   ABRUFEN Sie unified Gruppen, denen ich Mitglied bin|   `https://graph.microsoft.com/v1.0/me/memberOf/$/microsoft.graph.group?$filter=groupTypes/any(a:a%20eq%20'unified')` |
|   ABRUFEN von Benutzern in meiner Organisation     | `https://graph.microsoft.com/v1.0/users` |
|   ABRUFEN von Unterhaltungen der Gruppe |   `https://graph.microsoft.com/v1.0/groups/<id>/conversations` |
|   ABRUFEN Sie Personen, die im Zusammenhang mit mir    | `https://graph.microsoft.com/beta/me/people` |
|   ABRUFEN von Dateien, um mich Trend |  `https://graph.microsoft.com/beta/me/trendingAround` |
|   ABRUFEN von Personen, denen ich arbeite     | `https://graph.microsoft.com/beta/me/workingWith` |
|   ABRUFEN von Meine Aufgaben    | `https://graph.microsoft.com/beta/me/tasks` |
|   ABRUFEN von Notizen |  `https://graph.microsoft.com/beta/me/notes/notebooks` |

<!-- <a name="msg_roof"> </a> -->

## <a name="all-office-365-data-under-one-roof"></a>Alle Office 365-Daten in einem

Das folgende Diagramm zeigt das Microsoft Graph Developer Stack und deren Funktionsweise.

![Microsoft Graph-API für Entwickler-Stapel.](./images/MicrosoftGraph_DevStack.png)

 >  Ihr Feedback ist uns sehr wichtig. Verbinden Sie mit uns in Kontakt auf [Stapelüberlauf](http://stackoverflow.com/questions/tagged/office365+or+microsoftgraph). Markieren Sie Ihre Fragen mit [MicrosoftGraph] und [office365].



