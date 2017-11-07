# <a name="directoryroletemplate-resource-type"></a>Ressourcentyp directoryRoleTemplate

Stellt eine Verzeichnis Rollenvorlage dar. Vorlage Rolle Directory gibt die Eigenschaftswerte einer Rolle Verzeichnis ([DirectoryRole](directoryrole.md)). Es ist eine zugehörige Verzeichnis Rolle Template-Objekt für jede der Directory Rollen, die in einem Mandanten aktiviert werden können. Um eine Rolle Directory lesen oder deren Member aktualisieren möchten, müssen sie zuerst im Mandanten aktiviert werden. Nur die Administratoren im Unternehmen Directory Rolle ist standardmäßig aktiviert. Andere Rollen verfügbaren Verzeichnis zu aktivieren, die Sie Senden einer POST-Anforderung an den `/directoryRoles` Endpunkt mit der ID des Directory Rolle die Rolle Directory auf dem basiert angegebenen Vorlage im **RoleTemplateId** -Parameter der Anforderung. Nach dem erfolgreichen Abschluss dieser Anforderung können Sie dann zum Lesen und Zuweisen von Mitgliedern zur Rolle Directory starten. **Hinweis**: Directory Rollenvorlage ist für die Rolle der Benutzer Directory verfügbar gemacht werden. Die Rolle der Benutzer Verzeichnis ist implizit und ist für Directory-Clients nicht sichtbar. Jeder Benutzer in den Mandanten wird von der Infrastruktur dieser Rolle zugewiesen. Die Rolle ist bereits aktiviert. Verwenden Sie diese Vorlage nicht.


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von directoryRoleTemplate](../api/directoryroletemplate_get.md) | [directoryRoleTemplate](directoryroletemplate.md) |Lesen Sie Eigenschaften und Beziehungen des DirectoryRoleTemplate-Objekts.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|description|String|Die Beschreibung für die Rolle Directory festgelegt. Schreibgeschützt.|
|displayName|String|Der Anzeigename für die Rolle Directory festgelegt. Schreibgeschützt. |
|id|String|Der eindeutige Bezeichner für die Vorlage. Geerbt von [DirectoryObject](directoryobject.md). Sie können für die **RoleTemplateId** -Eigenschaft in der POST-Anforderung Aktivieren einer [DirectoryRole](directoryrole.md) in einem Mandanten die **Id** der Vorlage Rolle Directory festlegen. Wichtige, nicht NULL-Werte zulässt. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
Keine



## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryRoleTemplate"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryRoleTemplate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
