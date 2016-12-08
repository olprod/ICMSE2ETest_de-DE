# <a name="notesoperation-resource-type"></a>Ressourcentyp notesOperation

Der Status der bestimmte langer OneNote-Vorgänge.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.notesoperation"
}-->

```json
{
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.notesOperationError"},
  "id": "string (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceId": "string",
  "resourceLocation": "string",
  "status": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|createdDateTime| DateTimeOffset |Die Anfangszeit des Vorgangs.|
|Problem|[notesOperationError](notesoperationerror.md)|Der Fehler, die von der Operation zurückgegeben.|
|id|string|Die Id des Vorgangs. Schreibgeschützt.|
|lastActionDateTime| DateTimeOffset |Der Zeitpunkt der letzten Aktion des Vorgangs.|
|resourceId|string|Die Ressourcen-Id.|
|resourceLocation|string|Die Ressourcen-URI für das Objekt. Beispielsweise ist der Ressourcen-URI für eine kopierte Seite oder eines Abschnitts. |
|status|string|Der aktuelle Status des Vorgangs: `notstarted`, `running`, `completed`,`failed` |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get-Vorgang](../api/notesoperation_get.md) | [NotesOperation](notesoperation.md) |Rufen Sie den Status des Vorgangs. |


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notesOperation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
