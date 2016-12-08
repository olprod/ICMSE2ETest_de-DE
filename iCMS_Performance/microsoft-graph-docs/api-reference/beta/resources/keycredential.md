# <a name="keycredential-resource-type"></a>Ressourcentyp keyCredential

Enthält wichtige Anmeldeinformationen eine Anwendung oder einen Dienstprinzipal zugeordnet ist. Die **KeyCredentials** -Eigenschaft der [Anwendung](application.md) und [ServicePrincipal](serviceprincipal.md) Entitäten ist eine Auflistung von **KeyCredential**.


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.keyCredential"
}-->

```json
{
  "customKeyIdentifier": "binary",
  "endDate": "String (timestamp)",
  "keyId": "guid",
  "startDate": "String (timestamp)",
  "type": "string",
  "usage": "string",
  "value": "binary"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|customKeyIdentifier|Binary|            |
|endDate|DateTimeOffset|Datum und Uhrzeit, zu der die Anmeldeinformationen abläuft. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Schlüssel-ID|Guid|Der eindeutige Bezeichner (GUID) für die-Taste.|
|startDate|DateTimeOffset|Datum und Uhrzeit, an dem die Anmeldeinformationen gültig ist. Der Zeitstempeltyp Datum und Uhrzeit Informationen mit ISO 8601-Format darstellt und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Typ|String|Die Art der wichtigsten Anmeldeinformationen. beispielsweise "Symmetrisch".|
|Verwendung|String|Eine Zeichenfolge, die den Zweck beschreibt, für den der Schlüssel verwendet werden kann. beispielsweise "Überprüfen".|
|value|Binary|            |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "keyCredential resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->