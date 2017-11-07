# <a name="section-resource-type"></a>Abschnitt Ressourcentyp

Ein Abschnitt in einem OneNote-Notizbuch. Abschnitte können Seiten enthalten.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

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
|createdBy|String|Der Benutzer, die der Abschnitt erstellt. Schreibgeschützt.|
|createdTime|DateTimeOffset|Datum und Uhrzeit der Erstellung der Abschnitt. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Um Mitternacht UTC 1 Jan 2014 würde beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|id|String|Der eindeutige Bezeichner des Abschnitts.  Schreibgeschützt.|
|isDefault|Boolean|Gibt an, ob dies Abschnitt "Default" des Benutzers ist. Schreibgeschützt.|
|lastModifiedBy|String|Der Benutzer, die im Abschnitt der letzten Änderung. Schreibgeschützt.|
|ZuletztGeändertUm|DateTimeOffset|Datum und Uhrzeit der letzten im Abschnitt Änderung. Der Zeitstempel stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Um Mitternacht UTC 1 Jan 2014 würde beispielsweise wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt.|
|name|String|Der Name des Abschnitts. |
|pagesUrl|String|Die `pages` Endpunkt, in dem Sie Details für alle Seiten im Abschnitt abrufen können. Schreibgeschützt.|
|Self|String|Der Endpunkt, in dem Sie Details zum Abschnitt abrufen können. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Seiten|[Seite](page.md) -Auflistung|Die Auflistung der Seiten im Abschnitt.  Schreibgeschützt. NULL-Werte zulässt.|
|parentNotebook|[Notizbuch](notebook.md)|Das Notizbuch, das den Abschnitt enthält.  Schreibgeschützt.|
|parentSectionGroup|[SectionGroup](sectiongroup.md)|Der Abschnittsgruppe, die den Abschnitt enthält.  Schreibgeschützt.|

## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Get-Abschnitt](../api/section_get.md) | [Abschnitt](section.md) |Lesen Sie die Eigenschaften und Beziehungen des Abschnitts.|
|[Seite "erstellen"](../api/section_post_pages.md) |[Seite](page.md)| Erstellen Sie eine Seite durch das Veröffentlichen in der Pages-Auflistung im angegebenen Abschnitt.|
|[Listenseiten](../api/section_list_pages.md) |[Seite](page.md) -Auflistung| Rufen Sie eine Auflistung von Seiten im angegebenen Abschnitt.|
|[copyToNotebook](../api/section_copytonotebook.md)|Keine|Kopieren Sie im Abschnitt in einem bestimmten Notizbuch.|
|[copyToSectionGroup](../api/section_copytosectiongroup.md)|Keine|Kopieren Sie den Abschnitt zu einer bestimmten Gruppe.|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "section resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
