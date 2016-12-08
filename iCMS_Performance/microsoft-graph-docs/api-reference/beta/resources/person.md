# <a name="person-resource-type"></a>Ressourcentyp Person

Die Aggregation von Informationen über die von einer Person über e-Mail, Kontakte und sozialen Netzwerken. Personen können lokalen Kontakten, Kontakte aus für soziale Netzwerke, Ihrer Organisation Verzeichnis und Personen von letzte Kommunikation (wie e-Mail und Skype) sein.

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen der person](../api/person_get.md) | [Person](person.md) |Lesen Sie Eigenschaften und die Beziehungen eines Person-Objekts.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Geburtsdatum|string|Geburtsdatum der Person.|
|Firma|string|Der Name der Firma der Person.|
|Abteilung|string|Die Person Abteilung.|
|displayName|string|Anzeigename der Person.|
|emailAddresses|[RankedEmailAddress](rankedemailaddress.md) -Auflistung|Die Person e-Mail-Adressen.|
|Vorname|string|Die Person angegebenen Namen.|
|id|string|Eindeutiger Bezeichner der Person. Schreibgeschützt.|
|isFavorite|boolean|`true`Wenn der Benutzer diese Person als Favoriten gekennzeichnet hat.|
|mailboxType|string|Der Typ des Postfachs an, die durch die e-Mail-Adresse der Person dargestellt wird.|
|officeLocation|string|Der Speicherort der Office der Person.|
|personNotes|string|Formfreies weist darauf hin, die der Benutzer über diese Person vorgenommen hat.|
|personType|string|Der Typ der Person, beispielsweise Verteilerliste.|
|Telefone|[Telefon](phone.md) -Auflistung|Telefonnummern der Person.|
|postalAddresses|[Standort](location.md) -Auflistung|Die Person Adressen.|
|Beruf|string|Die Person Beruf.|
|Datenquellen|[PersonDataSource](persondatasource.md) -Auflistung|Die Quellen die Benutzerdaten stammen aus, beispielsweise Directory oder Outlook-Kontakte.|
|Nachname|string|Nachname der Person.|
|title|string|Titel der Person.|
|userPrincipalName|string|Der Benutzerprinzipalname (UPN) der Person ein. Der Benutzerprinzipalname ist ein Internet-Schreibweise Anmeldenamen der Person, die basierend auf dem Internet standard [RFC 822](http://www.ietf.org/rfc/rfc0822.txt). Standardmäßig sollte dies die e-Mail-Namen der Person zuordnen. Die allgemeine-Format vorliegtalias@domain.|
|Websites|[die Websitesammlung](website.md)|Die Person-Websites.|
|yomiCompany|string|Der phonetische japanische Name der Firma der Person.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.person"
}-->

```json
{
  "birthday": "string",
  "companyName": "string",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.rankedEmailAddress"}],
  "givenName": "string",
  "id": "string (identifier)",
  "isFavorite": true,
  "mailboxType": "string",
  "officeLocation": "string",
  "personNotes": "string",
  "personType": "string",
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "postalAddresses": [{"@odata.type": "microsoft.graph.location"}],
  "profession": "string",
  "sources": [{"@odata.type": "microsoft.graph.personDataSource"}],
  "surname": "string",
  "title": "string",
  "userPrincipalName": "string",
  "websites": [{"@odata.type": "microsoft.graph.website"}],
  "yomiCompany": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "person resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
