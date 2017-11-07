# <a name="contact-resource-type"></a>Wenden Sie sich an Ressourcentyp

Ein Kontakt ist ein Element in Outlook, in dem Sie organisieren und Speichern von Informationen zu Personen und Organisationen, mit denen Sie kommunizieren, können. Kontakte sind im Kontakteordner enthalten.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von Kontakt](../api/contact_get.md) | [Wenden Sie sich an](contact.md) |Schreibgeschützte Eigenschaften und Beziehungen zwischen Kontaktobjekt.|
|[Erstellen](../api/user_post_contacts.md) | [Wenden Sie sich an](contact.md) |Hinzufügen eines Kontakts in den Stammordner Kontakte oder an den Endpunkt Kontakte von einer anderen Kontaktordner.|
|[Update](../api/contact_update.md) | [Wenden Sie sich an](contact.md) |Contact-Objekt zu aktualisieren. |
|[Löschen](../api/contact_delete.md) | Keine |Contact-Objekt zu löschen. |
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine Erweiterung der offenen Typ Daten und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assistantName|String|Der Name des Assistenten des Kontakts.|
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Kontakts. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|businessAddress|[Physikalische Adresse](physicaladdress.md)|Business-Adresse des Kontakts.|
|businessHomePage|String|Die Business-Homepage des Kontakts.|
|businessPhones|String-Auflistung|Der Kontakt geschäftlichen Telefonnummer.|
|Kategorien|String-Auflistung|Die Kategorien, die dem Kontakt zugeordnet.|
|changeKey|String|Gibt die Version des Kontakts an. Jedes Mal, wenn der Kontakt geändert wird, ändert ChangeKey sowie. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen.|
|untergeordnete Elemente|String-Auflistung|Die Namen der untergeordneten Elemente des Kontakts.|
|Firma|String|Der Name der Firma des Kontakts.|
|createdDateTime|DateTimeOffset|Der Zeitpunkt, an der Kontakt erstellt wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Abteilung|String|Die Abteilung des Kontakts.|
|displayName|String|Anzeigename des Kontakts.|
|emailAddresses|[EmailAddress](emailaddress.md) -Auflistung|Der Kontakt-e-Mail-Adressen.|
|fileAs|String|Der Namen des Kontakts wird unter eingereicht werden.|
|Generierung|String|Generierung des Kontakts.|
|Vorname|String|Vorname des Kontakts.|
|homeAddress|[Physikalische Adresse](physicaladdress.md)|Die Adresse des Kontakts Startseite.|
|homePhones|String-Auflistung|Private Rufnummern eines Kontakts.|
|id|String|Eindeutiger Bezeichner des Kontakts. Schreibgeschützt.|
|imAddresses|String-Auflistung|Der Kontakt instant messaging (IM) Adressen.|
|Initialen|String|Initialen des Kontakts.|
|jobTitle|String|Position des Kontakts.|
|lastModifiedDateTime|DateTimeOffset|Die Zeit, die der Kontakt geändert wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Vorgesetzter|String|Der Name des Vorgesetzten des Kontakts.
|middleName|String|Vorname des Kontakts.|
|mobilePhone|String|Die Mobiltelefonnummer des Kontakts.|
|Spitzname|String|Spitzname des Kontakts.|
|officeLocation|String|Der Speicherort der Office des Kontakts.|
|otherAddress|[Physikalische Adresse](physicaladdress.md)|Andere Adressen für den Kontakt.|
|parentFolderId|String|Die ID des übergeordneten Ordners des Kontakts.|
|personalNotes|String|Der Benutzer Notizen zum Kontakt.|
|Beruf|String|Der Beruf des Kontakts.|
|spouseName|String|Der Name des Kontakts Partner/in.|
|Nachname|String|Den Nachnamen des Kontakts.|
|title|String|Titel des Kontakts.|
|yomiCompanyName|String|Der phonetische Japanisch Firmenname des Kontakts an.|
|yomiGivenName|String|Dem phonetischen japanische angegebenen Namen (Vorname) des Kontakts.|
|yomiSurname|String|Der phonetische Japanisch Nachname (Nachname) des Kontakts.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der geöffneten Typ Daten Erweiterungen für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|
|Foto|[profilePhoto](profilephoto.md)| Optional Kontaktbild. Sie können abrufen oder festlegen ein Fotos für einen Kontakt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "photo"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.contact"
}-->

```json
{
  "assistantName": "string",
  "birthday": "String (timestamp)",
  "businessAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "businessHomePage": "string",
  "businessPhones": ["string"],
  "categories": ["string"],
  "changeKey": "string",
  "children": ["string"],
  "companyName": "string",
  "createdDateTime": "String (timestamp)",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.emailAddress"}],
  "fileAs": "string",
  "generation": "string",
  "givenName": "string",
  "homeAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "homePhones": ["string"],
  "id": "string (identifier)",
  "imAddresses": ["string"],
  "initials": "string",
  "jobTitle": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "manager": "string",
  "middleName": "string",
  "mobilePhone": "string",
  "nickName": "string",
  "officeLocation": "string",
  "otherAddress": {"@odata.type": "microsoft.graph.physicalAddress"},
  "parentFolderId": "string",
  "personalNotes": "string",
  "profession": "string",
  "spouseName": "string",
  "surname": "string",
  "title": "string",
  "yomiCompanyName": "string",
  "yomiGivenName": "string",
  "yomiSurname": "string",

  "photo": { "@odata.type": "microsoft.graph.profilePhoto" }
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contact resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
