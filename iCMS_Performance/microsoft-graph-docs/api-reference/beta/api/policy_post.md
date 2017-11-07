# <a name="create-policy"></a>Richtlinie erstellen

Erstellen [Sie ein neues Gruppenrichtlinienobjekt](../resources/policy.md) nach Angabe Anzeigename, Richtlinientyp und Beschreibung der Richtlinie.

>Hinweis: Die Richtliniendetails werden vor dem gespeichert werden überprüft. Wenn sie die Überprüfung nicht bestanden hat, wird ein 400 Ungültige Anforderung zurückgegeben werden soll.

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*
### <a name="http-request"></a>HTTP-Anforderung

```http
POST /policies
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | Application/json  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Richtlinienobjekts](../resources/policy.md) .

In der folgenden Tabelle werden die Eigenschaften gezeigt, die erforderlich sind, wenn Sie eine Richtlinie erstellen.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Definition|String|Die Zeichenfolgenversion des [Richtlinienobjekts](../resources/policy.md) .|
|displayName|String|Ein benutzerdefinierter Name für die Richtlinie ein.|
|Typ|String|Gibt den Typ der Richtlinie an. Derzeit muss "TokenLifetimePolicy" sein.|

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Richtlinie](../resources/policy.md) im Antworttext. Wenn Sie nicht erfolgreich ist, ein `4xx` mit bestimmten Details entsprechende Fehlermeldung zurückgegeben.  

### <a name="example"></a>Beispiel
Das folgende Beispiel erstellt eine neue token Lebensdauer Richtlinie. Beachten Sie, dass der Definition Zeichenfolgenparameter doppelte Anführungszeichen mit Escapezeichen versehen hat.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
POST https://graph.microsoft.com/beta/policies
Content-Type: application/json

{
  "displayName":"CustomTokenLifetimePolicy",
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"],
  "type":"TokenLifetimePolicy"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#policies/$entity",
  "id":"id-value",
  "alternativeIdentifier":null,
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"],
  "displayName":"name-value",
  "isOrganizationDefault":false,
  "keyCredentials",
  "type":"TokenLifetimePolicy"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: createReply",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
