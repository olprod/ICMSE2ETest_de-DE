# <a name="notebook-resource-type"></a>Notebook-Ressourcentyp

Ein OneNote-Notizbuch.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

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
|createdBy|String|Der Benutzer, die das Notizbuch erstellt. Schreibgeschützt.|
|createdTime|DateTimeOffset|Datum und Uhrzeit der Erstellung des Notizbuchs. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise könnte Uhr UTC auf 1 Jan 2014 wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|id|String|Der eindeutige Bezeichner des Notizbuchs. Schreibgeschützt.|
|isDefault|Boolean|Gibt an, ob dies die standardmäßige Notizbuch des Benutzers ist. Schreibgeschützt.|
|isShared|Boolean|Gibt an, ob das Notizbuch gemeinsam genutzt wird. Wenn true, können von anderen Personen außer dem Besitzer der Inhalt des Notizbuchs angezeigt werden. Schreibgeschützt.|
|lastModifiedBy|String|Der Benutzer, der letzten des Notizbuchs Änderung. Schreibgeschützt.|
|ZuletztGeändertUm|DateTimeOffset|Datum und Uhrzeit der letzten des Notizbuchs Änderung. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise könnte Uhr UTC auf 1 Jan 2014 wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|Verknüpfungen|[NotebookLinks](notebooklinks.md)|Links zum Öffnen des Notizbuchs. Die `oneNoteClientURL` Link wird das Notizbuch in den OneNote-native Client geöffnet, wenn es installiert ist. Die `oneNoteWebURL` Link wird das Notizbuch in OneNote Online geöffnet.|
|name|String|Der Name des Notizbuchs.|
|sectionGroupsUrl|String|Die URL für die `sectionGroups` Navigationseigenschaft, die alle Abschnittsgruppen im Notizbuch zurückgibt. Schreibgeschützt.|
|sectionsUrl|String|Die URL für die `sections` Navigationseigenschaft, die alle Abschnitte im Notizbuch zurückgibt. Schreibgeschützt.|
|Self|String|Der Endpunkt, in dem Sie Details über das Notizbuch abrufen können. Schreibgeschützt.|
|userRole|String|Mögliche Werte sind: `Owner`, `Contributor`, `Reader`, `None`. Besitzer stellt Zugriff auf Benutzerebene Besitzer in das Notizbuch. Mitwirkender stellt Lese-/Schreibzugriff auf das Notizbuch. Leser stellt schreibgeschützten Zugriff auf das Notizbuch. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|sectionGroups|[SectionGroup](sectiongroup.md) -Auflistung|Die Abschnittsgruppen in das Notizbuch. Schreibgeschützt. NULL-Werte zulässt.|
|Sections|[Section](section.md) -Auflistung|In den Abschnitten im Notizbuch. Schreibgeschützt. NULL-Werte zulässt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen des Notizbuchs](../api/notebook_get.md) | [Notizbuch](notebook.md) |Lesen Sie die Eigenschaften und Beziehungen des Notizbuchs.|
|[Erstellen Sie im Abschnittsgruppe](../api/notebook_post_sectiongroups.md) |[SectionGroup](sectiongroup.md)| Erstellen einer Gruppe durch die Veröffentlichung auf der SectionGroups-Auflistung in das angegebene Notizbuch.|
|[Liste von Abschnittsgruppen](../api/notebook_list_sectiongroups.md) |[SectionGroup](sectiongroup.md) -Auflistung| Rufen Sie eine Auflistung von Abschnittsgruppen in das angegebene Notizbuch.|
|[Erstellen Sie im Abschnitt](../api/notebook_post_sections.md) |[Abschnitt](section.md)| Erstellen Sie einen Abschnitt durch das Veröffentlichen in der Sections-Auflistung im angegebenen Notizbuch.|
|[Liste Abschnitten](../api/notebook_list_sections.md) |[Section](section.md) -Auflistung| Rufen Sie eine Auflistung von Abschnitten im angegebenen Notizbuch.|
|[copyNotebook](../api/notebook_copynotebook.md)| Keine | Kopiert ein Notizbuch.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notebook resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
