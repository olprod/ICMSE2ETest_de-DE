# <a name="update-contact"></a>Update contact

Update the properties of contact object.
## <a name="prerequisites"></a>Voraussetzungen
One of the following **scopes** is required to execute this API: *Contacts.ReadWrite*
## <a name="http-request"></a>Verwenden Sie diese HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
A [contact](../resources/contact.md) from user's default [contactFolder](../resources/contactfolder.md).
```http
PATCH /me/contacts/<id>
PATCH /users/<id | userPrincipalName>/contacts/<id>
```
A [contact](../resources/contact.md) from a user's top level [contactFolder](../resources/contactfolder.md).
```http
PATCH /me/contactFolders/<id>/contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
A [contact](../resources/contact.md) contained in a child folder of a [contactFolder](../resources/mailfolder.md).  The example below shows one level of nesting, but a contact can be located in a child of a child and so on.
```http
PATCH /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Required.  |
| contentType  | application/json. Required.  |

## <a name="request-body"></a>Anforderungstextkörper
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|AssistantName|String|The name of the contact's assistant.|
|Birthday|DateTimeOffset|The contact's birthday.|
|Kategorien|String|The categories associated with the contact.|
|Kinder|String||
|CompanyName|String|The name of the contact's company.|
|Department|String|The contact's department.|
|DisplayName|String|Der Anzeigename des Benutzers.|
|Eigenschaft emailAddresses|[EmailAddress](../resources/emailaddress.md) collection|The contact's email addresses.|
|FileAs|String|The name the contact is filed under.|
|Gender |String |The contact's gender. |
|generation|String|The contact's generation.|
|givenName|String|The contact's given name.|
|imAddresses|String|The contact's instant messaging (IM) addresses.|
|Initials|String|The contact's initials.|
|JobTitle|String|The contact’s job title.|
|Vorgesetzter|String|The name of the contact's manager.
|MiddleName|String|The contact's middle name.|
|NickName|String|The contact's nickname.|
|OfficeLocation|String|The location of the contact's office.|
|parentFolderId|String|The ID of the contact's parent folder.|
|personalNotes|String|The user's notes about the contact.|
|phones |[phone](../resources/phone.md) collection |Phone numbers associated with the contact, for example, home phone, mobile phone, and business phone. |
|postalAddresses |[physicalAddress](../resources/physicalAddress.md) collection |Addresses associated with the contact, for example, home address and business address. |
|Profession|String|The contact's profession.|
|spouseName|String|The name of the contact's spouse.|
|surname|String|The contact's surname.|
|title|String|The contact's title.|
|Websites |[website](../resources/website.md) collection|Web sites associated with the contact. |
|weddingAnniversary |Date |The contact's wedding anniversary. |
|YomiCompanyName|String|The phonetic Japanese company name of the contact. This property is optional.|
|yomiGivenName|String|The phonetic Japanese given name (first name) of the contact. This property is optional.|
|yomiSurname|String|The phonetic Japanese surname (last name)  of the contact. This property is optional.|

## <a name="response"></a>Antwort
If successful, this method returns a `200 OK` response code and updated [contact](../resources/contact.md) object in the response body.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für das Markup des Nummerierungsteils.
<!-- {
  "blockType": "request",
  "name": "update_contact"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/contacts/<id>
Content-type: application/json
Content-length: 1977

{
  "postalAddresses": [{
    "type": "business",
    "postOfficeBox": "P.O. Box 100",
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "countryOrRegion": "USA",
    "postalCode": "98121"
  }],
  "birthday": "1974-07-22"
}
```
##### <a name="response"></a>Antwort
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.contact"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 1977

{
  "id": "AAMkAGI2THk0AAA=",
  "createdDateTime": "2014-10-19T23:08:24Z",
  "lastModifiedDateTime": "2014-10-19T23:08:24Z",
  "changeKey": "EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4",
  "categories": [],
  "parentFolderId": "AAMkAGI2AAEOAAA=",
  "birthday": "1974-07-22",
  "fileAs": "Fort, Garth",
  "displayName": "Garth Fort",
  "givenName": "Garth",
  "initials": "G.F.",
  "middleName": null,
  "nickName": "Garth",
  "surname": "Fort",
  "title": null,
  "yomiGivenName": null,
  "yomiSurname": null,
  "yomiCompanyName": null,
  "generation": null,
  "emailAddresses": [
    {
      "name": "Garth",
      "address": "garth@a830edad9050849NDA1.onmicrosoft.com"
    }
  ],
  "imAddresses": [
    "sip:garthf@a830edad9050849nda1.onmicrosoft.com"
  ],
  "jobTitle": "Web Marketing Manager",
  "companyName": "Contoso, Inc.",
  "department": "Sales & Marketing",
  "officeLocation": "20/1101",
  "profession": null,
  "assistantName": null,
  "manager": null,
  "phones": [{
    "type": "business",
    "number": "+1 918 555 0101"
  }],
  "postalAddresses": [{
    "type": "business",
    "postOfficeBox": "P.O. Box 100",
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "countryOrRegion": "USA",
    "postalCode": "98121"
  }],
  "spouseName": null,
  "personalNotes": null,
  "children": [], 
  "gender": null,
  "websites": [{
      "type": "work",
      "address": "http://www.contoso.com",
      "name": "Contoso"
  }],
  "weddingAnniversary": null,
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->