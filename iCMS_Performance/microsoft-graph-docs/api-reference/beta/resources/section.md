# <a name="section-resource-type"></a>section resource type

A section in a OneNote notebook. Sections can contain pages.

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "pages",
    "parentNotebook",
    "parentSectionGroup"
  ],
  "@odata.type": "microsoft.graph.section"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "name": "string",
  "pagesUrl": "string",
  "self": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|createdBy|String|Der Benutzer, der den Abschnitt erstellt hat.|
|createdTime|DateTimeOffset|The date and time when the section was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|id|String|The unique identifier of the section.  Read-only.|
|isDefault|Boolean|Gibt an, ob das der Standardabschnitt des Benutzers ist.|
|lastModifiedBy|String|Der Benutzer, der den Abschnitt zuletzt geändert hat|
|lastModifiedTime|DateTimeOffset|The date and time when the section was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|name|String|Der Name des Abschnitts. |
|pagesUrl|String|Der /pages-Endpunkt, von dem Sie Details für alle Seiten im Abschnitt abrufen können.|
|self|String|Der Endpunkt, an dem Sie Details zu dem Abschnitt abrufen können.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Seiten|[Page](page.md) collection|The collection of pages in the section.  Read-only. Nullable.|
|parentNotebook|[Notizbuch](notebook.md)|The notebook that contains the section.  Read-only.|
|parentSectionGroup|[SectionGroup-Objekt](sectiongroup.md)|The section group that contains the section.  Read-only.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get section](../api/section_get.md) | [Section[]](section.md) |Read the properties and relationships of the section.|
|[Erstellen eines Seitenlayouts](../api/section_post_pages.md) |[page](page.md)| Create a page by posting to the pages collection in the specified section.|
|[List pages](../api/section_list_pages.md) |[Page](page.md) collection| Get a collection of pages in the specified section.|
|[copyToNotebook](../api/section_copytonotebook.md)|Keine|Copy the section to a specific notebook.|
|[copyToSectionGroup](../api/section_copytosectiongroup.md)|Keine|Copy the section to a specific section group.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "section resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
