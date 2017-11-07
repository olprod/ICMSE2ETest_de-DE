# <a name="verifieddomain-resource-type"></a>Ressourcentyp verifiedDomain

Gibt eine Domäne für einen Mandanten an. Die **VerifiedDomains** -Eigenschaft der Entität [Organisation](organization.md) ist eine Auflistung von **VerifiedDomain**.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Funktionen|String|Beispielsweise "E-Mail", "OfficeCommunicationsOnline".|
|isDefault|Boolean|                **true,** Wenn dies die Standarddomäne den Mandanten zugeordnet ist. anderenfalls **false**.            |
|isInitial|Boolean|**true,** Wenn dies die erste Domäne, die den Mandanten zugeordnet ist. andernfalls **"false"**|
|name|String|Der Domänenname; beispielsweise "contoso.onmicrosoft.com"|
|Typ|String|Beispielsweise verwaltet"."|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.verifieddomain"
}-->

```json
{
  "capabilities": "string",
  "isDefault": true,
  "isInitial": true,
  "name": "string",
  "type": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "verifiedDomain resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
