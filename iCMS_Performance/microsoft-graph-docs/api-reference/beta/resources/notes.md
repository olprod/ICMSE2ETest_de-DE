# <a name="notes-resource-type"></a>Notes-Ressourcentyp

Der Einstiegspunkt für OneNote-Ressourcen.

Alle Anrufe an die OneNote-Dienst über die Microsoft Graph-API verwenden dieses dienststamm-URL:

```
https://graph.microsoft.com/<version>/<location>/notes/ 
```

OneNote-Unterstützung ist in der Vorschau, damit immer die Version ist `beta`. 

Nur Benutzer und Gruppe Notizbücher auf Office 365 werden unterstützt. Zugreifen auf die Consumer-Notizbüchern in OneDrive oder SharePoint-Website gehostet Notebooks wird derzeit nicht unterstützt. 

**Benutzer-Notizbüchern** Verwenden Sie den Zugriff auf persönliche-Notizbüchern in OneDrive für Unternehmen eine der folgenden URLs:

```
https://graph.microsoft.com/beta/me/notes/<notebooks | sections | sectionGroups | pages> 
https://graph.microsoft.com/beta/users/<userPrincipalName>/notes/<notebooks | sections | sectionGroups | pages> 
https://graph.microsoft.com/beta/users/<id>/notes/<notebooks | sections | sectionGroups | pages> 
```

**Gruppe-Notizbüchern** Verwenden Sie zum Notizbücher zugreifen, die von einer Gruppe gehören, dienststamm-die folgenden URL:

```
https://graph.microsoft.com/beta/groups/<id>/notes/<notebooks | sections | sectionGroups | pages> 
```

Die folgenden berechtigungsbereiche bieten Zugriff auf OneNote-Notizbücher. Auswählen von berechtigungsbereiche, richtet auf den Speicherort der Ihnen vorgesehenen Notizbücher und Funktionalität Ihrer app. 

**Bereiche für persönliche-Notizbüchern in OneDrive für Unternehmen, die der aktuelle Benutzer besitzt**

| Bereich (Enterprise) | Berechtigung in Azure-portal | Beschreibung |
|:-------|:------|:------|
| Notes.Create | Erstellen von Seiten in Benutzer-Notizbüchern (Preview) | Die Titel der Abschnitte und Notizbücher können angezeigt werden. Erstellen Sie neue Seiten an einem Standort. Nicht anzeigen oder bearbeiten Sie vorhandene Seiten. |
| Notes.ReadWrite.CreatedByApp | Begrenzte Notizbuch Zugriff (Preview) | Der Titel der Abschnitte und Notizbücher können angezeigt werden. Erstellen neuer Seiten; Anzeigen und Ändern von Seiten von der app erstellt wurden. Nicht anzeigen oder Ändern von Seiten, die von anderen apps oder kennwortgeschützte Abschnitte erstellt wurden. |
| Notes.Read | Lesen Sie die Benutzer-Notizbüchern (Preview) | Können den Inhalt Ihrer Notizbücher und Abschnitte anzeigen. Neue Seiten kann nicht erstellt werden; Bearbeiten Sie vorhandene Seiten. Zugriff auf kennwortgeschützte Abschnitte. |
| Notes.ReadWrite | Lesen und Schreiben von Benutzer-Notizbüchern (Preview) | Der Titel der Abschnitte und Notizbücher können angezeigt werden. Zeigen Sie an und ändern Sie alle Seiten; Erstellen Sie neuer Seiten. Kennwortgeschützte Abschnitte kann nicht zugegriffen werden. |

**Bereiche für persönliche Notebooks, die von anderen Benutzern und Gruppe Notebooks, die der aktuelle Benutzer zugreifen kann gemeinsam genutzt werden**

| Bereich (Enterprise) | Berechtigung in Azure portal | Beschreibung |
|:-------|:------|:------|
| Notes.Read.All | Lesen Sie alle Notizbücher an, die der Benutzer zugreifen kann (Preview) | Kann die Notizbüchern und Abschnitten in allen Notizbüchern anzuzeigen, denen der angemeldeten Benutzer zugreifen kann. Neue Seiten kann nicht erstellt werden; Ändern Sie vorhandene Seiten; Zugriff auf kennwortgeschützte Abschnitte. |
| Notes.ReadWrite.All | Lesen und Schreiben von Notizbüchern (Preview) der Benutzer zugreifen zu können | Die Titel der Abschnitte und Notizbücher können angezeigt werden. Anzeigen und Ändern von allen Seiten; Erstellen Sie neuer Seiten in allen Notebooks, denen der angemeldeten Benutzer zugreifen kann. Kennwortgeschützte Abschnitte kann nicht zugegriffen werden. |

