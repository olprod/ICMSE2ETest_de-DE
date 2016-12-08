# <a name="useridcollection-resource-type"></a>Ressourcentyp userIdCollection

Die Ressource UserIdCollection * stellt die Liste der Benutzer-Ids, denen für einen [Plan](plan.md) freigegeben ist. Wenn Sie Office 365 Gruppen nutzen, verwenden Sie die API-Gruppen zum Verwalten der Gruppenmitgliedschaft zum Planen [der Gruppe](group.md) freigeben. Sie können auch vorhandene Mitglieder der Gruppe zu dieser Auflistung hinzufügen, obwohl es nicht erforderlich, damit sie Zugriff auf den Besitz der Gruppe Plan ist.

* Beachten Sie, dass dies vom Typ geöffnet ist.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.userIdCollection"
}-->
```json
{
  "String-value": true
}
```

Beispiel
```json
{
  "400723e1-102b-43aa-aba9-f35524827084": true, // property name is user id
  "f117339e-c914-4a9c-9b66-1c062b027556": true,
  "e886d105-23b9-47e2-bde1-757e75ee4a28": true
}

```### Properties
Properties of an Open Type can be defined by the client. In this case, the client should provide user ids as properties with their values being the `true` boolean. When user ids are no longer shared with, properties are automatically removed by setting their values to the `false` boolean.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "userIdCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->