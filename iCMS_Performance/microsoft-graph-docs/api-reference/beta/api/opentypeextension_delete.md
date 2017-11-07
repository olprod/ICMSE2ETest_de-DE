# <a name="delete-data-extension"></a>Löschen von Daten-Erweiterung

Löschen einer Daten-Erweiterungs ([OpenTypeExtension](../resources/openTypeExtension.md) -Objekt) aus der angegebenen Instanz von einer Ressource. 

Die Ressource kann es sich um eine Nachricht, Kalenderereignis oder Kontakt der des angemeldeten Benutzers auf Office 365 oder Outlook.com sein. Alternativ kann ein Ereignis oder eine Post für eine Office 365-Gruppe sein.

## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist erforderlich, um diese API, abhängig von der Ressource ausführen, den Sie die Erweiterung von löschen:

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_

 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /me/messages/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/messages/<id>/extensions/<extensionId>
DELETE /me/mailFolders/<id>/messages/<id>/extensions/<extensionId>

DELETE /me/events/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/events/<id>/extensions/<extensionId>

DELETE /me/contacts/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/contacts/<id>/extensions/<extensionId>

DELETE /groups/<id>/events/<id>/extensions/<extensionId>

DELETE /groups/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
DELETE /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
```

## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Ein eindeutiger Bezeichner für eine Instanz in der entsprechenden Auflistung. Erforderlich.|
|extensionID geändert|string|Dies kann eine Erweiterung der ist eine eindeutige ID der Erweiterung oder einen voll gekennzeichneten Namen, der den Erweiterungstyp und eindeutige Text-ID verkettet sein. Der vollständig qualifizierte Name wird zurückgegeben, der `id` Eigenschaft, wenn Sie die Erweiterung zu erstellen. Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Im ersten Beispiel verweist auf eine Erweiterung mit seinem Namen und löscht die Erweiterung in der angegebenen Nachricht.
<!-- {
  "blockType": "request",
  "name": "delete_opentypeextension"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

Im zweite Beispiel löscht eine Erweiterung in der angegebenen Gruppe Ereignis.

<!-- { "blockType": "ignored" } -->
```http
DELETE https://graph.microsoft.com/beta/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVlN17IsAAA=')/extensions('Com.Contoso.Referral')
```

 

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": false
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete opentypeextension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->