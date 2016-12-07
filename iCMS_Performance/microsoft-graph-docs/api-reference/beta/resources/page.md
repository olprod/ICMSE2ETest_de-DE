# <a name="page-resource-type"></a>page resource type

A page in a OneNote notebook.

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

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
|Inhalt|Stream|The page's HTML content.|
|contentUrl|String|The URL for the page's HTML content.  Read-only.|
|createdByAppId|String|Der eindeutige Bezeichner der Anwendung, die die Seite erstellt hat.|
|createdTime|DateTimeOffset|The date and time when the page was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|id|String|The unique identifier of the page.  Read-only.|
|lastModifiedTime|DateTimeOffset|The date and time when the page was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|Ebene|Int32|Die Einzugsebene des Absatzes.|
|Verknüpfungen|[PageLinks](pagelinks.md)|Links for opening the page. The `oneNoteClientURL` link opens the page in the OneNote native client if it 's installed. The `oneNoteWebUrl` link opens the page in OneNote Online. Read-only.|
|Reihenfolge|Int32|The order of the page within its parent section. Read-only.|
|self|String|Der Endpunkt, an dem Sie Details zu dem Abschnitt abrufen können.|
|title|String|Der Titel der Seite. |

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|parentNotebook|[Notizbuch](notebook.md)|The notebook that contains the page.  Read-only.|
|parentSection|[Section[]](section.md)|The section that contains the page. Read-only.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get page](../api/page_get.md) | [page](page.md) |Read the properties and relationships of the page.|
|[Update page content](../api/page_update.md) | Keine |Der HTML-Inhalt der Seite. |
|[Delete a Toolbox page](../api/page_delete.md) | Keine |Delete the page. |
|[copyToSection](../api/page_copytosection.md)| Keine |Copies the page to a specific section.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "page resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->