**Hinweis:** Zugreifen auf SharePoint-Website Notizbücher über die Diagramm-API wird derzeit nicht unterstützt.

**Bereiche für Gruppen**

Wenn Sie Gruppe Notizbücher zugreifen, benötigen Sie ein Gruppen-Berechtigungsbereich abzurufenden die Kennung. Derzeit ist diese Berechtigungen Administratorrechte erforderlich.

| Bereich (Enterprise) | Berechtigung in Azure-portal | Beschreibung |
|:-------|:------|:------|
| Group.Read.All | Lesen Sie alle Gruppen | Kann alle Gruppeneigenschaften und Mitgliedschaften gelesen werden. Lesen Sie einen Gruppenkalender und Unterhaltungen auf öffentliche Gruppen und Gruppen, denen der angemeldeten Benutzer Mitglied ist. |
| Group.ReadWrite.All | Lesen Sie und Schreiben Sie aller Gruppen | Erstellen von Gruppen im Namen des angemeldeten Benutzers, und Lesen Sie alle Gruppeneigenschaften und Mitgliedschaften können; Update Gruppeneigenschaften und Mitgliedschaften für Gruppen besitzt die angemeldeten Benutzers; Lesen und Schreiben für einen Gruppenkalender und Unterhaltungen auf öffentliche Gruppen und Gruppen, denen der angemeldeten Benutzer Mitglied ist. |

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "notebooks",
    "pages",
    "resources",
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.notes"
}-->

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Notizbücher|[Notebook](notebook.md) -Auflistung|Die Auflistung der OneNote-Notizbücher, die Besitzer der Benutzer oder die Gruppe. Schreibgeschützt. NULL-Werte zulässt.|
|Vorgänge|[Vorgang](notesoperation.md) -Auflistung |Der Status der OneNote-Vorgänge. Abrufen einer Operations-Auflistung wird nicht unterstützt, aber Sie können den Status von Vorgängen mit langer abrufen, wenn die `Operation-Location` Header in der Antwort zurückgegeben wird. Schreibgeschützt. NULL-Werte zulässt.|
|Seiten|[Seite](page.md) -Auflistung|Die Seiten in allen OneNote-Notizbücher, die Besitzer der Benutzer oder die Gruppe.  Schreibgeschützt. NULL-Werte zulässt.|
|Ressourcen|[Resource](resource.md) -Auflistung |Das Bild und anderen Ressourcen in OneNote-Seiten. Abrufen einer Resources-Auflistung wird nicht unterstützt, aber Sie können [den binären Inhalt einer bestimmten Ressource erhalten möchten](resource.md). Schreibgeschützt. NULL-Werte zulässt.|
|sectionGroups|[SectionGroup](sectiongroup.md) -Auflistung|Die Abschnittsgruppen in allen OneNote-Notizbücher, die Besitzer der Benutzer oder die Gruppe.  Schreibgeschützt. NULL-Werte zulässt.|
|Sections|[Section](section.md) -Auflistung|In den Abschnitten in allen OneNote-Notizbücher, die Besitzer der Benutzer oder die Gruppe.  Schreibgeschützt. NULL-Werte zulässt.|


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Notizbuch erstellen](../api/notes_post_notebooks.md) |[Notizbuch](notebook.md)| Erstellen Sie ein Notizbuch, durch die Veröffentlichung auf Notizbücher-Auflistung.|
|[Liste-Notizbüchern](../api/notes_list_notebooks.md) |[Notebook](notebook.md) -Auflistung| Möchten Sie eine Auflistung von Notizbüchern erhalten.|
|[Seite "erstellen"](../api/notes_post_pages.md) |[Seite](page.md)| Erstellt eine Seite durch das Veröffentlichen in der Pages-Auflistung.|
|[Listenseiten](../api/notes_list_pages.md) |[Seite](page.md) -Auflistung| Rufen Sie eine Auflistung von Seiten.|
|[Liste von Abschnittsgruppen](../api/notes_list_sectiongroups.md) |[SectionGroup](sectiongroup.md) -Auflistung| Rufen Sie eine Auflistung von Abschnittsgruppen.|
|[Liste Abschnitten](../api/notes_list_sections.md) |[Section](section.md) -Auflistung| Möchten Sie eine Auflistung von Abschnitten erhalten.|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notes resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
