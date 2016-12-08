# <a name="call-microsoft-graph-in-an-android-app"></a>Rufen Sie Microsoft Graph in einer Android-app

In diesem Artikel betrachten wir die minimalen Aufgaben erforderlich, um eine Access token Abrufen von Azure Active Directory (AD), und rufen Sie die Microsoft Graph. Wir verwenden Code aus dem [Office 365 Android verbinden Beispiel mithilfe von Microsoft Graph](https://github.com/microsoftgraph/android-java-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen.

Die folgende Abbildung zeigt die Beispiel-app senden Mail-Aktivität, die angezeigt wird, nachdem ein Benutzer eine Verbindung zu Office 365 hergestellt hat.

![Office 365 Android Unified API verbinden Beispiel screenshot](./images/AndroidConnect.png)

## <a name="overview"></a>Übersicht

Zum Aufrufen der Microsoft Graph-API führt das [Office 365 Android verbinden Beispiel](https://github.com/microsoftgraph/android-java-connect-rest-sample) folgende Aufgaben aus.

1. Authentifizieren eines Benutzers ein, und rufen Sie eine Access-token durch Aufrufen von Methoden für die Azure Active Directory-Bibliothek.
2. Erstellt eine e-Mail-Nachricht-Anforderung als REST Vorgang für den Endpunkt Microsoft Graph-API.

<!--<a name="register"/>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ finden Sie im Abschnitt **Registrieren der native app mit dem Azure-Verwaltungsportal** im Artikel [manuell registrieren Ihrer app mithilfe von Azure AD, damit sie Office 365-APIs zugreifen kann](https://msdn.microsoft.com/en-us/office/office365/howto/add-common-consent-manually) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Konfigurieren Sie die **delegierten Berechtigungen** , die Ihre app benötigt. Beispiel für Connect erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung.

* Client-ID
* Eine umleitungs-URL

Sie benötigen diese Werte so konfigurieren Sie den Code für die Authentifizierung in Ihrer app.

## <a name="gradle-dependencies-in-the-connect-sample"></a>Gradle Abhängigkeiten in der Connect-Beispiel
Im Beispiel übernimmt die Bibliotheken, die im folgenden Codeausschnitt build.gradle Abhängigkeiten

```gradle
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:22.1.1'

    // Azure Active Directory Library
    compile 'com.microsoft.aad:adal:1.1.7'

    // Retrofit + custom HTTP
    compile 'com.squareup.okhttp:okhttp-urlconnection:2.0.0'
    compile 'com.squareup.okhttp:okhttp:2.0.0'
    compile 'com.squareup.retrofit:retrofit:1.9.0'
}

```
<!--<a name="authenticate"/>-->
## <a name="authentication-in-the-connect-sample"></a>Authentifizierung in der Connect-Beispiel
Beispiel für Connect verwendet die Werte der Azure-app-Registrierung und -ID des Benutzers zum Authentifizieren. Es gibt zwei Authentifizierung Verhaltensweisen von Beispiel für Connect unterstützt.

* Authentifizierung dazu aufgefordert werden. Verwendet, wenn ein Benutzer den, dem ID in nicht zwischengespeichert ist, auf dem Android-Gerät Voreinstellungen gespeichert
* Automatische Authentifizierung. Verwendet, wenn eine Benutzer-ID zwischengespeichert wird und Bestätigung nicht erforderlich ist.

Die [AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java) -Klasse stellt eine `isConnected()` Hilfsmethode finden jede zwischengespeicherte Benutzer-ID und das Authentifizierung zu verwendende Verhalten, bestimmen.


```java
    private boolean isConnected(){
        SharedPreferences settings = this
                .mContextActivity
                .getSharedPreferences(PREFERENCES_FILENAME, Context.MODE_PRIVATE);

        return settings.contains(USER_ID_VAR_NAME);
    }

```

Mit entweder das Verhalten der ADAL Authentifizierung flow muss die Client-ID und umleiten URL, die Sie in der Azure Registrierungsprozess abzurufen. Das Beispiel behält diese Zeichenfolgen in Quellcode und ruft sie ab, bevor das Authentifizierung Manager-Objekt den Benutzer authentifiziert.

[Constants.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/Constants.java) -Schnittstelle stellt zwei statische Zeichenfolgen für Client-ID und URL umleiten.

```java
interface Constants {
    String AUTHORITY_URL = "https://login.microsoftonline.com/common";
    // Update these two constants with the values for your application:
    String CLIENT_ID = "<Your client id here>";
    String REDIRECT_URI = "<Your redirect uri here>";
    String UNIFIED_API_ENDPOINT = "https://graph.microsoft.com/v1.0/";
    String UNIFIED_ENDPOINT_RESOURCE_ID = "https://graph.microsoft.com/";
}
```
### <a name="construct-the-authenticationmanager-class"></a>Konstrukt der CustomTargetNameDictionary-Klasse
[AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java) Konstruktor keine Argumente akzeptiert, jedoch eine Klasse Zeichenfolgenfeld aus der Constants.java-Datei durch die URL des Endpunkts Diagramm festgelegt. Diese Ressourcenzeichenfolge wird für beide Verhaltensweisen Authentifizierung verwendet.

```java
    private AuthenticationManager() {
        mResourceId = Constants.UNIFIED_ENDPOINT_RESOURCE_ID;
    }
```

### <a name="prompted-authentication"></a>Aufforderung Authentifizierung

Die [AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java) -Klasse bietet ein `authenticatePrompt()` -Methode, um das Zugriffstoken für REST-Aufrufen für den einheitlichen Endpunkt verwendete erwerben.

Die Bibliothek ADAL `acquireToken()` Methode ist asynchron. Die Methodenargumente Hinzufügen eines Verweises auf den Kontext der aktuellen Aktivität zusammen mit der Ressource, die Client-ID und umleitungs-URL. Die aktuelle Aktivität Referenz ermöglicht die ADAL Bibliothek ein Anmeldeinformationen Herausforderung Zeichenblatt in der Aktivität anzeigt.
Wenn die Authentifizierung erfolgreich ist, ruft die ADAL Bibliothek die `onSuccess()` Rückruf. Dieser Rückruf führt zwei Schritte

* Speichert das Zugriffstoken in `mAccessToken`. Bei REST, eine e-Mail-Nachricht senden anrufen, wird im Beispiel dieses Zugriffstoken in eine Authorization-Kopfzeile.
* Speichert die Benutzer-ID in den gespeicherten Voreinstellungen.


```java
    /**
     * Calls acquireToken to prompt the user for credentials.
     *
     * @param authenticationCallback The callback to notify when the processing is finished.
     */
    private void authenticatePrompt(final AuthenticationCallback<AuthenticationResult> authenticationCallback) {
        getAuthenticationContext().acquireToken(
                this.mContextActivity,
                this.mResourceId,
                Constants.CLIENT_ID,
                Constants.REDIRECT_URI,
                PromptBehavior.Always,
                new AuthenticationCallback<AuthenticationResult>() {
                    @Override
                    public void onSuccess(final AuthenticationResult authenticationResult) {
                        if (authenticationResult != null) {
                            if (authenticationResult.getStatus() == AuthenticationStatus.Succeeded) {
                                setUserId(authenticationResult.getUserInfo().getUserId());
                                mAccessToken = authenticationResult.getAccessToken();
                                authenticationCallback.onSuccess(authenticationResult);
                            } else {
                                // We need to make sure that there is no data stored with the failed auth
                                AuthenticationManager.getInstance().disconnect();
                                // This condition can happen if user signs in with an MSA account
                                // instead of an Office 365 account
                                authenticationCallback.onError(
                                        new AuthenticationException(
                                                ADALError.AUTH_FAILED,
                                                authenticationResult.getErrorDescription()));
                            }
                        } else {
                            // I could not authenticate the user silently,
                            // falling back to prompt the user for credentials.
                            authenticatePrompt(authenticationCallback);
                        }
                    }

                    @Override
                    public void onError(Exception e) {
                        // We need to make sure that there is no data stored with the failed auth
                        AuthenticationManager.getInstance().disconnect();
                        authenticationCallback.onError(e);
                    }
                }
        );
    }

```

###<a name="silent-authentication"></a>Automatische Authentifizierung
Die [AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java) -Klasse bietet ein `authenticateSilent()` -Methode, um das Zugriffstoken für REST-aufrufen unified Endpunkt verwendete erwerben.

Die Bibliothek ADAL `acquireTokenSilent()` Methode ist asynchron. Zusätzlich zu den Azure Registrierung Client-ID und Ressourcen-Id dauert die Benutzer-ID, die in den freigegebenen Voreinstellungen gespeichert ist. Die Hilfsmethode `getUserId()` Ruft die Benutzer-ID aus dem Speicher ab.

Wenn die Authentifizierung erfolgreich ist, wird die `onSuccess()` -Methode aufgerufen wird. `onSuccess`Speichert das Zugriffstoken in `mAccessToken`. Bei REST, eine e-Mail-Nachricht senden anrufen, wird im Beispiel dieses Zugriffstoken in eine Authorization-Kopfzeile.
```java
    /**
     * Calls acquireTokenSilent with the user id stored in shared preferences.
     * In case of an error, it falls back to {@link AuthenticationManager#authenticatePrompt(AuthenticationCallback)}.
     *
     * @param authenticationCallback The callback to notify when the processing is finished.
     */
    private void authenticateSilent(final AuthenticationCallback<AuthenticationResult> authenticationCallback) {
        getAuthenticationContext().acquireTokenSilent(
                this.mResourceId,
                Constants.CLIENT_ID,
                getUserId(),
                new AuthenticationCallback<AuthenticationResult>() {
                    @Override
                    public void onSuccess(final AuthenticationResult authenticationResult) {
                        if (authenticationResult != null) {
                            if (authenticationResult.getStatus() == AuthenticationStatus.Succeeded) {
                                mAccessToken = authenticationResult.getAccessToken();
                                authenticationCallback.onSuccess(authenticationResult);
                            } else {
                                authenticationCallback.onError(
                                        new Exception(authenticationResult.getErrorDescription()));

                            }
                        } else {
                            // I could not authenticate the user silently,
                            // falling back to prompt the user for credentials.
                            authenticatePrompt(authenticationCallback);
                        }
                    }

                    @Override
                    public void onError(Exception e) {
                        // I could not authenticate the user silently,
                        // falling back to prompt the user for credentials.
                        authenticatePrompt(authenticationCallback);
                    }
                }
        );
    }

```
<!--<a name="sendmail"/>-->
## <a name="send-an-email-message-using-office-365"></a>Senden einer e-Mail-Nachricht mithilfe von Office 365

Nachdem der Benutzer auf Anzeichen für in Azure zeigt das Sample verbinden dem Benutzer eine Aktivität zum Senden einer e-Mail-Nachricht. Beispiel für Connect verwendet die [MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java) -Klasse, um die Nachricht zu senden, wenn die Benutzer klickt auf die Schaltfläche e-Mail senden.

### <a name="rest-adapter-helper-class"></a>REST-Adapter Hilfsklasse
Die [RESTHelper.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/RESTHelper.java) -Klasse bietet eine Methode zum Einfügen einer Authorization-Kopfzeile in jedem REST-Aufruf im Beispiel macht. Anschließend wird das Zugriffstoken vom Authentifizierungsmanager bereitgestellt.

```java
       //This method catches outgoing REST calls and injects the Authorization and host headers before
        //sending to REST endpoint
        RequestInterceptor requestInterceptor = new RequestInterceptor() {
            @Override
            public void intercept(RequestFacade request) {
                final String token = mAccessToken;
                if (null != token) {
                    request.addHeader("Authorization", "Bearer " + token);
                }
            }
        };
```
### <a name="unifiedapicontroller-class"></a>UnifiedAPIController-Klasse
Die Klasse [MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java) generiert, die REST-Anforderung in der `sendMail()` Methode.


```java
    /**
     * Sends an email message using the Unified API on Office 365. The mail is sent
     * from the address of the signed in user.
     *
     * @param emailAddress The recipient email address.
     * @param subject      The subject to use in the mail message.
     * @param body         The body of the message.
     * @param callback     UI callback to be invoked by Retrofit call when
     *                     operation completed
     */
    public void sendMail(
            final String emailAddress,
            final String subject,
            final String body,
            Callback<Void> callback) {
        ensureService();
        // Use the Unified API service on Office 365 to create the message.
        mUnifiedAPIService.sendMail(
                "application/json",
                createMailPayload(
                        subject,
                        body,
                        emailAddress),
                callback);
    }

```
### <a name="the-unifiedapiservice-interface"></a>Die UnifiedAPIService-Schnittstelle
Die [MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java) -Schnittstelle bietet Methodensignaturen für die REST-Aufrufe durch das Beispiel Nachrüstteilen Anmerkungen mit.

```java
    @POST("/me/sendMail")
    void sendMail(
            @Header("Content-type") String contentTypeHeader,
            @Body TypedString mail,
            Callback<Void> callback);


```

## <a name="next-steps"></a>Nächste Schritte
Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die [Microsoft Graph-Dokumentation](http://graph.microsoft.io/docs) zu untersuchen, was Sie mit der Microsoft Graph-API ausgeführt werden können.

Wir haben viele Android-Beispiele für Office 365 veröffentlicht. Jedes dieser Beispiele für die Konzepte, die eine Einführung in das Beispiel für Connect zusammenstellen. Wenn Sie mehr erreichen möchten mit Ihrer Android-apps finden Sie unter [mehrere der unsere Android-Beispiele für Office 365](http://aka.ms/androidgraphsamples) in der Organisation Office GitHub.
 
