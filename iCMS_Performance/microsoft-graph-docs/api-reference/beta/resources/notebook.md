# <a name="notebook-resource-type"></a>notebook resource type

A OneNote notebook.

## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.notebook"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "isShared": true,
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "links": {"@odata.type": "microsoft.graph.notebookLinks"},
  "name": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string",
  "userRole": "String"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|createdBy|String|Der Benutzer, der das Notizbuch erstellt hat.|
|createdTime|DateTimeOffset|The date and time when the notebook was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|id|String|Der eindeutige Bezeichner des Notizbuchs.|
|isDefault|Boolean|Indicates whether this is the user's default notebook. Read-only.|
|isShared|Boolean|Gibt an, ob das Notizbuch freigegeben ist. Wenn der Wert „true“ lautet, kann der Inhalt des Notizbuch auch von anderen Personen als dem Besitzer angezeigt werden.|
|lastModifiedBy|String|Der Benutzer, der das Notizbuch zuletzt geändert hat|
|lastModifiedTime|DateTimeOffset|The date and time when the notebook was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `'2014-01-01T00:00:00Z'`. Read-only.|
|Verknüpfungen|[NotebookLinks](notebooklinks.md)|Links for opening the notebook. The `oneNoteClientURL` link opens the notebook in the OneNote native client if it's installed. The `oneNoteWebURL` link opens the notebook in OneNote Online.|
|name|String|Der Name des Notizbuchs.|
|sectionGroupsUrl|String|The URL for the `sectionGroups` navigation property, which returns all the section groups in the notebook. Read-only.|
|sectionsUrl|String|The URL for the `sections` navigation property, which returns all the sections in the notebook. Read-only.|
|self|String|Der Endpunkt, an dem Sie Details zu dem Notizbuch abrufen können.|
|userRole|String|Possible values are: `Owner`, `Contributor`, `Reader`, `None`. Owner represents owner-level access to the notebook. Contributor represents read/write access to the notebook. Reader represents read-only access to the notebook. Read-only.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|/sectiongroups|SectionGroup-Auflistung|The section groups in the notebook. Read-only. Nullable.|
|Sections|[Section](section.md) collection|The sections in the notebook. Read-only. Nullable.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get notebook](../api/notebook_get.md) | [Notizbuch](notebook.md) |Read the properties and relationships of the notebook.|
|[Create section group](../api/notebook_post_sectiongroups.md) |[SectionGroup-Objekt](sectiongroup.md)| Create a section group by posting to the sectionGroups collection in the specified notebook.|
|[List section groups](../api/notebook_list_sectiongroups.md) |SectionGroup-Auflistung| Get a collection of section groups in the specified notebook.|
|[Create section](../api/notebook_post_sections.md) |[Section[]](section.md)| Create a section by posting to the sections collection in the specified notebook.|
|[List sections](../api/notebook_list_sections.md) |[Section](section.md) collection| Get a collection of sections in the specified notebook.|
|[copyNotebook](../api/notebook_copynotebook.md)| Keine | Copies a notebook.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notebook resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
