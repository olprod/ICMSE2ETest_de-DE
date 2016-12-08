# <a name="assign-policy"></a>Zuweisen der Richtlinie

Eine Anwendung oder ein Dienstprinzipal eine [Richtlinie](../resources/policy.md) zugewiesen.

>Hinweis: Derzeit gilt richtlinienzuweisung nur für Token Lebensdauer Richtlinie. Dieser Typ der Richtlinie wird in der [Richtlinie](../resources/policy.md)beschrieben.

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung

```http
POST /applications/<id>/policies/$ref
POST /serviceprincipals/<id>/policies/$ref
```

> Hinweis: "Id" in der Anforderung ist die Eigenschaft "Id" der Anwendung oder Dienstprinzipal, nicht die Eigenschaft "Appid".

### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | Application/json  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des Richtlinienobjekts hinzugefügt werden soll.

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Wenn nicht erfolgreich ist, ein `4xx` mit spezifische Details entsprechende Fehlermeldung zurückgegeben.

### <a name="example"></a>Beispiel
Das folgende Beispiel weist eine Richtlinie zu einer Anwendung.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
POST /applications/<id>/policies/$ref
Content-type: application/json
{
    "@odata.id":"https://graph.microsoft.com/beta/policies/<policyid>"
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 204 No Content
```
