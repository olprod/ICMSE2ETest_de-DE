# <a name="sectiongroup-resource-type"></a>SectionGroup Ressourcentyp

Einer Gruppe in einem OneNote-Notizbuch. Abschnittsgruppen können Abschnitte und Abschnittsgruppen.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "parentNotebook",
    "parentSectionGroup",
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.sectiongroup"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "name": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|createdBy|String|Der Benutzer, die im Abschnittsgruppe erstellt. Schreibgeschützt.|
|createdTime|DateTimeOffset|Datum und Uhrzeit der Erstellung die Abschnittsgruppe. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise könnte Uhr UTC auf 1 Jan 2014 wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|id|String|Der eindeutige Bezeichner der Abschnittsgruppe. Schreibgeschützt.|
|lastModifiedBy|String|Der Benutzer, die im Abschnittsgruppe zuletzt geändert. Schreibgeschützt.| 
|ZuletztGeändertUm|DateTimeOffset|Datum und Uhrzeit der letzten die Abschnittsgruppe Änderung. Der Zeitstempel stellt Datum und Uhrzeit Informationen mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 könnte beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|name|String|Der Name der Abschnittsgruppe.|
|sectionGroupsUrl|String|Die URL für die `sectionGroups` Navigationseigenschaft, die alle Abschnittsgruppen in den Abschnittsgruppe zurückgibt. Schreibgeschützt.| 
|sectionsUrl|String|Die URL für die `sections` Navigationseigenschaft, die alle Abschnitte in der Abschnittsgruppe im zurückgibt. Schreibgeschützt.|
|Self|String|Der Endpunkt, in dem Sie die Details zur Abschnittsgruppe im abrufen können. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|parentNotebook|[Notizbuch](notebook.md)|Das Notizbuch, das die im Abschnittsgruppe enthält. Schreibgeschützt.|
|parentSectionGroup|[SectionGroup](sectiongroup.md)|Der Abschnittsgruppe, die im Abschnittsgruppe enthält. Schreibgeschützt.|
|sectionGroups|[SectionGroup](sectiongroup.md) -Auflistung|Die Abschnittsgruppen im Abschnitt. Schreibgeschützt. NULL-Werte zulässt.|
|Sections|[Section](section.md) -Auflistung|Die Abschnitte in der Abschnittsgruppe im. Schreibgeschützt. NULL-Werte zulässt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erhalten Sie im Abschnittsgruppe](../api/sectiongroup_get.md) | [SectionGroup](sectiongroup.md) |Lesen Sie die Eigenschaften und Beziehungen der Abschnittsgruppe.|
|[Erstellen Sie im Abschnittsgruppe](../api/sectiongroup_post_sectiongroups.md) |[SectionGroup](sectiongroup.md)| Erstellen einer Gruppe durch die Veröffentlichung auf der SectionGroups-Auflistung in der angegebenen Abschnittsgruppe.|
|[Liste von Abschnittsgruppen](../api/sectiongroup_list_sectiongroups.md) |[SectionGroup](sectiongroup.md) -Auflistung| Rufen Sie Auflistung von Abschnittsgruppen in der angegebenen Abschnittsgruppe.|
|[Erstellen Sie im Abschnitt](../api/sectiongroup_post_sections.md) |[Abschnitt](section.md)| Erstellen Sie einen Abschnitt durch das Veröffentlichen in der Sections-Auflistung in der angegebenen Abschnittsgruppe aus.|
|[Liste Abschnitten](../api/sectiongroup_list_sections.md) |[Section](section.md) -Auflistung| Rufen Sie eine Auflistung von Abschnitten in der angegebenen Abschnittsgruppe.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sectionGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->