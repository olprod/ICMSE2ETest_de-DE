# <a name="checklistitemcollection-resource-type"></a>Ressourcentyp checklistItemCollection

Die Ressource ChecklistItemCollection * stellt die Auflistung der Prüfliste Elemente für einen Vorgang. Es ist Teil des [Aufgabendetails](taskdetails.md) -Objekts. Der Wert in der Eigenschaft-Wert-Paar ist das [ChecklistItem](checklistitem.md) -Objekt.

* Beachten Sie, dass dies vom Typ geöffnet ist.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.checklistItemCollection"
}-->

```json
{
  "String-value":
  {
    "isChecked": true,
    "lastModifiedBy": "String-value",
    "lastModifiedByDateTime": "String(timestamp)",
    "orderHint": "String-value",
    "title": "String-value"
  }
}
```
Beispiel

```json
{
  "3a73c9dd-fb47-4230-9c0f-b80788fb0f9b": // client-generated GUID
  {
    "@odata.type": "microsoft.graph.checklistItem", // required in PATCH requests to edit the checklist on a task
    "isChecked": true,
    "lastModifiedBy": "4e971521-101a-4311-94f4-0917d7218b4e",
    "lastModifiedByDateTime": "2015-09-21T17:45:12.039Z",
    "orderHint": "0009005756397228702",
    "title": "Get stamps"
  },
  "5f36f5b2-1ec0-4c48-9c75-ed59429516c5":
  {
     "@odata.type": "microsoft.graph.checklistItem",
    "isChecked": false,
    "lastModifiedBy": "4e971521-101a-4311-94f4-0917d7218b4e",
    "lastModifiedByDateTime": "2015-09-21T17:45:12.039Z",
    "orderHint": "0004105723397228784",
    "title": "Mail card at UPS"
  }
}

```


## <a name="properties"></a>Eigenschaften
Eigenschaften vom Typ Open können vom Client definiert werden. In diesem Fall der Client sollte als Eigenschaften **GUIDs** bereitstellen und deren Werte muss [ChecklistItem](checklistitem.md) -Objekte. Beispiel wird oben angezeigt. Wenn ein Element in der Prüfliste entfernen möchten, legen Sie den Wert der Eigenschaft `null`.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "checklistItemCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->