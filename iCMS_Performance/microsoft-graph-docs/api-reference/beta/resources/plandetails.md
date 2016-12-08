# <a name="plandetails-resource-type"></a>PlanDetails Ressourcentyp

Die Ressource PlanDetails stellt zusätzliche Informationen zum eines Plans. Jedes [Plan](plan.md) -Objekt ist ein Details-Objekt.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.plandetails"
}-->

```json
{
  "category0Description": "string",
  "category1Description": "string",
  "category2Description": "string",
  "category3Description": "string",
  "category4Description": "string",
  "category5Description": "string",
  "id": "string (identifier)",
  "sharedWith": {"@odata.type": "microsoft.graph.userIdCollection"}
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|category0Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|category1Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|category2Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|category3Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|category4Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|category5Description|String| Beschreibung der Kategorie (oder Beschriftung), das die Aufgabe zugewiesen werden kann. |
|id|String| Schreibgeschützt. ID des Plans. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst.|
|sharedWith|[userIdCollection](useridcollection.md)| Liste der Benutzer-Ids, denen mit diesem Plan freigegeben werden. Wenn Sie Office 365 Gruppen nutzen, verwenden Sie die API-Gruppen zum Verwalten der Gruppenmitgliedschaft zum Planen [der Gruppe](group.md) freigeben. Sie können auch vorhandene Mitglieder der Gruppe zu dieser Auflistung hinzufügen, obwohl es nicht erforderlich, damit sie Zugriff auf den Besitz der Gruppe Plan ist. |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[PlanDetails abrufen](../api/plandetails_get.md) | [planDetails](plandetails.md) |Lesen Sie Eigenschaften und Beziehungen PlanDetails-Objekts.|
|[PlanDetails aktualisieren](../api/plandetails_update.md) | Keine  |PlanDetails-Objekt zu aktualisieren. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "planDetails resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->