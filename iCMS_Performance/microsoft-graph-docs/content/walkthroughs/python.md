# <a name="call-microsoft-graph-in-a-python-app"></a>Aufrufen von Microsoft Graph in einer Python-app 

In diesem Artikel betrachten wir die mindestens erforderlichen Aufgaben zum Verbinden Ihrer Anwendung zu Office 365, und rufen Sie die Microsoft Graph-API ein. Wir verwenden Code aus dem [Office 365 Python verbinden Beispiel mithilfe von Microsoft Graph](https://github.com/microsoftgraph/python3-connect-rest-sample) , um die wichtigsten Konzepte erläutert werden, die Sie in Ihrer app implementieren müssen.

![Office 365 verbinden Python Beispiel screenshot](./images/web-screenshot.png)

##  <a name="prerequisites"></a>Voraussetzungen

In diesem Thema wird Folgendes vorausgesetzt:

* Sie vertraut sind Python-Code zu lesen.
* Sie sind mit OAuth-Konzepten vertraut.

## <a name="overview"></a>Übersicht

Ihre app Python muss die folgenden Aufgaben ausführen, um die Microsoft Graph-API aufzurufen.

1. Registrieren Sie die Anwendung in Azure Active Directory
2. Umleiten des im Browser zu der Anmeldeseite
3. Empfangen eines Autorisierungscodes in der Antwort-URL-Seite
4. Fordern Sie ein Zugriffstoken aus dem Endpunkt Ausstellen von token
5. Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API 

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>Registrieren Sie die Anwendung in Azure Active Directory

Bevor Sie mit Office 365 arbeiten können, müssen Sie Ihre Anwendung registrieren und Festlegen von Berechtigungen zum Verwenden von Microsoft Graph-Dienste.
Mit nur wenigen Mausklicks können Sie Ihre Anwendung Zugriff auf einen Benutzer arbeiten oder Schule Konto mit dem [Anwendung Registration-Tool](https://dev.office.com/app-registration)registrieren. Um ihn zu verwalten, die Sie benötigen, fahren Sie mit der [Microsoft Azure-Verwaltungsportal](https://manage.windowsazure.com)

Alternativ dazu finden Sie im Abschnitt [Registrieren Ihrer Anwendung Server mit dem Azure-Verwaltungsportal](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp) Anweisungen zum manuell registrieren der app, Bedenken Sie Folgendes ein:

* Stellen Sie sicher, dass Sie Http://127.0.0.1:8000/verbinden/Get_token angeben/als **URL anmelden**.
* Nach dem Registrieren Sie der Anwendung, die Ihre app Python benötigt [die **delegierten Berechtigungen** zu konfigurieren](https://github.com/microsoftgraph/python3-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure) . Das Connect-Beispiel erfordert die Berechtigung **Senden als angemeldeten Benutzers** .

Beachten Sie die folgenden Werte in der Seite zum **Konfigurieren** der Azure-Anwendung, da Sie diese Werte zum Konfigurieren des OAuth-Ablauf in Ihrer app Python benötigen.

* Client-ID (eindeutig für die Anwendung)
* Eine Antwort URL (Http://127.0.0.1:8000/verbinden/Get_token /)
* Eine Anwendungsschlüssel (eindeutig für Ihre Anwendung)

<!--<a name="redirect"></a>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>Umleiten des im Browser zu der Anmeldeseite

Ihre app muss im Browser auf der Anmeldeseite den OAuth-Ablauf beginnen und Abrufen eines Autorisierungscodes umleiten. 

Im Beispiel Connect erstellt der folgende Code (befindet sich in [*connect/auth_helper.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/auth_helper.py)) die URL, die die app muss der Benutzer weitergeleitet und geleitet auf die Ansicht, in dem sie für die Umleitung verwendet werden. 

```python
# This function creates the signin URL that the app will
# direct the user to in order to sign in to Office 365 and
# give the app consent.
def get_signin_url(redirect_uri):
  # Build the query parameters for the signin URL.
  params = { 'client_id': client_id,
             'redirect_uri': redirect_uri,
             'response_type': 'code'
           }

  authorize_url = '{0}{1}'.format(authority, '/common/oauth2/authorize?{0}')
  signin_url = authorize_url.format(urlencode(params))
  return signin_url
```

<!--<a name="authCode"></a>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>Empfangen eines Autorisierungscodes in der Antwort-URL-Seite

Nachdem der Benutzer anmeldet, wird der Browser umgeleitet an Ihre Antwort-URL der ```get_token``` -Funktion im [*connect/views.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/views.py)mit einer Autorisierungscode an der als Abfragezeichenfolge angehängt der ```code``` Variable. 

Beispiel für Connect Ruft den Code aus der Abfragezeichenfolge ab, sodass es dann für ein Zugriffstoken austauschen kann.

```python
auth_code = request.GET['code']
```

<!--<a name="accessToken"></a>-->
## <a name="request-an-access-token-from-the-token-issuing-endpoint"></a>Fordern Sie ein Zugriffstoken aus dem Endpunkt Ausstellen von token

Nachdem Sie den Autorisierungscode haben, können Sie sie an die Client-ID wichtige und Beantworten von URL-Werten, die Sie von Azure Active Directory eine Access anfordern token erhalten haben. 

> **Hinweis** Die Anforderung muss auch eine Ressource angeben, die Sie nutzen möchten. Im Fall von Microsoft Graph, ist der Wert der `https://graph.microsoft.com`.

Beispiel für Connect fordert ein Token in der ```get_token_from_code``` Funktion in der [*connect/auth_helper.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/auth_helper.py) -Datei.

```python
# This function passes the authorization code to the token
# issuing endpoint, gets the token, and then returns it.
def get_token_from_code(auth_code, redirect_uri):
  # Build the post form for the token request
  post_data = { 'grant_type': 'authorization_code',
                'code': auth_code,
                'redirect_uri': redirect_uri,
                'client_id': client_id,
                'client_secret': client_secret,
                'resource': 'https://graph.microsoft.com'
              }
              
  r = requests.post(token_url, data = post_data)
  
  try:
    return r.json()
  except:
    return 'Error retrieving token: {0} - {1}'.format(r.status_code, r.text)
```

> **Hinweis** Die Antwort enthält mehr Informationen als nur das Zugriffstoken an. Angenommen, erhalten Ihre app eine Aktualisierung zur neuen Zugriffstoken anfordern, ohne dass des Benutzers explizit erneut anmelden token.

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>Verwenden Sie das Zugriffstoken in einer Anforderung an die Microsoft Graph-API

Mit einem Zugriffstoken kann Ihre app authentifizierte Anforderungen für die Microsoft Graph-API veröffentlichen. Ihre app muss das Zugriffstoken an den **Authorization** -Header jeder Anforderung anfügen.

Beispiel für Connect sendet eine e-Mail mit den ```me/microsoft.graph.sendMail``` Endpunkt in der Microsoft Graph-API. Der Code befindet sich in der ```call_sendMail_endpoint``` Funktion in der [*connect/graph_service.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/graph_service.py) -Datei. Dies ist der Code, der zeigt, wie die Zugriffscode an der Authorization-Header angefügt.

```python
# Set request headers.
headers = { 
  'User-Agent' : 'python_tutorial/1.0',
  'Authorization' : 'Bearer {0}'.format(access_token),
  'Accept' : 'application/json',
  'Content-Type' : 'application/json'
}
```

> **Hinweis** Senden der Anforderung muss auch einen **Content-Type** -Header mit einem Wert von Graph API akzeptiert `application/json`.

Die Microsoft Graph-API ist eine sehr leistungsstarke Unifiying API, die Interaktion mit allen Arten von Microsoft-Daten verwendet werden können. Checken Sie die API-Referenz zu untersuchen, was Sie mit der Microsoft Graph-API ausführen können.

<!--
## Additional resources

-  [Office 365 Python Connect sample using Microsoft Graph](https://github.com/OfficeDev/O365-Python-Microsoft-Graph-Connect)
-  [Office Dev Center](http://dev.office.com) 
-  [Microsoft Graph API reference]()-->
