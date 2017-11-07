# <a name="localeinfo-resource-type"></a>LocaleInfo Ressourcentyp

Informationen über das Gebietsschema, einschließlich der bevorzugten Sprache und Land/Region des angemeldeten Benutzers.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Gebietsschema|string|Eine Darstellung Gebietsschema für den Benutzer, der den Benutzer enthält bevorzugte Sprache und Land/Region. Beispielsweise "En-us". Die Sprachkomponente folgt 2 folgenden Buchstabencodes gemäß Definition im [ISO 639-1](http://www.iso.org/iso/home/standards/language_codes.htm), und die Komponente Land folgt 2 folgenden Buchstabencodes gemäß Definition im [ISO 3166-1 Alpha-2](http://www.iso.org/iso/country_codes.htm).|
|displayName|string|Einen Namen, die das Gebietsschema des Benutzers in natürlicher Sprache, z. B. "Englisch (USA)" darstellt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.localeInfo"
}-->

```json
{
  "locale": "string",
  "displayName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "localeInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->