# <a name="call-microsoft-graph-in-a-ruby-app"></a>Aufrufen von Microsoft Graph in einer app Ruby 

In diesem Artikel betrachten wir die minimalen Aufgaben erforderlich, um eine Access token Abrufen von Azure Active Directory (AD), und rufen Sie die Microsoft Graph-API. Wir verwenden Code aus dem [Office 365 Ruby verbinden Beispiel mithilfe von Microsoft Graph](https://github.com/microsoftgraph/ruby-connect-rest-sample) die wichtigsten Konzepte erläutern, die Sie in Ihrer app implementieren müssen.

![Office 365 verbinden Ruby Beispiel screenshot](./images/web-screenshot.png)

## <a name="overview"></a>Übersicht

Um die Microsoft Graph-API-aufrufen, muss Ihre app Ruby die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory
2. Umleiten des im Browser zu der Seite Anmeldung
3. Empfangen eines Autorisierungscodes in der Antwort-URL-Seite
4. Fordern Sie ein Zugriffstoken aus der Endpunkt-token
5. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API 

<!--<a name="register"/>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ dazu finden Sie im Abschnitt [Registrieren Ihrer Anwendung Server mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Geben Sie eine Route in Ihrer app Ruby als die **Sign-on URL** in Schritt 6. Im Fall von Beispiel für Connect, dies ist [`/auth/azureactivedirectory/callback`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L41).
* [Konfigurieren der **delegierten Berechtigungen** ](https://github.com/microsoftgraph/ruby-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) , die Ihre app benötigt. Beispiel für Connect erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung.

* Client-ID
* Ein gültiger-Schlüssel
* Eine Antwort-URL

Sie benötigen diese Werte als Parameter in der OAuth-Ablauf in Ihrer app.

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>Umleiten des im Browser zu der Seite Anmeldung

Ihre app muss im Browser zur Seite Anmeldung zum Abrufen eines Autorisierungscodes und weiterhin den OAuth-Ablauf umleiten.

In der Connect-Beispiel wird die Umleitung von der Bibliothek OmniAuth behandelt. Unsere app nur übergibt die Ausführung an das [`/auth/azureactivedirectory`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L30) Route vom OmniAuth verwaltet.

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>Empfangen eines Autorisierungscodes in der Antwort-URL-Seite

Nachdem der Benutzer auf Anzeichen für die Einwahl gibt der Ablauf der Browser zur URL Antwort in Ihrer app. Azure fügt einen Autorisierungscode an die Abfragezeichenfolge an. Das Connect-Beispiel verwendet die [`/auth/azureactivedirectory/callback`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L38) Route für diesen Zweck.

Der Autorisierungscode erfolgt der `code` Abfragezeichenfolgen-Variable. Beispiel für Connect speichert den Code in einer lokalen Variablen und kann später.

```ruby
code = params[:code]
```

<!--<a name="accesstoken"/>-->
## <a name="request-an-access-token-from-the-token-endpoint"></a>Fordern Sie ein Zugriffstoken aus der Endpunkt-token

Nachdem Sie den Autorisierungscode haben, können Sie sie an die Client-ID wichtige und Beantworten von URL-Werte, die Sie von Azure AD Zugriff anfordern token erhalten haben. 

> **Hinweis:** <br />
> Die Anforderung muss auch eine Ressource angeben, die wir nutzen möchten. Im Fall von Microsoft Graph, ist der Wert der `https://graph.microsoft.com`.

Beispiel für Connect delegiert erneut, diese Aufgabe in die Bibliothek OmniAuth. Die [`acquire_access_token`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L65) Funktion ruft die Bibliothek auf und übergibt den Code für die Authentifizierung gespeichert, die im vorherigen Abschnitt zusammen mit der Antwort URL, Client-ID Client Secret und Ressourcen-ID

```ruby
def acquire_access_token(auth_code, reply_url)
    AUTH_CTX.acquire_token_with_authorization_code(
                  auth_code,
                  reply_url,
                  CLIENT_CRED,
                  GRAPH_RESOURCE)
end
```

> **Hinweis:** <br />
> Die Client-ID und den geheimen Clientschlüssel dienen der `CLIENT_CRED` -Parameter im vorherigen Codeausschnitt.

<!--<a name="request"/>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. Ihre app muss das Zugriffstoken im **Authorization** -Header jeder Anforderung bereitstellen.

Beispiel für Connect sendet eine e-Mail mithilfe des **SendMail** -Endpunkts in der Microsoft Graph-API. Der Code befindet sich in der [`send_mail`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L82) Funktion. Dies ist der Code, der zeigt, wie der Zugriffscode im Authorization-Header gesendet.

```ruby
def send_mail
  # Used in the template
  @name = session[:name]
  @email = params[:specified_email]
  @recipient = params[:specified_email]
  @mailSent = false
  
  sendMailEndpoint = URI("#{GRAPH_RESOURCE}#{SENDMAIL_ENDPOINT}")
  http = Net::HTTP.new(sendMailEndpoint.host, sendMailEndpoint.port)
  http.use_ssl = true
  
  emailBody = File.read("app/assets/MailTemplate.html")
  emailBody.sub! "{given_name}", @name
  
  emailMessage = "{
          Message: {
          Subject: 'Welcome to Office 365 development with Ruby',
          Body: {
              ContentType: 'HTML',
              Content: '#{emailBody}'
          },
          ToRecipients: [
              {
                  EmailAddress: {
                      Address: '#{@recipient}'
                  }
              }
          ]
          },
          SaveToSentItems: true
          }"

  response = http.post(
    SENDMAIL_ENDPOINT, 
    emailMessage, 
    initheader = 
    {
      "Authorization" => "Bearer #{session[:access_token]}", 
      "Content-Type" => CONTENT_TYPE
    }
  )

  # The send mail endpoint returns a 202 - Accepted code on success
  if response.code == "202"
    @mailSent = true
  else
    @mailSent = false
    flash[:httpError] = "#{response.code} - #{response.message}"
  end
  
  render "callback"
end
```

> **Hinweis:** <br />
> Senden der Anforderung muss auch einen **Content-Type** -Header mit einem Wert von beispielsweise die Microsoft Graph-API akzeptiert `application/json;odata.metadata=minimal;odata.streaming=true`.

Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die API-Referenz zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

<!--## Additional resources

-  [Office 365 Ruby Connect sample using Microsoft Graph](https://github.com/microsoftgraph/ruby-connect-rest-sample)
-  [Office Dev Center](http://dev.office.com) 
-  [Microsoft Graph API reference](http://graph.microsoft.io/en-us/docs)-->
