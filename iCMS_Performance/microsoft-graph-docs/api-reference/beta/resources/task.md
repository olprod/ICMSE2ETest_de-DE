# <a name="task-resource-type"></a>Ressourcentyp

Die Aufgabe Ressource repräsentiert eine Aufgabe in Office 365. Eine Aufgabe ist in einem [Plan](plan.md) enthalten und kann ein [Bucket](bucket.md) in einem Plan zugewiesen werden. Jede Task-Objekt ist ein [Details](taskdetails.md) -Objekt, das Informationen über die Aufgabe enthalten kann. Finden Sie unter [Übersicht über die](tasks_overview.md) Weitere Informationen zur Beziehung zwischen Gruppen, Plan und Aufgabe.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "assignedToTaskBoardFormat",
    "bucketTaskBoardFormat",
    "details",
    "progressTaskBoardFormat"
  ],
  "@odata.type": "microsoft.graph.task"
}-->

```json
{
  "appliedCategories": {"@odata.type": "microsoft.graph.appliedCategoriesCollection"},
  "assignedBy": "string",
  "assignedDateTime": "String (timestamp)",
  "assignedTo": "string",
  "assigneePriority": "string",
  "bucketId": "string",
  "completedDateTime": "String (timestamp)",
  "conversationThreadId": "string",
  "createdBy": "string",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "hasDescription": true,
  "id": "string (identifier)",
  "orderHint": "string",
  "percentComplete": 1024,
  "planId": "string",
  "previewType": "String",
  "startDateTime": "String (timestamp)",
  "title": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|appliedCategories|[appliedCategoriesCollection](appliedcategoriescollection.md)|Die Kategorien, auf denen die Aufgabe angewendet wurde. Finden Sie unter AppliedCategoriesCollection für mögliche Werte. |
|assignedBy|String|Schreibgeschützt. Benutzer-Id mit dem die Aufgabe zugewiesen ist.|
|assignedDateTime|DateTimeOffset|Schreibgeschützt. Datum und Uhrzeit, zu der die Aufgabe zugewiesen ist. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|assignedTo|String|Benutzer-Id, denen die Aufgabe zugewiesen ist. |
|assigneePriority|String|Zum Festlegen der Reihenfolge der relativen Priorität Aufgaben zugewiesen sind, die dem Benutzer in einer Listenansicht verwendet. Betrachten Sie drei Vorgänge in der Reihenfolge der Priorität: `'A'`, `'B'`, `'C'`. So verschieben Sie `'B'` im oberen Bereich festlegen seiner `assignneePriority` zu kleiner als der von `'A'`. Vergleich wird ein Zeichenfolgenvergleich für Ordinale. |
|bucketId|String|Bucket-Id, zu der die Aufgabe gehört. Bucket muss in den Plan befinden, das die Aufgabe ist.|
|completedDateTime|DateTimeOffset|Schreibgeschützt. Datum und Uhrzeit an, die `'percentComplete'` des Vorgangs ist auf festgelegt `'100'`. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|conversationThreadId|String|Thread-Id der Unterhaltung auf die Aufgabe. Dies ist die Id des Unterhaltung Thread-Objekts in der Gruppe erstellt. |
|createdBy|String|Schreibgeschützt. Benutzer-Id mit dem die Aufgabe erstellt wird. |
|createdDateTime|DateTimeOffset|Schreibgeschützt. Datum und Uhrzeit, an dem die Aufgabe erstellt wird. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|dueDateTime|DateTimeOffset|Datum und Uhrzeit, an dem die Aufgabe fällig ist. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|hasDescription|Boolean|Schreibgeschützt. Wert ist `true` hat das Objekt Details der Aufgabe eine Beschreibung der nicht leeren und `false` andernfalls.|
|id|String|Schreibgeschützt. ID des Vorgangs. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst. |
|orderHint|String|Verwendet, um die relative Reihenfolge der Aufgaben in einer Listenansicht festzulegen. Betrachten Sie drei Vorgänge in der Reihenfolge der: `'X'`, `'Y'`, `'Z'`. So verschieben Sie `'Y'` festlegen im oberen Bereich, dessen `orderHint` zu kleiner als der von `'X'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|percentComplete|Int32|Prozentsatz der Fertigstellung des Vorgangs. Bei Festlegung auf `100`, gilt die Aufgabe als abgeschlossen. |
|"PlanID"|String|Plan-Id, zu der die Aufgabe gehört. Einmal festgelegt ist, kann dies aktualisiert werden. |
|previewType|String| Schreibgeschützt. Hierdurch wird den Typ der Vorschau, die für den Vorgang wird angezeigt. Mögliche Werte sind: `automatic`, `noPreview`, `checklist`, `description`, `reference`.|
|startDateTime|DateTimeOffset|Datum und Uhrzeit, an dem die Aufgabe beginnt. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|title|String|Erforderlich. Titel der Aufgabe. |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assignedToTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| Schreibgeschützt. Verwendet, um den Vorgang in der Vorgangsansicht Pinnwand Wenn nach AssignedTo gruppiert ordnungsgemäß gerendert. |
|bucketTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| Schreibgeschützt. Verwendet, um den Vorgang in der Vorgangsansicht Pinnwand Wenn nach Bucket gruppiert ordnungsgemäß gerendert.|
|Details|[taskDetails](taskdetails.md)| Schreibgeschützt. Weitere Informationen über die Aufgabe. Enthält `description`, `references`, `checklist` usw.. |
|progressTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| Schreibgeschützt. Verwendet, um den Vorgang in der Vorgangsansicht Pinnwand Wenn nach Status gruppiert ordnungsgemäß gerendert. |

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Aufgabe abrufen](../api/task_get.md) | [Aufgabe](task.md) |Eigenschaften lesen und Beziehungen des Task-Objekts.|
|[Aufgabe erstellen](../api/task_post_tasks.md) | [Aufgabe](task.md) | Erstellen eines neuen Task-Objekts. |
|[Update-task](../api/task_update.md) | Keine    |Aktualisieren von Task-Objekts. |
|[Vorgang löschen](../api/task_delete.md) | Keine |Task-Objekt zu löschen. |
|[List-Aufgaben](../api/task_list.md) | Auflistung von [Workflowaufgaben](task.md) | Rufen Sie eine Auflistung von Workflowaufgaben-Objekt. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "task resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->