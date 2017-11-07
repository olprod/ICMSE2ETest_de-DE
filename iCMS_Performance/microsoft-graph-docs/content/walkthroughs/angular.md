# <a name="call-microsoft-graph-in-an-angular-app"></a>Rufen Sie in einer app Winkel Microsoft Graph 

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden Ihrer Anwendung zu Office 365, und rufen Sie die Microsoft Graph-API ein. Wir verwenden Code aus dem [Office 365 Winkel verbinden Beispiel mithilfe von Microsoft Graph](https://github.com/microsoftgraph/angular-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen.

![Office 365 Winkel verbinden Beispiel screenshot](./images/web-screenshot.png)

## <a name="prerequisites"></a>Voraussetzungen  

In diesem Thema wird Folgendes vorausgesetzt.

* Sie sind Probleme mit dem Lesen JavaScript und [AngularJS](https://angularjs.org/) Code.

## <a name="overview"></a>Übersicht

Zum Aufrufen der Microsoft Graph-API müssen Sie die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory
2. Konfigurieren von Azure Active Directory-Bibliothek für JavaScript (ADAL JS)
3. Verwenden Sie ADAL JS, um ein Zugriffstoken abzurufen
4. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ finden Sie im Artikel [Registrieren der Browser-based Web app mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterWebApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Stellen Sie sicher, dass Sie Http://127.0.0.1:8080 angeben / als **URL anmelden**.
* Nach dem Registrieren Sie der Anwendung, die Ihre app Winkel benötigt [die **delegierten Berechtigungen** zu konfigurieren](https://github.com/microsoftgraph/angular-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) . Das Connect-Beispiel erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie folgende Werte auf der Seite **Configure** der Azure auf, da Sie diese Werte in Ihrer app Winkel [ADAL JS](https://github.com/AzureAD/azure-activedirectory-library-for-js) konfigurieren benötigen.

* Client-ID (eindeutig für die Anwendung)
* Eine Antwort-URL (Http://127.0.0.1:8080 /)

<!--<a name="adal"></a>-->
## <a name="configure-azure-active-directory-library-for-javascript-adal-js"></a>Konfigurieren von Azure Active Directory-Bibliothek für JavaScript (ADAL JS)

[ADAL JS](https://github.com/AzureAD/azure-activedirectory-library-for-js) ist eine JavaScript-Bibliothek, die Sie vollständige Unterstützung für die Anmeldung auf Azure Active Directory-Benutzer in einer Seite Applications (SPAs) wie im Beispiel verbinden und token Management sowie andere Features bereitstellt. Um diese Bibliothek nutzen zu können, muss Ihre app Winkel einschließen, und konfigurieren sie.

Zählen Sie einfach die Bibliothek und seine Angular-spezifischen Modul mit dem Microsoft CDN.

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.7/js/adal.min.js"></script>
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.7/js/adal-angular.min.js"></script>
```

Im nächsten Schritt müssen Sie den ADAL JS-Dienst konfigurieren, wo Sie Ihre Winkel app-Abhängigkeiten konfigurieren. Das Connect-Beispiel wird die Konfiguration in [*public/app.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/scripts/app.js). 

Zum Konfigurieren von ADAL JS zuerst durch hinzufügen einen Verweis auf das ADAL Modul enthalten ```AdalAngular``` Ihrem Modul benötigen Matrix, und übergeben Sie ```adalAuthenticationServiceProvider``` in Ihrer ```config``` Funktion. Konfigurieren Sie die Bibliothek mit der ```init``` -Funktion, Client-ID Ihrer Anwendung übergeben und ein ```endpoints``` -Objekt, das deklariert, die APIs die Winkel app CORS muss, um Anfragen.

```javascript
// Initialize the ADAL provider with your clientID (found in the Azure Management Portal) and 
// the API URL (to enable CORS requests).
adalAuthenticationServiceProvider.init(
  {
    clientId: clientId,
    // The endpoints here are resources for cross origin requests.
    endpoints: {
      'https://graph.microsoft.com': 'https://graph.microsoft.com'
    }
  },
  $httpProvider
);
```

<!--<a name="accessToken"></a>-->
## <a name="use-adal-js-to-get-an-access-token"></a>Verwenden Sie ADAL JS, um ein Zugriffstoken abzurufen

Ihre app muss den Browser an eine Anmeldeseite umleiten, sodass der Benutzer anmelden und Ihre Anwendungszugriff auf ihre Daten gewähren kann. Beispiel für Connect nutzt ADAL JS, um diese Aufgabe zu behandeln. 

In einer von Ihrer Anwendung Domänencontrollern, indem er einfügt einen Verweis auf die ADAL Dienst zuerst hinzufügen ```adalAuthenticationService``` in der Controller und definieren Sie eine Funktion, die der Dienst verwendet ```login``` Funktion, die die Benutzeroberfläche aufgerufen werden kann. Beispiel für Connect wird in der Datei [*controllers/mainController.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/controllers/mainController.js) . 

```javascript
/**
  * Expose the login method from ADAL to the view.
  */
function connect() {
  adalAuthenticationService.login();
};
```

Wenn diese Funktion aufgerufen wird, werden Ihre Anwendung den Benutzer auf eine Anmeldeseite weitergeleitet. Nachdem sie anmelden und Ihrer app autorisieren, benötigen sie für Ihre Anwendung mit dem Zugriffstoken in der Abfragezeichenfolge zurückgegeben, die ADAL JS abgerufen und gespeichert werden. 

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. ADAL JS automatisch alle HTTP-Anfragen abfängt und Ihrer Zugriffstoken Ihnen hinzugefügt werden, damit Sie nicht manuell festlegen, Kopfzeile, bei Verwendung der Bibliothek. 

Beispiel für Connect sendet eine e-Mail mit dem ```me/sendMail``` Endpunkt in der Microsoft Graph-API in der Datei [*controllers/mainController.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/controllers/mainController.js) . 

Das Microsoft Graph ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden kann. Checken Sie die [API-Referenz](http://graph.microsoft.io/docs/api-reference/v1.0) zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

