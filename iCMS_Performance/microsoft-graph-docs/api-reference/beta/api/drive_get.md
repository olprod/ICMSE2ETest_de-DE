# <a name="get-drive"></a>Abrufen von Laufwerk

Rufen Sie die Eigenschaften und Beziehungen des Drive-Objekts ab. Ein Laufwerk darstellt des Benutzers OneDrive oder OneDrive for Business oder eine SharePoint-Dokumentbibliothek ein Office 365-Gruppe zugeordnet.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive
GET /drives/<id>
GET /users/<id | userPrincipalName>/drive
GET /groups/<id>/drive
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung                 |
|:--------------|:-------|:----------------------------|
| Autorisierung | string | Bearer \<token\>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Code und [Laufwerk](../resources/drive.md) Antwortobjekt im Antworttext.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung

Hier ist ein Beispiel für die Anforderung an die Anmeldung des Benutzers OneDrive oder OneDrive für Unternehmen zu erhalten.

<!-- {
  "blockType": "request",
  "name": "get_drive"
}-->
```http
GET https://graph.microsoft.com/beta/me/drive
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.drive"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
    "driveType": "business",    
    "owner": {
        "user": {
            "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
            "displayName": "Ryan Gregg"
        }
    },
    "quota": {
        "deleted": 256938,
        "remaining": 1099447353539,
        "state": "normal",
        "total": 1099511627776
    }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get metadata for a OneDrive, OneDrive for Business, or Office 365 group drive",
  "keywords": "drive,onedrive,default drive,group drive",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Get Drive"
}-->
