# <a name="taskboardtaskformat-resource-type"></a>Ressourcentyp taskBoardTaskFormat

Die Ressource TaskBoardTaskFormat stellt die Informationen verwendet, um eine Aufgabe in einer Vorgangsansicht Pinnwand ordnungsgemäß zu rendern. Jede [Aufgabe](task.md) müssen drei TaskBoardTaskFormat-Objekte, wie drei Pinnwand Vorgangsansichten, denen einen Vorgang handelt.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.taskboardtaskformat"
}-->

```json
{
  "id": "string (identifier)",
  "orderHint": "string",
  "type": "String (identifier)"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| Schreibgeschützt. ID des Vorgangs. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst. |
|orderHint|String| Verwendet, um die relative Reihenfolge der Vorgänge in der vertikalen in der Vorgangsansicht Pinnwand festzulegen. Betrachten Sie drei Vorgänge in der Reihenfolge der: `'O'`, `'P'`, `'Q'`. So verschieben Sie `'P'` an den Anfang der vertikalen, legen seine `'orderHint'` zu kleiner als der von `'O'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|Typ|String| Schreibgeschützt. Verwendet, um den Typ der Vorgangsansicht Pinnwand festzulegen, in denen dieses Objekt verwendet wird, um die Aufgabe zu rendern. Mögliche Werte sind: `progress`, `assignedTo`, `bucket`. |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von taskBoardTaskFormat](../api/taskboardtaskformat_get.md) | [taskBoardTaskFormat](taskboardtaskformat.md) |Lesen Sie Eigenschaften und Beziehungen des TaskBoardTaskFormat-Objekts.|
|[TaskBoardTaskFormat aktualisieren](../api/taskboardtaskformat_update.md) | Keine  |TaskBoardTaskFormat-Objekt zu aktualisieren. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "taskBoardTaskFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->