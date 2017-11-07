# <a name="contact-resource-type"></a>Wenden Sie sich an Ressourcentyp

Ein Kontakt ist ein Element in Outlook können Sie organisieren und Speichern von Informationen zu Personen und Organisationen, mit denen Sie kommunizieren. Kontakte sind im Kontakteordner enthalten.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "extensions",
    "photo"
  ],
  "@odata.type": "microsoft.graph.contact"
}-->

```json
{
  "assistantName": "string",
  "birthday": "String (timestamp)",
  "categories": ["string"],
  "changeKey": "string",
  "children": ["string"],
  "companyName": "string",
  "createdDateTime": "String (timestamp)",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.emailAddress"}],
  "fileAs": "string",
  "gender": "string",
  "generation": "string",
  "givenName": "string",
  "id": "string (identifier)",
  "imAddresses": ["string"],
  "initials": "string",
  "jobTitle": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "manager": "string",
  "middleName": "string",
  "nickName": "string",
  "officeLocation": "string",
  "parentFolderId": "string",
  "personalNotes": "string",
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "postalAddresses": [{"@odata.type": "microsoft.graph.physicalAddress"}],
  "profession": "string",
  "spouseName": "string",
  "surname": "string",
  "title": "string",
  "websites": [{"@odata.type": "microsoft.graph.website"}],
  "weddingAnniversary": "date",
  "yomiCompanyName": "string",
  "yomiGivenName": "string",
  "yomiSurname": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assistantName|String|Der Name des Assistenten des Kontakts.|
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Kontakts. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Kategorien|Zeichenfolgenauflistung|Die Kategorien, die dem Kontakt zugeordnet.|
|changeKey|String|Gibt die Version des Kontakts an. Jedes Mal, wenn der Kontakt geändert wird, ändert ChangeKey sowie. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen.|
|untergeordnete Elemente|Zeichenfolgenauflistung|Die Namen der untergeordneten Elemente des Kontakts.|
|Firma|String|Der Name der Firma des Kontakts.|
|createdDateTime|DateTimeOffset|Der Zeitpunkt, an der Kontakt erstellt wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Abteilung|String|Die Abteilung des Kontakts.|
|displayName|String|Anzeigename des Kontakts.|
|emailAddresses|[EmailAddress](emailaddress.md) -Auflistung|Der Kontakt-e-Mail-Adressen.|
|fileAs|String|Der Namen des Kontakts wird unter eingereicht werden.|
|Geschlecht |String |Geschlecht des Kontakts. |
|Generierung|String|Generierung des Kontakts.|
|Vorname|String|Vorname des Kontakts.|
|id|String|Eindeutiger Bezeichner des Kontakts. Schreibgeschützt.|
|imAddresses|Zeichenfolgenauflistung|Der Kontakt instant messaging (IM)-Adressen.|
|Initialen|String|Initialen des Kontakts.|
|jobTitle|String|Position des Kontakts.|
|lastModifiedDateTime|DateTimeOffset|Die Zeit, die der Kontakt geändert wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Vorgesetzter|String|Der Name des Vorgesetzten des Kontakts.
|middleName|String|Vorname des Kontakts.|
|Spitzname|String|Spitzname des Kontakts.|
|officeLocation|String|Der Speicherort der Office des Kontakts.|
|parentFolderId|String|Die ID des übergeordneten Ordners des Kontakts.|
|personalNotes|String|Der Benutzer Hinweise zu den Kontakt.|
|Telefone |[Telefon](phone.md) -Auflistung |Telefonnummern für den Kontakt zugeordnet ist, beispielsweise Telefon (privat), Mobiltelefon und Telefon (geschäftlich) |
|postalAddresses |[physikalische Adresse](physicalAddress.md) -Auflistung |Der Kontakt zugeordnete Adressen home beispielsweise Adresse und Geschäftsadresse. |
|Beruf|String|Der Beruf des Kontakts.|
|spouseName|String|Der Name des Kontakts Partner/in.|
|Nachname|String|Den Nachnamen des Kontakts.|
|title|String|Titel des Kontakts.|
|Websites |[die Websitesammlung](website.md)|Websites, die dem Kontakt zugeordnet werden. |
|weddingAnniversary |Date |Hochzeitstag des Kontakts. |
|yomiCompanyName|String|Der phonetische Japanisch Firmenname des Kontakts an.|
|yomiGivenName|String|Dem phonetischen japanische angegebenen Namen (Vorname) des Kontakts.|
|yomiSurname|String|Der phonetische Japanisch Nachname (Nachname) des Kontakts.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der geöffneten Typ Daten Erweiterungen für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der Mehrfachwert erweiterte Eigenschaften für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|
|Foto|[Foto](profilephoto.md)| Optional Kontaktbild. Sie können abrufen oder festlegen ein Fotos für einen Kontakt.|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der einwertig erweiterte Eigenschaften für den Kontakt definiert. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von Kontakt](../api/contact_get.md) | [Wenden Sie sich an](contact.md) |Schreibgeschützte Eigenschaften und Beziehungen zwischen Kontaktobjekt.|
|[Erstellen](../api/user_post_contacts.md) | [Wenden Sie sich an](contact.md) |Fügen Sie einen Kontakt in den Stammordner Kontakte oder Endpunkts eines anderen Kontakts Ordners Kontakte.|
|[Update](../api/contact_update.md) | [Wenden Sie sich an](contact.md) |Contact-Objekt zu aktualisieren. |
|[Löschen](../api/contact_delete.md) | Keine |Contact-Objekt zu löschen. |
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine Erweiterung der offenen Typ Daten und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|
|[Erweiterte Eigenschaft einwertig erstellen](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[Wenden Sie sich an](contact.md)  |Erstellen Sie eine oder mehrere einwertig erweiterte Eigenschaften in einem neuen oder vorhandenen Kontakt aus.   |
|[Abrufen von Kontakt mit erweiterten Eigenschaft einwertig](../api/singlevaluelegacyextendedproperty_get.md)  | [Wenden Sie sich an](contact.md) | Abrufen von Kontakten, die einen erweiterte Eigenschaft mithilfe von Single-Wert enthalten `$expand` oder `$filter`. |
|[Erstellen von erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [Wenden Sie sich an](contact.md) | Erstellen Sie eine oder mehrere erweiterte mehrwertige Eigenschaften in einem neuen oder vorhandenen Kontakt aus.  |
|[Abrufen von Kontakt mit erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_get.md)  | [Wenden Sie sich an](contact.md) | Abrufen ein Kontakts, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`. |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contact resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->