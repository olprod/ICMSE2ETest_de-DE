# <a name="update-data-extension"></a>Aktualisieren von Daten-Erweiterung

Aktualisieren einer Daten-Erweiterungs ([OpenTypeExtension](../resources/openTypeExtension.md) -Objekt) mit den Eigenschaften im Textkörper Anforderung:

- Wenn eine Eigenschaft im Textkörper Anforderung auf den Namen einer vorhandenen Eigenschaft in der Erweiterung übereinstimmt, werden die Daten in die Erweiterung aktualisiert.
- Andernfalls werden diese Eigenschaft und die Daten an die Erweiterung hinzugefügt. 

Die Erweiterung kann in Meldung, Ereignis oder Kontakt im Postfach des angemeldeten Benutzers bei Office 365 oder Outlook.com sein. Alternativ kann ein Ereignis oder eine Post für eine Office 365-Gruppe sein. Daten in einer Erweiterung möglich Grundtypen oder Arrays von Grundtypen.


## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist diese API, abhängig von der Ressource auszuführenden Ihnen die Erweiterung im erstellten erforderlich:

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->

```http
PATCH /me/messages/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/messages/<id>/extensions/<extensionId>
PATCH /me/mailFolders/<id>/messages/<id>/extensions/<extensionId>

PATCH /me/events/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/events/<id>/extensions/<extensionId>

PATCH /me/contacts/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/contacts/<id>/extensions/<extensionId>

PATCH /groups/<id>/events/<id>/extensions/<extensionId>

PATCH /groups/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
PATCH /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
```


## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Ein eindeutiger Bezeichner für eine Instanz der entsprechenden Auflistung. Erforderlich.|
|extensionID geändert|string|Dies kann eine Erweiterung der ist eine eindeutige ID einer Erweiterung oder einen voll gekennzeichneten Namen, der den Erweiterungstyp und eindeutige Text-ID verkettet sein. Der vollständig qualifizierte Name wird zurückgegeben, der `id` Eigenschaft, wenn Sie die Erweiterung zu erstellen. Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|
| Inhaltstyp | Application/json |

## <a name="request-body"></a>Anforderungstext

Bieten Sie ein JSON-Body eines Objekts [OpenTypeExtension](../resources/openTypeExtension.md) die folgenden erforderlichen Name / Wert-Paare und benutzerdefinierten Daten ändern oder hinzufügen zu dieser Erweiterung. Die Daten in der JSON-Nutzlast möglich Grundtypen oder Arrays von Grundtypen.

| Name       | Wert |
|:---------------|:----------|
| @odata.type | Microsoft.Graph.OpenTypeExtension |
| .-Kennung Erweiterungsname | Unique_string % |


## <a name="response"></a>Antwort

Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und das aktualisierte [OpenTypeExtension](../resources/openTypeExtension.md) -Objekt.


## <a name="example"></a>Beispiel
#### <a name="request-1"></a>Anforderung 1

Im ersten Beispiel wird veranschaulicht, wie eine Erweiterung in einer Nachricht zu aktualisieren. Die Erweiterung wird zunächst die folgenden JSON-Nutzlast dargestellt:

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00Z"
}
```

Sie können anhand des Namens die Erweiterung verweisen:

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

Oder Sie können unter den vollqualifizierten Namen die Erweiterung verweisen:

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

Beispiel für eine Anforderung und die folgenden Anforderungstext können Sie um die Erweiterung von zu aktualisieren:
- Ändern der `companyName` aus `Wingtip Toys` an`Wingtip Toys (USA)`
- Ändern der `dealValue` aus `500050` ,`500100`
- Hinzufügen neuer Daten als benutzerdefinierte Eigenschaft`updated`

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.type": "Microsoft.Graph.OpenTypeExtension",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": "500100",
    "expirationDate": "2015-12-03T10:00:00.000Z",
    "updated": "2015-10-29T11:00:00.000Z"
} 
```


#### <a name="response-1"></a>Antwort 1

Nachfolgend finden Sie die Antwort, die unabhängig von der Methode verwendet, um die Erweiterung verweisen identisch ist.

<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": 500100,
    "expirationDate": "2015-12-03T10:00:00Z",
    "updated": "2015-10-29T11:00:00.000Z"
}
```

****

#### <a name="request-2"></a>Anfordern von 2

Im zweite Beispiel veranschaulicht eine Erweiterung in einer Gruppe Post aktualisieren. Die Erweiterung wird zunächst durch die folgenden JSON-Nutzlast dargestellt, mit einer `expirationDate` Wert der `2015-07-03T13:04:00Z`:

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2015-07-03T13:04:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```

Im folgenden finden Sie die Anforderung und Anforderungstext so ändern Sie die `expirationDate` auf `2016-07-30T11:00:00Z`:

<!-- {
  "blockType": "request",
  "name": "update_opentypeextension"
}-->
```http
PATCH https://graph.microsoft.com/beta/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate')
Content-type: application/json

{
   "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
   "extensionName": "Com.Contoso.Estimate",
   "companyName": "Contoso",
   "expirationDate": "2016-07-30T11:00:00.000Z",
   "DealValue": 1010100,
   "topPicks": [
       "Employees only",
       "Add spouse or guest",
       "Add family"
    ]
}
```

#### <a name="response-2"></a>Antwort 2

Nachfolgend finden Sie die Antwort des im zweiten Beispiel wird die aktualisierten zeigt `expirationDate` -Erweiterung.

<!-- {  
  "blockType": "response",  
  "truncated": true,  
  "@odata.type": "microsoft.graph.opentypeextension"  
} --> 
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2016-07-30T11:00:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```

<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update opentypeextension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
} -->
