# <a name="send-a-sharing-invitation"></a>Senden Sie eine Einladung zur Freigabe

Sendet eine Einladung zur Freigabe an ein vorhandenes Element. Eine freigabeeinladung erstellt eine eindeutige sharing Verknüpfung und sendet eine e-Mail an den Empfänger der Einladung, die den Freigabe Link enthält.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /drive/root/invite
POST /drive/items/<id>/invite
POST /drives/<id>/root/invite

```

## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung ein JSON-Objekt mit den folgenden Parametern aus.

| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Empfänger|Empfänger|Eine Liste der e-Mail-Adressen für die Einladung zur Freigabe.|
|Nachricht|String|Eine nur-Text-formatierten Nachricht, die in der Einladung zur Freigabe enthalten ist. Höchstens 2000 Zeichen.|
|requireSignIn|Boolean|Gibt an, in dem der Empfänger der Einladung zur Anmeldung an das freigegebene Element anzeigen erforderlich ist.|
|sendInvitation|Boolean|Gibt an, ob eine e-Mail oder Post generierten (False) oder wenn die Berechtigung nur (true) erstellt wird.|
|Rollen|String|Geben Sie die Rollen, die an die Empfänger, der die Einladung zur Freigabe erteilt werden.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200 OK` Antwort [Berechtigung](../resources/permission.md) und Code-Auflistungsobjekt in der Antworttext.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "item_invite"
}-->
```http
POST https://graph.microsoft.com/v1.0/drive/root/invite
Content-type: application/json
Content-length: 313

{
  "recipients": [
    {
      "email": "email-value",
      "alias": "alias-value",
      "objectId": "objectId-value",
      "permissionIdentityType": "permissionIdentityType-value"
    }
  ],
  "message": "message-value",
  "requireSignIn": true,
  "sendInvitation": true,
  "roles": [
    "roles-value"
  ]
}
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 939

{
  "value": [
    {
      "grantedTo": {
        "application": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "device": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "user": {
          "displayName": "displayName-value",
          "id": "id-value"
        }
      },
      "id": "id-value",
      "invitation": {
        "email": "email-value",
        "redeemedBy": "redeemedBy-value",
        "signInRequired": true
      },
      "inheritedFrom": {
        "driveId": "driveId-value",
        "id": "id-value",
        "path": "path-value"
      },
      "link": {
        "application": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "type": "type-value",
        "webUrl": "webUrl-value"
      },
      "roles": [
        "roles-value"
      ]
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->

<!-- {
  "type": "#page.annotation",
  "description": "item: invite",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
