# <a name="call-microsoft-graph-in-a-universal-windows-10-app"></a>Aufrufen von Microsoft Graph in einer universellen Windows-10-app

In diesem Artikel betrachten wir die minimalen Aufgaben erforderlich, um eine Access token Abrufen von Azure Active Directory (AD), und rufen Sie die Microsoft Graph. Wir verwenden Code aus dem [Office 365 verbinden-Beispiel für UWP mithilfe von Microsoft Graph](https://github.com/microsoftgraph/uwp-csharp-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen.

## <a name="sample-user-interface"></a>Beispiel-Benutzeroberfläche

Das Beispiel enthält eine sehr einfache Benutzeroberfläche, bestehend aus einer oberen Befehlsleiste, eine **Schaltfläche Verbinden**, eine Schaltfläche **e-Mail senden** und ein Textfeld, die mit E-mail-Adresse des angemeldeten Benutzers automatisch aufgefüllt wird, kann jedoch bearbeitet werden. Die Befehlsleiste enthält außerdem eine Schaltfläche, die ermöglicht es Entwicklern, hier finden Sie der app URI umleiten.

Die **e-Mail-Nachrichten senden** -Schaltfläche ist deaktiviert, wenn der Benutzer keine Verbindung hergestellt hat:

![Bildschirm mit der Schaltfläche Verbinden aktiviert und die Schaltfläche zum Senden von e-Mail deaktiviert](images/SignedOut.png)

Die oberste Befehlsleiste enthält eine Schaltfläche Trennen Wenn der Benutzer eine Verbindung hergestellt hat:

![Bildschirm mit den verbundenen Benutzer e-Mail-Adresse und die Schaltfläche zum Senden von e-Mail aktiviert](images/SignedIn.png)

Alle Benutzeroberflächenzeichenfolgen des Beispiels werden in der Datei Resources.resw im Ordner Objekte gespeichert.

## <a name="register-the-app"></a>Registrieren der app
 
Windows 10 enthält jede Anwendung mit einem eindeutigen URI und wird sichergestellt, dass Nachrichten an diesen URI nur an die Anwendung gesendet werden. Sie müssen Ihre app erstellen und dieser URI vom System generierte suchen, bevor Sie Ihre app registrieren. In diesem Beispiel finden Sie in der Datei AuthenticationHelper.cs diese Methode:

```c#
        public static string GetAppRedirectURI()
        {
            // Windows 10 universal apps require redirect URI in the format below. Add a breakpoint to this line and run the app before you register it, so that
            // you can supply the correct redirect URI value.
            return string.Format("ms-appx-web://microsoft.aad.brokerplugin/{0}", WebAuthenticationBroker.GetCurrentApplicationCallbackUri().Host).ToUpper();
        }
```

Dass die Methode wird von der Schaltfläche **Kopie umleiten URI** in der Stichprobe ausgelöst, jedoch können Sie auch das Muster im [AzureAD-NativeClient-UWP-WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM) -Beispiel, in denen die Zeichenfolge in der Deklaration der MainPage-Klasse definiert ist und Sie können mithilfe von Visual Studio-Debugger abrufen folgen. 

Führen Sie die Schritte im [registrieren und konfigurieren Sie die app](https://github.com/microsoftgraph/uwp-csharp-connect-rest-sample#register) im Beispiel Infodatei, um Ihre app zu registrieren, nachdem Sie den umleitungs-URI-Wert gelangt sind.

Sie benötigen den Client-ID-Wert aus der Seite zum **Konfigurieren** der Azure-Anwendung, wenn Sie Ihre app für die Authentifizierung konfigurieren.

## <a name="connect-to-microsoft-graph"></a>Verbinden mit Microsoft Graph

Im Beispiel wird der systemeigenen Windows 10 WebAccountManager-API zum Authentifizieren von Benutzern verwendet. Es folgt ein Muster ähnelt der zuvor beschriebenen, der [entwickeln Universal Apps für Windows Azure AD und Windows-API für die 10 Identität](http://blogs.technet.com/b/ad/archive/2015/08/03/develop-windows-universal-apps-with-azure-ad-and-the-windows-10-identity-api.aspx) Blog veröffentlichen und in der [AzureAD-NativeClient-UWP-WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM) -Beispiel veranschaulicht.

Objektebene enthält Schlüssel/Wert-Paaren, die Ihre app benötigen, um den Benutzer zu authentifizieren und Autorisieren der app eine e-Mail senden:

```xml
    <Application.Resources>
        <!-- Add your client id here. -->
        <x:String x:Key="ida:ClientID"><your client id></x:String>
        <x:String x:Key="ida:AADInstance">https://login.microsoftonline.com/</x:String>
        <!-- Add your developer tenant domain here. -->
        <x:String x:Key="ida:Domain">yourtenant.onmicrosoft.com</x:String>
    </Application.Resources>
```

Fügen Sie des Client-ID-Werts, den Sie erhalten haben, wenn Sie Ihre app als Wert für den Schlüssel **Ida: ClientID** registriert. Ändern Sie den Wert des Schlüssels **Ida: Domäne** , damit sie Ihre Office 365-Mandanten übereinstimmt.

Die Datei AuthenticationHelper.cs enthält alle des Codes Authentifizierung sowie zusätzliche Logik, die Benutzerinformationen und erzwingt Authentifizierung nur wenn der Benutzer von der app getrennt ist.

Das ``GetTokenHelperAsync`` -Methode in dieser Datei definiert ausgeführt wird, bei der Benutzer authentifiziert und anschließend bei jedem die app Microsoft Graph aufruft. Die erste Aufgabe besteht darin, einen Azure AD-Konto-Anbieter zu suchen:

```c#
           aadAccountProvider = await WebAuthenticationCoreManager.FindAccountProviderAsync("https://login.microsoft.com", authority);
```

Der Wert der ``authority`` verkettete Zeichenfolge erstellt aus zwei Werte in Objektebene gespeichert ist: der Wert des Schlüssels **Ida: AADInstance** plus den Wert des Schlüssels **Ida: Domäne** . Dadurch wird eine Mandanten-spezifischen Autorität erstellt. Sie können auch die Zeichenfolge "Organisationen" verwenden, wenn Sie Ihre app auf ein Azure AD-Mandant ausführen möchten.

Nachdem der Benutzer authentifiziert, die app speichert den Benutzer-ID-Wert im ``ApplicationData.Current.RoamingSettings``. Die ``GetTokenHelperAsync`` -Methode zuerst überprüft, um festzustellen, ob dieser Wert vorhanden ist, und wenn Ja, versucht wird, im Hintergrund zu authentifizieren:

```c#
            // Check if there's a record of the last account used with the app
            var userID = _settings.Values["userID"];

            if (userID != null)
            {

                WebTokenRequest webTokenRequest = new WebTokenRequest(aadAccountProvider, string.Empty, clientId);
                webTokenRequest.Properties.Add("resource", ResourceUrl);

                // Get an account object for the user
                userAccount = await WebAuthenticationCoreManager.FindAccountAsync(aadAccountProvider, (string)userID);


                // Ensure that the saved account works for getting the token we need
                WebTokenRequestResult webTokenRequestResult = await WebAuthenticationCoreManager.RequestTokenAsync(webTokenRequest, userAccount);
                if (webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.Success || webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.AccountSwitch)
                {
                    WebTokenResponse webTokenResponse = webTokenRequestResult.ResponseData[0];
                    userAccount = webTokenResponse.WebAccount;
                    token = webTokenResponse.Token;

                }
                else
                {
                    // The saved account could not be used for getting a token
                    // Make sure that the UX is ready for a new sign in
                    SignOut();
                }

            }
```

Die app verwendet den Microsoft Graph-Endpunkt-- **https://graph.microsoft.com/** --als der Ressourcenwert. Wenn er erstellt die ``WebTokenRequest`` verwendet den Client-ID-Wert, der Sie auf Objektebene hinzugefügt haben. Da die app bekannt, die Benutzer-ID ist und der Benutzer noch nicht getrennt wird, können die WebAccountManager-API suchen Sie das Benutzerkonto und übergeben es an die tokenanforderung. Die ``WebAuthenticationCoreManager.RequestTokenAsync`` -Methode gibt ein Zugriffstoken zurück, mit den entsprechenden Berechtigungen zugewiesen.

Findet die app keinen Wert für ``userID`` in Roamingeinstellungen, erstellt es eine ``WebTokenRequest`` erzwingt, den Benutzer über die Benutzeroberfläche authentifizieren:

```c#
            else
            {
                // There is no recorded user. Start a sign in flow without imposing a specific account.

                WebTokenRequest webTokenRequest = new WebTokenRequest(aadAccountProvider, string.Empty, clientId, WebTokenRequestPromptType.ForceAuthentication);
                webTokenRequest.Properties.Add("resource", ResourceUrl);

                WebTokenRequestResult webTokenRequestResult = await WebAuthenticationCoreManager.RequestTokenAsync(webTokenRequest);
                if (webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.Success)
                {
                    WebTokenResponse webTokenResponse = webTokenRequestResult.ResponseData[0];
                    userAccount = webTokenResponse.WebAccount;
                    token = webTokenResponse.Token;

                }
            }
```

Wenn ein Versuch, ein Token abzurufen erfolgreich ist die ``GetTokenHelperAsync`` Methode abgeschlossen ist, indem wichtige Benutzerinformationen in Roamingeinstellungen und klicken Sie dann den Wert zurückgibt, token gespeichert. Andernfalls ist er sichergestellt, dass Roamingeinstellungen werden null und gibt einen null-Wert zurück.

```c#
            // We succeeded in getting a valid user.
            if (userAccount != null)
            {
                // save user ID in local storage
                _settings.Values["userID"] = userAccount.Id;
                _settings.Values["userEmail"] = userAccount.UserName;
                _settings.Values["userName"] = userAccount.Properties["DisplayName"];

                return token;
            }

            // We didn't succeed in getting a valid user. Clear the app settings so that another user can sign in.
            else
            {
                
                SignOut();
                return null;
            }
```

## <a name="send-an-email-with-microsoft-graph"></a>Senden Sie eine e-Mail mit Microsoft Graph

Die MailHelper.cs-Datei enthält den Code, der erstellt und sendet eine e-Mail an. Es besteht aus einer einzelnen Methode-- ``ComposeAndSendMailAsync`` –, die erstellt und sendet eine POST-Anforderung an den Endpunkt **https://graph.microsoft.com/v1.0/me/microsoft.graph.SendMail** . 

Die ``ComposeAndSendMailAsync`` Methode enthält drei Zeichenfolgenwerte-- ``subject``, ``bodyContent``, und ``recipients`` –, die von der Datei MainPage.xaml.cs wird übergeben. Die ``subject`` und ``bodyContent`` Zeichenfolgen gespeichert sind, sowie alle anderen Benutzeroberflächenzeichenfolgen in der Datei Resources.resw. Die ``recipients`` Zeichenfolge stammt aus dem Adressfeld auf die app-Benutzeroberfläche. 

Da der Benutzer potenziell mehr als eine Adresse weiterleiten kann, die erste Aufgabe besteht darin, teilen der ``recipients`` Zeichenfolge in einen Satz von EmailAddress-Objekte, die dann in der POST-Text der Anforderung übergeben werden können:

```c#
            // Prepare the recipient list
            string[] splitter = { ";" };
            var splitRecipientsString = recipients.Split(splitter, StringSplitOptions.RemoveEmptyEntries);
            string recipientsJSON = null;

            int n = 0;
            foreach (string recipient in splitRecipientsString)
            {
                if ( n==0)
                recipientsJSON += "{'EmailAddress':{'Address':'" + recipient.Trim() + "'}}";
                else
                {
                    recipientsJSON += ", {'EmailAddress':{'Address':'" + recipient.Trim() + "'}}";
                }
                n++;
            }
```

Der zweite Vorgang ist das Erstellen eines gültigen Objekts JSON-Nachricht und senden Sie sie an den Endpunkt **me/microsoft.graph.SendMail** über eine HTTP POST-Anforderung. Da die ``bodyContent`` Zeichenfolge ist ein HTML-Dokument, die Anforderung wird von der **ContentType** -Wert auf HTML. Beachten Sie außerdem den Anruf an ``AuthenticationHelper.GetTokenHelperAsync`` um sicherzustellen, dass wir eine frische Zugriffstoken in der Anforderung übergeben haben.

```c#
                HttpClient client = new HttpClient();
                var token = await AuthenticationHelper.GetTokenHelperAsync();
                client.DefaultRequestHeaders.Add("Authorization", "Bearer " + token);

                // Build contents of post body and convert to StringContent object.
                // Using line breaks for readability.
                string postBody = "{'Message':{" 
                    +  "'Body':{ " 
                    + "'Content': '" + bodyContent + "'," 
                    + "'ContentType':'HTML'}," 
                    + "'Subject':'" + subject + "'," 
                    + "'ToRecipients':[" + recipientsJSON +  "]}," 
                    + "'SaveToSentItems':true}";

                var emailBody = new StringContent(postBody, System.Text.Encoding.UTF8, "application/json");

                HttpResponseMessage response = await client.PostAsync(new Uri("https://graph.microsoft.com/v1.0/me/microsoft.graph.SendMail"), emailBody);

                if ( !response.IsSuccessStatusCode)
                {

                    throw new Exception("We could not send the message: " + response.StatusCode.ToString());
                }
```

Nachdem Sie eine erfolgreiche REST-Anforderung getroffen haben, haben Sie die drei Schritte für die Interaktion mit Microsoft Graph durchgeführt: app-Registrierung, Benutzerauthentifizierung und Durchführen von REST-Anforderung.


<!--## Additional resources

* [Develop Windows Universal Apps with Azure AD and the Windows 10 Identity API](http://blogs.technet.com/b/ad/archive/2015/08/03/develop-windows-universal-apps-with-azure-ad-and-the-windows-10-identity-api.aspx)
* [AzureAD-NativeClient-UWP-WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM)
* [Office Dev Center](http://dev.office.com)-->

