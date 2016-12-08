# <a name="update-policy"></a>Update-Richtlinie

Aktualisieren von Eigenschaften in einer vorhandenen [Richtlinie](../resources/policy.md).

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung

```http
PATCH /policies/<id>
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |
| Inhaltstyp | Application/json  | Die Art der Daten im Textkörper einer Entität. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den Parametern, die aktualisiert werden müssen. Die folgende Tabelle zeigt die möglichen Parameter.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Definition|String|Die stringified Version des [Richtlinienobjekts](../resources/policy.md) .|
|displayName|String|Ein benutzerdefinierter Name für die Richtlinie ein.|
|isOrganizationDefault|Boolean|Gibt an, ob diese Richtlinie standardmäßig angewendet wird.|
|Typ|String|Gibt den Typ der Richtlinie an. Derzeit muss "TokenLifetimePolicy" sein.|

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Wenn Sie nicht erfolgreich ist, ein `4xx` mit bestimmten Details entsprechende Fehlermeldung zurückgegeben.

### <a name="example"></a>Beispiel
Im folgende Beispiel wird die Definition der Richtlinie Gültigkeitsdauer von token aktualisiert und platziert es als Standard Organisation.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
PATCH https://graph.microsoft.com/beta/policies/<id>
Content-Type: application/json
{
    "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\",\"MaxInactiveTime\":\"20:00:00\",}}"],
    "isOrganizationDefault":true
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 204 No Content
```
