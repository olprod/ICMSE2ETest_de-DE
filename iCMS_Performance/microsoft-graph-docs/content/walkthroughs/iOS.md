# <a name="call-microsoft-graph-in-an-ios-app"></a>Rufen Sie Microsoft Graph in einer iOS-App

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden Ihrer Anwendung mit Office 365 und die Microsoft Graph-API-aufrufen. Wir verwenden Code aus der [Ios-Objectivec-verbinden-Rest-Sample](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen. Diese Beispiele behandelt die Core-Grundlagen für die Authentifizierung mit die Microsoft Azure Active Directory (AAD), und machen einen einfachen Dienst für den Office 365-Mail-Dienst mithilfe der Microsoft Graph-API (Senden einer e-Mails) aufrufen. Es wird empfohlen, dass Sie Klonen oder Laden Sie das Projekt vom Repository zu diesem Artikel. 


Dieser Artikel verweist auf die [Microsoft Azure Active Directory Authentifizierung Library (ADAL) für IOS- und OSX ausgeführt WERDEN](https://github.com/AzureAD/azure-activedirectory-library-for-objc), und das Beispiel [Ios-Objectivec-verbinden-Rest-Sample](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample) authentifiziert sich mit dieser Bibliothek. Finden Sie unter diesem Repository für Weitere Informationen zur Verwendung und Implementierung in Ihrer iOS-Projekt.


## <a name="overview"></a>Übersicht

Um die Microsoft Graph-API aufzurufen, muss Ihre iOS-app folgende Schritte durchführen:

1. Registrieren Sie die Anwendung aus die Microsoft Azure Active Directory (AD).
2. Anfordern und ein Zugriffstoken aus dem Azure Active Directory zu erwerben.
3. Verwenden Sie das Zugriffstoken in eine REST-Anforderung an die Microsoft Graph-API. 



## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ finden Sie im Abschnitt **Registrieren der native app mit dem Azure-Verwaltungsportal** im Artikel [manuell registrieren Ihrer app mithilfe von Azure AD, damit sie Office 365-APIs zugreifen kann](https://msdn.microsoft.com/en-us/office/office365/howto/add-common-consent-manually) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Für die Registrierung müssen Sie eine umleitungs-URI angeben. Diese ein erforderlicher Wert, der angibt, in dem ein Benutzer nach einer erfolgreichen Authentifizierungsversuch umgeleitet werden soll. Wenn Sie nicht die richtige umleitungs-URI angeben, schlägt der Authentifizierungsanforderung fehl.
* Bei der Registrierung muss die app der **Nachricht senden als angemeldeten Benutzer die Berechtigung** für das **Microsoft Graph**erteilt werden.  


Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung.

* Client-ID
* Umleiten von URI

Sie benötigen diese Werte so konfigurieren Sie den OAuth-Ablauf in Ihrer app. 

## <a name="request-and-acquire-an-access-token-from-azure-ad"></a>Fordern Sie an und erhalten Sie ein Zugriffstoken von Azure AD

Anfordern und ein Zugriffstoken für Anrufe bei der Microsoft Graph-API zu erhalten, können **AcquireAuthTokenWithResource:clientId:redirectUri:completionBlock:** von der [Microsoft Azure Active Directory Authentifizierung Library (ADAL) für IOS- und OSX](https://github.com/AzureAD/azure-activedirectory-library-for-objc)bereitgestellt. In diesem SDK finden Ihre Anwendung den vollen Funktionsumfang von Microsoft Azure AD, einschließlich der Branche Standardprotokoll Unterstützung für OAuth2, Web-API-Integration mit Zustimmung des Benutzers Ebene, und zwei Faktor unterstützte Authentifizierung.

Diese Methode verwendet den folgenden Parameter:

1. **ResourceID** - ist dies die angeforderte Ressource, den, die Sie zugreifen möchten. Beispielsweise möchten wir die Microsoft Graph-API zuzugreifen, sodass dieser Wert "https://graph.microsoft.com".
2. **ClientID** - der angegebene Wert auf Ihre app zu identifizieren, wenn Sie die Registrierung AAD abgeschlossen haben.
3. **RedirectURI** - erneut, dies ein erforderlicher Wert, der angibt, in dem ein Benutzer nach einer erfolgreichen Authentifizierungsversuch umgeleitet werden soll.


Zunächst müssen Sie einen Authentifizierung Kontext festzulegen. Hierdurch wird lediglich die Behörde, wo Sie Ihre Zugriffstoken aus abrufen möchten. In unserem Fall ist es von einem Mandanten AAD, und Sie müssen sie deklarieren:

    @property (strong,    nonatomic) ADAuthenticationContext *context;

Initialisieren Sie es dann mit dem Standort der Behörde ("https://login.microsoftonline.com/common"):

    self.context = [ADAuthenticationContext authenticationContextWithAuthority:self.authority]; 


In der [Ios-Objectivec-verbinden-Rest-Sample](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample) Zwecke Beispiel wir Singleton Authentifizierungsklasse (**CustomTargetNameDictionary**) für Demo erstellt, die mit der Zertifizierungsstelle und die erforderlichen Parameter initialisiert wird. Diese Klasse ist lediglich ein Beispiel zum Ansatz für des Authentifizierung Workflows. Ein Codesegment von Interesse: 



    - (void)acquireAuthTokenWithResource:(NSString *)resourceID
                            clientID:(NSString*)clientID
                         redirectURI:(NSURL*)redirectURI
                          completion:(void (^)(ADAuthenticationError *error))completion {
    
    NSLog(@"acquireAuthTokenWithResource");
    [self.context acquireTokenWithResource:resourceID
                                  clientId:clientID
                               redirectUri:redirectURI
                           completionBlock:^(ADAuthenticationResult *result) {
                               NSLog(@"Completion");
                               
                               if (result.status !=AD_SUCCEEDED){
                                   NSLog(@"error");
                                   completion(result.error);
                               }
                               
                               else{
                                   NSLog(@"complete!");
                                   self.accessToken = result.accessToken;
                                   self.userID = result.tokenCacheStoreItem.userInformation.userId;
                                   completion(nil);
                               }
                           }];


Erstmalig diese app ausgeführt wird, wird die Authentifizierung Manager sendet eine Anforderung der Behörde dem Sie eine Anmeldeseite umleitet. Fügen Sie Ihre Anmeldeinformationen und die Antwort enthält das Ergebnis der Authentifizierung. Wenn sie erfolgreich war, wird es auch Ihre Aktualisierung und Access Token enthalten. Zweites Mal dieser Anwendung gestartet wird, und verwenden Sie den Zugriff oder Aktualisieren von Token im Cache Clientanforderungen authentifiziert wird vorausgesetzt, dass Sie Ihre Tokencache und Cookies, die Authentication Manager deaktivieren nicht. Dies führt zu einem Aufruf an den Dienst ein Zugriffstoken abrufen möchten. 


## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. Ihre app muss das Zugriffstoken an den HTTP-Anforderungsheader unter **Autorisierung**anfügen.

Im Beispiel [Ios-Objectivec-verbinden-Rest-Sample](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample) sendet eine e-Mail mit den SendMail-Endpunkt in der Microsoft Graph-API. In diesem Fall unsere in unserem Beispiel wir eine Singleton-Authentifizierung-Klasse (CustomTargetNameDictionary), die initialisiert wird mit dem Zugriffstoken erstellt. Wir benötigen das Zugriffstoken an unsere Anforderung erstellen.



    - (void)sendMailREST {
    
    AuthenticationManager *authManager = [AuthenticationManager sharedInstance];

    //Helper method used to construct the email message
    NSData *postData = [self mailContent];
    
    //Microsoft Graph API endpoint for sending mail
    NSMutableURLRequest *request = [[NSMutableURLRequest alloc] initWithURL:[NSURL URLWithString:@"https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail"]];

    [request setHTTPMethod:@"POST"];
    [request setValue:@"application/json" forHTTPHeaderField:@"Content-Type"];
    [request setValue:@"application/json, text/plain, */*" forHTTPHeaderField:@"Accept"];
    
    // Access token required for request header
    NSString *authorization = [NSString stringWithFormat:@"Bearer %@", authManager.accessToken];
    [request setValue:authorization forHTTPHeaderField:@"Authorization"];
    [request setHTTPBody:postData];

    NSURLConnection *conn = [[NSURLConnection alloc] initWithRequest:request delegate:self];
    
    if(conn) {
        NSLog(@"Connection Successful");
    } else {
        NSLog(@"Connection could not be made");
    }
    
    [conn start];

Wie Sie sehen können, wird die Antwort mit den NSURLConnection Delegaten, nämlich die NSURLConnectionDelegate und NSURLConnectionDataDelegate behandelt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Zugriffstoken abgelaufen ist oder der Testzeitraum, Sie die ADAuthenticationContext können **AcquireTokenSilentWithResource:clientId:redirectUri:completionBlock:** um ein neues Zugriffstoken zu erwerben. Die Verwendung wird im Beispiel für [Ios-Objectivec-verbinden-Rest-Sample](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample) behandelt. Darüber hinaus finden Sie den Code, um Ihre Tokencache und gespeicherten Cookies zu deaktivieren.  

Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die [API-Referenz](http://graph.microsoft.io/docs/api-reference/v1.0) zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

