# <a name="delete-policy"></a>Löschrichtlinie

Löschen einer [Richtlinie](../resources/policy.md).

### <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP-Anforderung

```http
DELETE /policies/<id>
```
### <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

### <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

### <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Wenn Sie nicht erfolgreich...

### <a name="example"></a>Beispiel
Im folgende Beispiel wird eine Richtlinie gelöscht.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

```http
DELETE https://graph.microsoft.com/beta/policies/<id>
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.

```http
HTTP/1.1 204 No Content
```
