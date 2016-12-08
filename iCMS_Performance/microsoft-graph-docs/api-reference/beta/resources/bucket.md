# <a name="bucket-resource-type"></a>Bucket Ressourcentyp

Die Ressource Bucket stellt ein Bucket (oder "benutzerdefinierte Spalte") für Aufgaben in einem Plan in Office 365. Es kann ist in einem [Plan](plan.md) enthalten und eine Auflistung von [Aufgaben](task.md).

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "tasks"
  ],
  "@odata.type": "microsoft.graph.bucket"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string",
  "orderHint": "string",
  "planId": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|String| Schreibgeschützt. ID des Bucket. Es ist eine 28 Zeichen lang und Groß-/Kleinschreibung beachtet. [Format Validierung](tasks_identifiers_disclaimer.md) erfolgt für den Dienst.|
|name|String| Name des Bucket. |
|orderHint|String| Verwendet, um die relative Reihenfolge der Buckets in der Vorgangsansicht Pinnwand festzulegen. Berücksichtigen Sie drei Buckets in der Reihenfolge der: `'E'`, `'F'`, `'G'`. So tätigen `'F'` der erste Bucket, legen seine `'orderHint'` zu kleiner als der von `'x'`. Vergleich wird ein ordinal Zeichenfolgenvergleich.|
|"PlanID"|String| Plan-Id zu dem Bucket gehört. |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Aufgaben|Auflistung von [Workflowaufgaben](task.md)| Schreibgeschützt. NULL-Werte zulässt. Auflistung von Aufgaben im Bucket. |

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erste bucket](../api/bucket_get.md) | [Bucket](bucket.md) |Eigenschaften lesen und Beziehungen Bucket-Objekts.|
|[Listenaufgaben](../api/bucket_list_tasks.md) |Auflistung von [Workflowaufgaben](task.md)| Rufen Sie eine Auflistung von Workflowaufgaben-Objekt.|
|[Bucket erstellen](../api/bucket_post_buckets.md) | [Bucket](bucket.md)   | Erstellen eines neuen Bucket-Objekts. |
|[Bucket aktualisieren](../api/bucket_update.md) | Keine |Update-Bucket-Objekt. |
|[Bucket löschen](../api/bucket_delete.md) | Keine |Bucket-Objekt zu löschen. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "bucket resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
