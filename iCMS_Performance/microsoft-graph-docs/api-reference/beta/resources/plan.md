# <a name="plan-resource-type"></a>Plan Ressourcentyp

Die Ressource Plan stellt einen Plan in Office 365. Ein Plan kann eine [Gruppe](group.md) Besitz und enthält eine Auflistung von [Aufgaben](task.md). Sie können auch eine Auflistung von [Buckets](bucket.md)verfügen. Jedes Plan Objekt ist ein [Details](plandetails.md) -Objekt die Weitere Informationen zu den Plan enthalten kann. Finden Sie unter [Übersicht über die](tasks_overview.md) Weitere Informationen zu den Beziehungen zwischen Gruppen, Planen und Aufgabe.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "assignedToTaskBoard",
    "bucketTaskBoard",
    "buckets",
    "details",
    "progressTaskBoard",
    "tasks"
  ],
  "@odata.type": "microsoft.graph.plan"
}-->

```json
{
  "createdBy": "string",
  "id": "string (identifier)",
  "owner": "string",
  "title": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|createdBy|String|Schreibgeschützt. Benutzer-Id mit dem Plan erstellt wird.|
|id|String| Schreibgeschützt. ID des Plans. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst. |
|Besitzer|String|[Gruppe](group.md) `id` nach dem Planen gehört. Eine gültige Gruppe muss vorhanden sein, bevor Sie dieses Feld festgelegt werden kann. Einmal festgelegt ist, kann dies nur vom Besitzer aktualisiert werden.|
|title|String| Erforderlich. Titel des Plans. In der Regel ist dies der Name der Gruppe der Besitzer des Plans festgelegt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|assignedToTaskBoard|[planTaskBoard](plantaskboard.md)| Schreibgeschützt. Verwendet, um die Pinnwand Vorgangsansicht ordnungsgemäß gerendert wird, wenn nach AssignedTo gruppiert.|
|bucketTaskBoard|[planTaskBoard](plantaskboard.md)| Schreibgeschützt. Zum Rendern der Buckets ordnungsgemäß in der Vorgangsansicht Pinnwand verwendet.|
|Buckets|[Bucket](bucket.md) -Auflistung| Schreibgeschützt. NULL-Werte zulässt. Die Auflistung der Buckets im Plan. |
|Details|[planDetails](plandetails.md)| Schreibgeschützt. Zusätzliche Informationen zu planen. |
|progressTaskBoard|[planTaskBoard](plantaskboard.md)| Schreibgeschützt. Verwendet, um die Pinnwand Vorgangsansicht ordnungsgemäß gerendert wird, wenn durch den Fortschritt gruppiert.|
|Aufgaben|Auflistung von [Workflowaufgaben](task.md)| Schreibgeschützt. NULL-Werte zulässt. Auflistung von Aufgaben in den Plan. |

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Plan abrufen](../api/plan_get.md) | [Plan](plan.md) |Eigenschaften lesen und Beziehungen Plan-Objekts.|
|[Liste buckets](../api/plan_list_buckets.md) |[Bucket](bucket.md) -Auflistung| Rufen Sie eine Auflistung der Bucket-Objekts.|
|[Listenaufgaben](../api/plan_list_tasks.md) |Auflistung von [Workflowaufgaben](task.md)| Rufen Sie eine Auflistung von Workflowaufgaben-Objekt. |
|[Erstellen eines Plans](../api/plan_post_plans.md) | [Plan](plan.md) | Erstellen eines neuen Plans. |
|[Plan aktualisieren](../api/plan_update.md) | Keine    |Update-Plan-Objekt. |
|[Plan löschen](../api/plan_delete.md) | Keine |Plan-Objekt zu löschen. |
|[Liste Pläne](../api/plan_list.md) | [Plan](plan.md) -Auflistung | Rufen Sie eine Auflistung der Plan-Objekts. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "plan resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->