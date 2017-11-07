# <a name="directoryobject-resource-type"></a>Ressourcentyp directoryObject

Azure Active Directory-Objekt darstellt. Der **DirectoryObject** -Typ ist den Basistyp für viele andere Verzeichnistypen für Entität.


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von directoryObject](../api/directoryobject_get.md) | [directoryObject](directoryobject.md) |Lesen Sie die Eigenschaften eines Verzeichnisobjekts.|
|[Löschen](../api/directoryobject_delete.md) | Keine |Löscht ein Verzeichnisobjekt. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String|Eine Guid, die den eindeutigen Bezeichner für das Objekt ist; beispielsweise 12345678-9abc-def0-1234-56789abcde. -Taste. Nicht NULL-Werte zulässt. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryObject"
}-->

```json
{
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryObject resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
