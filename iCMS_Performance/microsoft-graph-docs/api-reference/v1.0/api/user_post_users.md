# <a name="create-user"></a>Benutzer erstellen

Verwenden Sie diese API, um einen neuen Benutzer zu erstellen.
Textkörper der Anforderung enthält den Benutzer zum Erstellen. Zumindest müssen Sie die erforderlichen Eigenschaften für den Benutzer angeben. Optional können Sie eine beliebige andere schreibbaren Eigenschaften angeben.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Directory.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /users
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/json  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Benutzerobjekts](../resources/user.md) .

In der folgenden Tabelle werden die Eigenschaften gezeigt, die erforderlich sind, wenn Sie einen Benutzer erstellen.

| Parameter | Typ | Beschreibung|
|:---------------|:--------|:----------|
|accountEnabled |boolean |True, wenn das Konto aktiviert ist; andernfalls, False.|
|displayName |string |Der Name im Adressbuch für den Benutzer angezeigt.|
|onPremisesImmutableId |string |Muss nur angegeben werden, wenn ein neues Benutzerkonto zu erstellen, wenn Sie eine verbunddomäne für die Benutzereigenschaft UserPrincipalName (UPN) nutzen.|
|mailNickname |string |Der e-Mail-Alias des Benutzers.|
|passwordProfile|[PasswordProfile](../resources/passwordprofile.md) |Das Profil, das Kennwort für den Benutzer.|
|userPrincipalName |string |Der Benutzerprinzipalname (someuser@contoso.com).|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Benutzer](../resources/user.md) in der Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_user_from_users"
}-->
```http
POST https://graph.microsoft.com/v1.0/users
Content-type: application/json
Content-length: 551

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "bea13e0c-3828-4daa-a392-28af7ff61a0f"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Benutzerobjekts](../resources/user.md) .
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.user"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 551

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "bea13e0c-3828-4daa-a392-28af7ff61a0f"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create User",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
