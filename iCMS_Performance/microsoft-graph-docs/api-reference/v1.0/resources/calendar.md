# <a name="calendar-resource-type"></a>Ressourcentyp Kalender

Ein Kalender ist ein Container für Ereignisse.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Liste Kalender](../api/user_list_calendars.md)|[Kalender](calendar.md) -Auflistung|Abgerufen Sie Kalender des Benutzers oder der Kalender in die Standardvorlage oder die Gruppe andere bestimmten Kalender werden.|
|[Kalender erstellen](../api/user_post_calendars.md) |[Kalender](calendar.md)| Erstellen Sie einen neuen Kalender in die Standard-Kalender oder Gruppe angegebenen Kalender.|
|[Abrufen von Kalender](../api/calendar_get.md) | [Kalender](calendar.md) |Eigenschaften lesen und Beziehungen des Calendar-Objekt.|
|[Update](../api/calendar_update.md) | [Kalender](calendar.md)  |Calendar-Objekt zu aktualisieren. |
|[Löschen](../api/calendar_delete.md) | Keine |Calendar-Objekt zu löschen. |
|[Liste calendarView](../api/calendar_list_calendarview.md) |[Ereignissammlung](event.md)| Der vorkommen, Ausnahmen und einzelne Instanzen von Ereignissen in einer Kalenderansicht definiert durch ein Zeitbereich, aus dem primären Kalender des Benutzers abrufen `(../me/calendarview)` oder aus einem angegebenen Kalender.|
|[List-Ereignisse](../api/calendar_list_events.md) |[Ereignis](event.md) -Auflistung| Abrufen einer Liste von Ereignissen in einem Kalender.  Die Liste enthält Einzelinstanz Besprechungen und Series-Master.|
|[Ereignis erstellen](../api/calendar_post_events.md) |[Ereignis](event.md)| Erstellen Sie ein neues Ereignis in die standardmäßigen oder den angegebenen Kalender.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|name|String|Der Kalendername.|
|changeKey|String|Gibt die Version des Calendar-Objekts. Jedes Mal, wenn der Kalender geändert wird, ändert ChangeKey sowie. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen. Schreibgeschützt.|
|color|String|Gibt die Farbdesigns, um den Kalender von anderen Kalender in einer Benutzeroberfläche zu unterscheiden. Die Eigenschaftswerte werden: Hellblau = 0, LightGreen = 1, LightOrange = 2, LightGray = 3, LightYellow = 4, LightTeal = 5, LightPink = 6, LightBrown = 7 LightRed = 8, MaxColor = 9, Auto =-1|
|id|String|Eindeutiger Bezeichner der Gruppe. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|calendarView|[Ereignis](event.md) -Auflistung|Die Kalenderansicht für den Kalender. Navigationseigenschaft. Schreibgeschützt.|
|Ereignisse|[Ereignis](event.md) -Auflistung|Die Ereignisse im Kalender. Navigationseigenschaft. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "calendarView",
    "events"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.calendar"
}-->

```json
{
  "changeKey": "string",
  "color": "String",
  "id": "string (identifier)",
  "name": "string"
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "calendar resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
