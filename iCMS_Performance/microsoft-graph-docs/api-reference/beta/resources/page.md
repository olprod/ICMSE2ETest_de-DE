# <a name="page-resource-type"></a>Seite Ressourcentyp

Eine Seite in einem OneNote-Notizbuch.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "parentNotebook",
    "parentSection"
  ],
  "@odata.type": "microsoft.graph.page"
}-->

```json
{
  "content": "stream",
  "contentUrl": "string",
  "createdByAppId": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedTime": "String (timestamp)",
  "level": 1024,
  "links": {"@odata.type": "microsoft.graph.pageLinks"},
  "order": 1024,
  "self": "string",
  "title": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Inhalt|Stream|Die Seite HTML-Inhalt.|
|contentUrl|String|Die URL für die Seite HTML-Inhalt.  Schreibgeschützt.|
|createdByAppId|String|Der eindeutige Bezeichner der Anwendung, die die Seite erstellt hat. Schreibgeschützt.|
|createdTime|DateTimeOffset|Datum und Uhrzeit der Erstellung die Seite. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Um Mitternacht UTC 1 Jan 2014 würde beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|id|String|Der eindeutige Bezeichner der Seite.  Schreibgeschützt.|
|ZuletztGeändertUm|DateTimeOffset|Datum und Uhrzeit der letzten die Seite Änderung. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Um Mitternacht UTC 1 Jan 2014 würde beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|Ebene|Int32|Die Einzugsebene auf der Seite. Schreibgeschützt.|
|Verknüpfungen|[PageLinks](pagelinks.md)|Links zum Öffnen der Seite. Die `oneNoteClientURL` Link wird die Seite im OneNote-native Client geöffnet, wenn es installiert ist. Die `oneNoteWebUrl` Link wird die Seite in OneNote Online. Schreibgeschützt.|
|Reihenfolge|Int32|Die Reihenfolge der Seiten im übergeordneten Abschnitt. Schreibgeschützt.|
|Self|String|Der Endpunkt, in dem Sie Details zu der Seite abrufen können. Schreibgeschützt.|
|title|String|Der Titel der Seite. |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|parentNotebook|[Notizbuch](notebook.md)|Das Notizbuch, das die Seite enthält.  Schreibgeschützt.|
|parentSection|[Abschnitt](section.md)|Der Abschnitt, der die Seite enthält. Schreibgeschützt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erste Seite](../api/page_get.md) | [Seite](page.md) |Lesen Sie die Eigenschaften und Beziehungen der Seite.|
|[Aktualisieren von Seiteninhalten](../api/page_update.md) | Keine |Aktualisieren Sie die HTML-Inhalte auf der Seite. |
|[Seite löschen](../api/page_delete.md) | Keine |Löscht das Zeichenblatt. |
|[copyToSection](../api/page_copytosection.md)| Keine |Kopiert die Seite zu einem bestimmten Abschnitt.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "page resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->