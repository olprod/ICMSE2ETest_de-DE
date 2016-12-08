# <a name="create-inferenceclassificationoverride"></a>Erstellen von inferenceClassificationOverride

Erstellen einer Außerkraftsetzung für eine SMTP-Adresse identifizierten Absender. Nachrichten von diesem SMTP-Adresse konsistent eingestuft wird wie in die Außerkraftsetzung angegeben.

**Hinweis**

- Wenn bereits eine Überschreibung mit der gleichen SMTP-Adresse vorhanden ist, werden die Felder **ClassifyAs** und **Name** der die Außerkraftsetzung mit den angegebenen Werten aktualisiert.
- Die maximale Anzahl von Außerkraftsetzungen unterstützt für ein Postfach ist 1000, basierend auf eindeutigen SMTP-Absenderadressen.
- POST-Operation unterstützt nur eine Außerkraftsetzung zu einem Zeitpunkt erstellen.

## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/inferenceClassification/overrides
POST /users/<id>/inferenceClassification/overrides
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [InferenceClassificationOverride](../resources/inferenceclassificationoverride.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortcode und eines [InferenceClassificationOverride](../resources/inferenceclassificationoverride.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_inferenceclassificationoverride_from_inferenceclassification"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/inferenceClassification/overrides
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Fanny Downs",
    "address": "fannyd@adatum.onmicrosoft.com"
  }
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.inferenceClassificationOverride"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Fanny Downs",
    "address": "fannyd@adatum.onmicrosoft.com"
  },
  "id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create inferenceClassificationOverride",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->