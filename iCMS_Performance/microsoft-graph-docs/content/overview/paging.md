
# <a name="paging-microsoft-graph-data-in-your-app"></a>Microsoft Graph Paging von Daten in Ihrer app 
 
Wenn die API-Anfragen zu viele Informationen auf einer Seite anzeigen zurückkehren, können Paging Sie die Informationen in verwaltbare Gruppen aufteilen. 

Sie können in der Microsoft Graph vorwärts- und Rückwärtssuche blättern. Eine Antwort, die Ergebnisanzeige enthält wird ein Token überspringen ( **odata.nextLink** ) enthalten, die zum Abrufen der nächsten Seite der Ergebnisse ausgeführt werden können. Dieses Token überspringen mit kombiniert werden kann eine **Vorherige Seite = True** Argument für die Abwärtskompatibilität Seite abzufragen.

Beispiel für eine Anforderung die Follow veranschaulicht paging weiterleiten:

```
https://graph.microsoft.com/v1.0/users?$top=5$skiptoken=X'4453707402.....0000'
```
Der Parameter **$skiptoken** aus der vorherigen Antwort enthalten ist, und zum Abrufen der nächsten Seite der Ergebnisse ermöglicht.

Die folgende Beispiel für eine Anforderung wird das rückwärts paging veranschaulicht:

```
https://graph.microsoft.com/v1.0/users?$top=5$skiptoken=X'4453707.....00000'&previous-page=true
```
Der Parameter **$skiptoken** aus der vorherigen Antwort ist enthalten. Wenn diese mit kombiniert die **& Vorherige Seite = True** Parameter, der vorherigen Seite der Suchergebnisse abgerufen werden soll.

Die folgenden Schritte zeigen den Fluss Anforderung und Antwort zum Vorwärts- und Rückwärtssuche Seite:

1. Angefordert wird eine Liste der ersten 10 Benutzer nicht genügend 15 abrufen. Die Antwort enthält ein Token überspringen, um der letzten Seite des 10 Benutzer darauf hinzuweisen.
2. Wenn Sie die letzten 5 Benutzer erhalten möchten, einen anderen angefordert wird, enthält das Überspringen Token aus der vorherigen Antwort zurückgegeben.
3. Um rückwärts Sie auf der Seite angefordert wird mit dem in Schritt 1 und der Parameter zurückgegebenen überspringen Token **& Vorherige Seite = True** die Anforderung hinzugefügt wird.
4. Die Antwort enthält frühere (Startseite) von 10 Benutzern. In einem anderen Szenario, in dem weitere Seiten hinterlassen wurden, wird ein neues überspringen Token zurückgegeben. Die Anforderung zusammen mit diesem neuen überspringen Token hinzugefügt werden **& Vorherige Seite = True** erneut rückwärts blättern.

Die folgenden Einschränkungen gelten für ausgelagerten Anforderungen:

- Die Seite Standardgröße ist 100. Die maximale Seitengröße ist 999.
- Abfragen für Rollen unterstützt Paging nicht. Dazu gehören Rolle Objekte lesen, sich selbst als auch für Rolle Mitglieder.
- Paging wird für die Link-Suche nicht wie unterstützt, für das Abfragen von Gruppenmitgliedern verwendet wird.
