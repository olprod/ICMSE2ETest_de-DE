# <a name="call-microsoft-graph-in-an-aspnet-mvc-app"></a>Aufrufen von Microsoft Graph in einer ASP.NET MVC-app

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden Ihrer Anwendung zu Office 365, und rufen Sie die Microsoft Graph-API ein. In diesem Thema werden nicht von Grund auf eine app erstellen. Wir verwenden Code aus [Office 365 ASP.NET MVC verbinden Beispiel mit Microsoft Graph](https://github.com/microsoftgraph/aspnet-connect-rest-sample) die wichtigsten Konzepte erläutern, die Sie in Ihrer app implementieren müssen.

Es folgt ein Screenshot der Seite e-Mail-Nachrichten senden.

![Screenshot von Office 365 ASP.NET MVC-Beispiel](./images/O365AspNetMVCSendMailPageScreenshot.png)

## <a name="overview"></a>Übersicht

Zum Aufrufen der Microsoft Graph-API müssen Sie die folgenden Aufgaben ausführen.

1. Registrieren Sie die Anwendung in Azure Active Directory
2. Authentifizieren eines Benutzers ein, und rufen Sie eine Access-token durch Aufrufen von Methoden in der Bibliothek zu Azure AD-Authentifizierung für .NET. (ADAL)
3. Verwenden Sie ADAL, um ein Zugriffstoken abzurufen
4. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API
5. Trennen der Sitzung

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Finden Sie unter [Registrieren Ihrer Browser-based Web app mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/office/office365/HowTo/add-common-consent-manually#bk_RegisterWebApp) alternative Anweisungen, und behalten Sie Folgendes im Hinterkopf.

* Stellen Sie sicher, dass Sie Http://localhost:55065 angeben / als **URL anmelden**.
* Nach dem Registrieren Sie der Anwendung, die Ihre app Winkel benötigt [die **delegierten Berechtigungen** zu konfigurieren](https://github.com/microsoftgraph/aspnet-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) . Das Connect-Beispiel erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung, da Sie diese Werte so konfigurieren Sie in Ihrer app benötigen.

* Client-ID (eindeutig für die Anwendung)
* Taste (auch bekannt als clientgeheimnis)
* Eine Antwort-URL (auch bekannt als URL umleiten). In diesem Beispiel ist es Http://localhost:55065 /.

  > Hinweis: URL-Wert der Antwort wird automatisch mit der Sign-on URL-Wert, wenn Sie die Anwendung registrieren anzugeben.

<!--<a name="#auth"></a>-->
## <a name="authentication-in-the-connect-sample"></a>Authentifizierung in der Connect-Beispiel

Die Azure AD Authentication Library (ADAL) für .NET können Entwickler der Clientanwendung Benutzer zu authentifizieren, und klicken Sie dann Zugriffstoken API-Anrufe zu erhalten.  Sie können diese Bibliothek im ASP.NET MVC-Projekt über das **Verwalten von NuGet-Pakete** in Visual Studio einschließen.

Es folgt ein Screenshot der Startseite.

![Screenshot von Office 365 ASP.NET MVC-Beispiel](./images/O365AspNetMVCHomePageScreenshot.png)

Der authentifizierungsfluss kann auf zwei grundlegenden Schritten unterbrochen werden:

1. Anfordern eines Autorisierungscodes
2. Verwenden Sie Autorisierungscode, um ein Zugriffstoken anzufordern.

>  **Hinweis**: Sie erhalten auch eine Aktualisierung token zusammen mit der Zugriffstoken. Der Aktualisierungstoken können Sie ein neues Zugriffstoken erwerben, wenn das aktuelle Zugriffstoken läuft ab.

Beispiel für Connect verwendet die Werte der Azure-app-Registrierung und -ID des Benutzers zum Authentifizieren. Die ADAL Authentifizierung Fluss Anforderungen die Client-ID wichtige und URL (auch bekannt als umleitungs-URL) Sie in der Azure Registrierungsprozess erhalten Antworten.

Um die für einen Autorisierungscode anzufordern, zuerst Umleiten der app zu Azure AD-URL für die Autorisierung Anforderung wie folgt (Siehe HomeController.cs-Datei).


```c#
        public ActionResult Login()
        {
            if (string.IsNullOrEmpty(Settings.ClientId) || string.IsNullOrEmpty(Settings.ClientSecret))
            {
                ViewBag.Message = "Please set your client ID and client secret in the Web.config file";
                return View();
            }


            var authContext = new AuthenticationContext(Settings.AzureADAuthority);

            // Generate the parameterized URL for Azure login.
            Uri authUri = authContext.GetAuthorizationRequestURL(
                Settings.O365UnifiedAPIResource,
                Settings.ClientId,
                loginRedirectUri,
                UserIdentifier.AnyUser,
                null);

            // Redirect the browser to the login page, then come back to the Authorize method below.
            return Redirect(authUri.ToString());
        }

```
Wenn diese **Anmeldung** Methode aufgerufen wird, werden die app den Benutzer auf eine Anmeldeseite weitergeleitet. Dies wird die app zur Anmeldeseite dauern. Nachdem die Anmeldeinformationen des Benutzers erfolgreich authentifiziert werden, leitet Azure die app auf die umleitungs-URL im Code erwähnt, wie durch *LoginRedirectUri*gekennzeichnet. Diese Umleitung ist URL eine URL zu einer anderen Aktion in der ASP.NET MVC-app wie dargestellt.

```c#

 Uri loginRedirectUri => new Uri(Url.Action(nameof(Authorize), "Home", null, Request.Url.Scheme));

```
Die URL enthält außerdem den Autorisierungscode in Schritt 1 und 2 oben erwähnten.  Dies wird den Autorisierungscode aus der Anforderungsparameter abzurufen. Verwenden den Code Authorizationn, wird die app Azure AD um das Zugriffstoken abzurufen tätigen Sie einen Anruf. Nachdem wir das Zugriffstoken abzurufen, speichern wir es in der Sitzung, damit es für mehrere Anforderungen verwendet werden können.

Die autorisieren-Aktion in der URL-Umleitung erwähnten sieht folgendermaßen aus.

```c#
        public async Task<ActionResult> Authorize()
        {
            var authContext = new AuthenticationContext(Settings.AzureADAuthority);


            // Get the token.
            var authResult = await authContext.AcquireTokenByAuthorizationCodeAsync(
                Request.Params["code"],                                         // the auth 'code' parameter from the Azure redirect.
                loginRedirectUri,                                               // same redirectUri as used before in Login method.
                new ClientCredential(Settings.ClientId, Settings.ClientSecret), // use the client ID and secret to establish app identity.
                Settings.O365UnifiedAPIResource);

            // Save the token in the session.
            Session[SessionKeys.Login.AccessToken] = authResult.AccessToken;

            // Get info about the current logged in user.
            Session[SessionKeys.Login.UserInfo] = await UnifiedApiHelper.GetUserInfoAsync(authResult.AccessToken);

            return RedirectToAction(nameof(Index), "Message");

        }

```
>  **Hinweis**: Weitere Informationen zu autorisierungsflusses, finden Sie unter [Autorisierung Grant Codefluss] (https://msdn.microsoft.com/en-US/library/azure/dn645542.aspx)

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Nachdem der Benutzer auf Anzeichen für die Einwahl zeigt das Sample verbinden dem Benutzer eine Aktivität zum Senden einer e-Mail-Nachricht.  Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen.

Zum Beispiel die UnifiedApiHelper.cs-Datei enthält den Code, die:

1)  Abrufen von Informationen zu den aktuellen Anmeldungsbenutzer.  Die ``GetUserInfoAsync`` Methode nimmt ein einziges Argument (zugriffstokenwerts) stellen Sie einen Anruf an **https://graph.microsoft.com/v1.0/me** zum Abrufen von Informationen über den aktuellen Anmeldungsbenutzer.

 ```c#

        public static async Task<UserInfo> GetUserInfoAsync(string accessToken)
        {
            UserInfo myInfo = new UserInfo();

            using (var client = new HttpClient())
            {
                using (var request = new HttpRequestMessage(HttpMethod.Get, Settings.GetMeUrl))
                {
                    request.Headers.Accept.Add(Json);
                    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);

                    using (var response = await client.SendAsync(request))
                    {
                        if (response.StatusCode == HttpStatusCode.OK)
                        {
                            var json = JObject.Parse(await response.Content.ReadAsStringAsync());
                            myInfo.Name = json?["displayName"]?.ToString();
                            myInfo.Address = json?["mail"]?.ToString().Trim().Replace(" ", string.Empty);

                        }
                    }
                }
            }

            return myInfo;
        }

```



2)  Erstellen und Senden der Nachricht, die der Benutzer per e-Mail senden möchte. Die ``SendMessageAsync`` -Methode erstellt und sendet eine POST-Anforderung an den **https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail** Resource URL mithilfe der zugriffstokenwerts als eines der Argumente.


```c#

        public static async Task<SendMessageResponse> SendMessageAsync(string accessToken, SendMessageRequest sendMessageRequest)
        {
            var sendMessageResponse = new SendMessageResponse { Status = SendMessageStatusEnum.NotSent };

            using (var client = new HttpClient())
            {
                using (var request = new HttpRequestMessage(HttpMethod.Post, Settings.SendMessageUrl))
                {
                    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);
                    request.Content = new StringContent(JsonConvert.SerializeObject(sendMessageRequest), Encoding.UTF8, "application/json");
                    using (HttpResponseMessage response = await client.SendAsync(request))
                    {
                        if (response.IsSuccessStatusCode)
                        {
                            sendMessageResponse.Status = SendMessageStatusEnum.Sent;
                            sendMessageResponse.StatusMessage = null;
                        }
                        else
                        {
                            sendMessageResponse.Status = SendMessageStatusEnum.Fail;
                            sendMessageResponse.StatusMessage = response.ReasonPhrase;
                        }
                    }
                }
            }

            return sendMessageResponse;
        }

```


Die ``MessageController.cs `` -Datei enthält Code, der e-Mail-Nachrichten verwaltet. Beispielsweise die Schaltfläche **E-Mail senden** . Die ``SendMessageSubmit `` Methode sendet die Nachricht, wenn der Benutzer klickt auf die Schaltfläche **E-Mail senden** .


```c#

        public async Task<ActionResult> SendMessageSubmit(UserInfo userInfo)
        {
            // After Index method renders the View, user clicks Send Mail, which comes in here.
            EnsureUser(ref userInfo);

            // Send email using O365 unified API.
            var sendMessageResult = await UnifiedApiHelper.SendMessageAsync(
                (string)Session[SessionKeys.Login.AccessToken],
                GenerateEmail(userInfo));

            // Reuse the Index view for messages (sent, not sent, fail) .
            // Redirect to tell the browser to call the app back via the Index method.
            return RedirectToAction(nameof(Index), new RouteValueDictionary(new Dictionary<string,object>{
                { "Status", sendMessageResult.Status },
                { "StatusMessage", sendMessageResult.StatusMessage },
                { "Address", userInfo.Address },
            }));
        }

```


Das ``CreateEmailObject`` -Methode erstellt das Email-Objekt im erforderlichen Anforderung Format-Daten Vertrag, die der POST-Text erforderlich sind:


  ```c#

        private SendMessageRequest CreateEmailObject(UserInfo to, string subject, string body)
        {
            return new SendMessageRequest
            {
                Message = new Message
                {
                    Subject = subject,
                    Body = new MessageBody
                    {
                        ContentType = "Html",
                        Content = body
                    },
                    ToRecipients = new List<Recipient>
                    {
                        new Recipient
                        {
                            EmailAddress = new UserInfo
                            {
                                 Name =  to.Name,
                                 Address = to.Address
                            }
                        }
                    }
                },
                SaveToSentItems = true
            };

```

Einer anderen Aufgabe besteht darin, eine gültige Zeichenfolge von JSON Nachricht erstellen und senden Sie ihn an die ``https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail`` Endpunkt mithilfe einer HTTP POST-Anforderung. Anforderung legt fest, da der e-Mail-Text ist als HTML-Dokument gesendet werden, die ``ContentType`` Wert der e-Mail-Nachricht in HTML, und den Inhalt als JSON für die HTTP POST-Anforderung codiert. Die Datei UnifiedApiMessageModels.cs enthält Daten oder Schema Verträge zwischen diese app und die Office 365 unified API-Server.



```c#


    public class SendMessageResponse
    {
        public SendMessageStatusEnum Status { get; set; }
        public string StatusMessage { get; set; }
    }

    public class SendMessageRequest
    {
        public Message Message { get; set; }

        public bool SaveToSentItems { get; set; }
    }

    public class Message
    {
        public string Subject { get; set; }
        public MessageBody Body { get; set; }
        public List<Recipient> ToRecipients { get; set; }
    }
    public class Recipient
    {
        public UserInfo EmailAddress { get; set; }
    }

    public class MessageBody
    {
        public string ContentType { get; set; }
        public string Content { get; set; }
    }

    public class UserInfo
    {
        public string Name { get; set; }
        public string Address { get; set; }
    }

}

```
<!--<a name="logout"></a>-->
## <a name="disconnect-the-session"></a>Zum Trennen der Sitzung

Klickt der Benutzer **Trennen** auf e-Mail senden, wird der Benutzer der Sitzung abmelden sein. Der Code wird dies durch
* Deaktivieren die lokale Sitzung
* Umleiten des Browsers an den Endpunkt Abmeldung (damit Azure eigene Cookies löschen kann)

Die **Abmeldung** -Methode (Siehe HomeController.cs-Datei) zeigt, wie Sie dies tun.


```c#
        public ActionResult Logout()
        {
            Session.Clear();
            return Redirect(Settings.LogoutAuthority + logoutRedirectUri.ToString());
        }

```

##<a name="next-steps"></a>Nächste Schritte
Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die API-Referenz zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.
Machen Sie sich unsere anderen Beispielen für ASP.NET auf [GitHub](http://aka.ms/aspnetgraphsamples)ein.


