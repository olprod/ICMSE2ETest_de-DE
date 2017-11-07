# <a name="taskdetails-resource-type"></a>Ressourcentyp taskDetails

Die Ressource TaskDetails stellt zusätzliche Informationen zu einer Aufgabe. Jede [Task](task.md) -Objekt ist ein Details-Objekt.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.taskdetails"
}-->

```json
{
  "checklist": {"@odata.type": "microsoft.graph.checklistItemCollection"},
  "completedBy": "string",
  "description": "string",
  "id": "string (identifier)",
  "previewType": "String",
  "references": {"@odata.type": "microsoft.graph.externalReferenceCollection"}
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Prüfliste|[checklistItemCollection](checklistitemcollection.md)| Die Auflistung der Prüfliste Elemente für den Vorgang.|
|completedBy|String| Benutzer-Id nach dem Abschluss des Vorgangs. |
|description|String| Beschreibung der Aufgabe. |
|id|String| Schreibgeschützt. ID des Vorgangs. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst.|
|previewType|String| Hierdurch wird den Typ der Vorschau, die für den Vorgang wird angezeigt. Mögliche Werte sind: `automatic`, `noPreview`, `checklist`, `description`, `reference`.|
|Verweise|[externalReferenceCollection](externalreferencecollection.md)| Die Auflistung der Verweise auf die Aufgabe. |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von taskDetails](../api/taskdetails_get.md) | [taskDetails](taskdetails.md) |Lesen Sie Eigenschaften und Beziehungen TaskDetails-Objekts.|
|[Update taskDetails](../api/taskdetails_update.md) | Keine|Aktualisieren Sie TaskDetails-Objekts. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "taskDetails resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->