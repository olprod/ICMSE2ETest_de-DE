# <a name="create-plan"></a>Erstellen eines Plans

Verwenden Sie diese API, um einen neuen Plan zu erstellen. 

Beachten Sie, dass Sie eine Gruppe erstellt haben und ein Mitglied werden, bevor Sie der Gruppe Besitzer des Plans machen müssen. Lesen der [Übersicht](../resources/tasks_overview.md) zum besseren Verständnis der Beziehung zwischen Gruppen, Plan und Aufgabe.


## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /plans

```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Wert sollte auf "Bearer (Zugriffstoken)" festgelegt werden |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Plans](../resources/plan.md) -Objekts.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `201, Created` Antwortobjekt Code und [Plan](../resources/plan.md) im Antworttext.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_plan_from_plans"
}-->
```http
POST https://graph.microsoft.com/beta/plans
Content-type: application/json
Content-length: 88

{
  "owner": "owner-value",
  "title": "title-value"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung des [Plans](../resources/plan.md) -Objekts.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plan"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 108

{
  "createdBy": "createdBy-value",
  "owner": "owner-value",
  "title": "title-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create plan",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->