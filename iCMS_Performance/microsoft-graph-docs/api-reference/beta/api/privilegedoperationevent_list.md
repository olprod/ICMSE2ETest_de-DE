# <a name="list-privilegedoperationevents"></a>Liste privilegedOperationEvents

Abrufen einer Liste der [PrivilegedOperationEvent](../resources/privilegedoperationevent.md) -Objekten, die die Überwachungsereignisse darstellen, die für die Rolle Vorgänge von privilegierten Identity Management generiert werden. Die Details zu den Überwachungsereignis finden Sie [PrivilegedOperationEvent](../resources/privilegedoperationevent.md). Verwenden, um die Abfrageergebnisse zu filtern, die standard-OData ``$filter`` Ausdruck.


## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: _Directory.AccessAsUser.All_

Der Requestor muss eine der folgenden Rollen verfügen: _Berechtigten Rolle Administrators_, _Globaler Administrator_, _Sicherheitsadministrator_oder _Sicherheit Leser_.

 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /privilegedOperationEvents
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn erfolgreich, diese Methode gibt eine `200 OK` Antwortcode und Auflistung von [PrivilegedOperationEvent](../resources/privilegedoperationevent.md) -Objekte in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1
Es folgt ein Beispiel der Anforderung.
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/privilegedOperationEvents
```
##### <a name="response-1"></a>Antwort 1
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedOperationEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 227

{
  "value": [
    {
      "id": "id-value",
      "userId": "userId-value",
      "userName": "userName-value",
      "userMail": "userMail-value",
      "roleId": "roleId-value",
      "roleName": "roleName-value"
    }
  ]
}
```

##### <a name="request-2"></a>Anfordern von 2
Es folgt ein Beispiel für die Anforderung mithilfe von $filter abzurufenden haben die Überwachungsereignisse ``requestType`` als ``Elevate``.
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/privilegedOperationEvents?$filter=requestType eq 'Elevate'
```
##### <a name="response-2"></a>Antwort 2
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedOperationEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 547

{
    "value": [
        {
            "id": "201605110001636551",
            "userId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "userName": "admin",
            "userMail": "admin@contoso.onmicrosoft.com",
            "roleId": "558dba2d-e536-4349-a983-dd73ec2be1f7",
            "roleName": "Security Administrator",
            "expirationDateTime": "2016-05-11T19:31:14.1157385Z",
            "creationDateTime": "2016-05-11T18:31:14.5013728Z",
            "requestorId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "requestorName": "admin",
            "tenantId": "ffffae8b-cc96-4325-9bd1-dc82594b0b40",
            "requestType": "Elevate",
            "additionalInformation": "elevate me"
        },
        {
            "id": "201605190001743860",
            "userId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "userName": "admin",
            "userMail": "admin@contoso.onmicrosoft.com",
            "roleId": "558dba2d-e536-4349-a983-dd73ec2be1f7",
            "roleName": "Security Administrator",
            "expirationDateTime": "2016-05-19T17:52:58.6019279Z",
            "creationDateTime": "2016-05-19T16:52:58.9475243Z",
            "requestorId": "ffff3614-c255-4cf5-92fa-74e770c656d8",
            "requestorName": "admin",
            "tenantId": "ffffae8b-cc96-4325-9bd1-dc82594b0b40",
            "requestType": "Elevate",
            "additionalInformation": "elevate me"
        }
    ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List privilegedOperationEvents",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->