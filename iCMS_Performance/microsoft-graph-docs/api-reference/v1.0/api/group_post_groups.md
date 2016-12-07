# <a name="create-group"></a>Zum Erstellen einer Gruppe:

Use this API to create a new group as specified in the request body. You can create one of 3 types of groups:
* Office 365 group (aka unified group)
* Dynamic group
* Sicherheitsgruppe

At a minimum, you must specify the properties required for the type of group you're creating. This includes:

| Type of group | **groupTypes** property | **securityEnabled** property |
|:--------------|:------------------------|:-----------------------------|
| Office 365 | "Unified" | falsch |
| Dynamik | "DynamicMembership" | falsch |
| Sicherheit | Do not set. | wahr |

Specify other writable properties as necessary, such as **mailEnabled** for mail-enabled groups. For more information, see the properties of the [group](../resources/group.md) resource.
## <a name="prerequisites"></a>Voraussetzungen
The following **scope** is required to execute this API: _Group.ReadWrite.All_ 
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Required. |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply a JSON representation of [group](../resources/group.md) object.

The following table shows the properties that are required when you create a group.

| Parameter | Typ | Beschreibung|
|:---------------|:--------|:----------|
| DisplayName | string | The name to display in the address book for the group. |
| mailEnabled | boolean | Set to **true** for mail-enabled groups. |
| mailNickname | string | The mail alias for the group. |
| securityEnabled | boolean | Set to **true** for security-enabled groups. Set to **false** if creating an Office 365 group. |

## <a name="response"></a>Antwort
If successful, this method returns `201, Created` response code and [group](../resources/group.md) object in the response body.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "create_group_from_groups"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```
In the request body, supply a JSON representation of [group](../resources/group.md) object.
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
