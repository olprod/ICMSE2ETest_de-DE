# <a name="update-inferenceclassificationoverride"></a>Inferenceclassificationoverride aktualisieren

Ändern Sie das **ClassifyAs** -Feld einer Außerkraftsetzung wie angegeben. 

Sie können nicht PATCH verwenden, um alle anderen Felder in einer [InferenceClassificationOverride](../resources/inferenceClassificationOverride.md) -Instanz zu ändern. 

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen Anzeigename geändert, können Sie die [POST](inferenceclassification_post_overrides.md) So erzwingen Sie ein Update in das Namensfeld in der vorhandenen Überschreibung verwenden.

Wenn eine Außerkraftsetzung für ein Absender vorhanden ist und der Absender seinen SMTP-Adresse, und [Löschen von](inferenceclassificationoverride_delete.md) vorhandenen außer Kraft setzen und [Erstellen von ändert](inferenceclassification_post_overrides.md) ist eine neue mit der neuen SMTP-Adresse die einzige Möglichkeit, der die Außerkraftsetzung für diesen Absender "Aktualisieren".

## <a name="prerequisites"></a>Voraussetzungen
Der folgende **Bereiche** sind erforderlich, um diese API ausführen: *Mail.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/inferenceClassification/overrides/<id>
PATCH /users/<id>/inferenceClassification/overrides/<id>
```

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | string  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie den neuen Wert für **ClassifyAs**im Textkörper Anforderung. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert werden.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|classifyAs|string| Gibt an, wie eingehende-Nachrichten von einer bestimmten Absender sollte stets als klassifiziert werden. Mögliche Werte sind: `focused`, `other`.|


## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [InferenceClassificationOverride](../resources/inferenceclassificationoverride.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Das folgende Beispiel ändert die Überschreibung für die SMTP-Adresse randiw@adatum.onmicrosoft.com aus `other` auf `focused`.

<!-- {
  "blockType": "request",
  "name": "update_inferenceclassificationoverride"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/inferenceClassification/overrides/<id>
Content-type: application/json

{
  "classifyAs": "focused"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.inferenceClassificationOverride"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Randi Welch",
    "address": "randiw@adatum.onmicrosoft.com"
  },
  "id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update inferenceclassificationoverride",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->