# <a name="update-contact"></a>Kontakt aktualisieren

Aktualisieren Sie die Eigenschaften des ein Kontaktobjekt.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
[Wenden Sie sich](../resources/contact.md) von einem Benutzer standardmäßig [ContactFolder](../resources/contactfolder.md).
```http
PATCH /me/contacts/<id>
PATCH /users/<id | userPrincipalName>/contacts/<id>
```
[Wenden Sie sich an](../resources/contact.md) von eines Benutzers oberen Ebene [ContactFolder](../resources/contactfolder.md).
```http
PATCH /me/contactFolders/<id>/contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
[Wenden Sie sich](../resources/contact.md) in einem untergeordneten Ordner von einem [ContactFolder](../resources/mailfolder.md)enthalten. Das folgende Beispiel zeigt eine Ebene von schachteln, aber ein Kontakt kann befindet sich ein untergeordnetes Element des ein untergeordnetes Element und so weiter.
```http
PATCH /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert |
|:---------------|:--------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/Json. Erforderlich.  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assistantName|String|Der Name des Assistenten des Kontakts.|
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Kontakts.|
|businessAddress|[Physikalische Adresse](../resources/physicaladdress.md)|Business-Adresse des Kontakts.|
|businessHomePage|String|Die Business-Homepage des Kontakts.|
|businessPhones|String|Der Kontakt geschäftlichen Telefonnummer.|
|Kategorien|String|Die Kategorien, die dem Kontakt zugeordnet.|
|untergeordnete Elemente|String|Die Namen der untergeordneten Elemente des Kontakts.|
|Firma|String|Der Name der Firma des Kontakts.|
|Abteilung|String|Die Abteilung des Kontakts.|
|displayName|String|Anzeigename des Kontakts.|
|emailAddresses|[EmailAddress](../resources/emailaddress.md) -Auflistung|Der Kontakt-e-Mail-Adressen.|
|fileAs|String|Der Namen des Kontakts wird unter eingereicht werden.|
|Generierung|String|Generierung des Kontakts.|
|Vorname|String|Vorname des Kontakts.|
|homeAddress|[Physikalische Adresse](../resources/physicaladdress.md)|Die Adresse des Kontakts Startseite.|
|homePhones|String-Auflistung|Private Rufnummern eines Kontakts.|
|imAddresses|String|Der Kontakt instant messaging (IM) Adressen.|
|Initialen|String|Initialen des Kontakts.|
|jobTitle|String|Position des Kontakts.|
|Vorgesetzter|String|Der Name des Vorgesetzten des Kontakts.
|middleName|String|Vorname des Kontakts.|
|mobilePhone|String|Die Mobiltelefonnummer des Kontakts.|
|Spitzname|String|Spitzname des Kontakts.|
|officeLocation|String|Der Speicherort der Office des Kontakts.|
|otherAddress|[Physikalische Adresse](../resources/physicaladdress.md)|Andere Adressen für den Kontakt.|
|parentFolderId|String|Die ID des übergeordneten Ordners des Kontakts.|
|personalNotes|String|Der Benutzer Notizen zum Kontakt.|
|Beruf|String|Der Beruf des Kontakts.|
|spouseName|String|Der Name des Kontakts Partner/in.|
|Nachname|String|Den Nachnamen des Kontakts.|
|title|String|Titel des Kontakts.|
|yomiCompanyName|String|Der phonetische Japanisch Firmenname des Kontakts an. Diese Eigenschaft ist optional.|
|yomiGivenName|String|Dem phonetischen japanische angegebenen Namen (Vorname) des Kontakts. Diese Eigenschaft ist optional.|
|yomiSurname|String|Der phonetische Japanisch Nachname (Nachname) des Kontakts. Diese Eigenschaft ist optional.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und eine aktualisierte [wenden Sie sich an](../resources/contact.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_contact"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/contacts/<id>
Content-type: application/json
Content-length: 1977

{
  "homeAddress": {
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98121"
  },
  "birthday": "1974-07-22"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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
  "businessHomePage": "http://www.contoso.com",
  "assistantName": null,
  "manager": null,
  "homePhones": [],
  "mobilePhone": null,
  "businessPhones": [
    "+1 918 555 0101"
  ],
  "homeAddress": {
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "postalCode": "98121"
  },
  "businessAddress": {
      "street": "10 Contoso Way",
      "city": "Redmond",
      "state": "WA",
      "countryOrRegion": "USA",
      "postalCode": "98075"  
  },
  "otherAddress": {},
  "spouseName": null,
  "personalNotes": null,
  "children": []
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
