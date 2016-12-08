# <a name="directorysetting-resource-type"></a>Verzeichnisberechtigungen Ressourcentyp

Directory-Einstellungen können basierend auf der verfügbaren [DirectorySettingTemplates](directorySettingTemplate.md)erstellt und die voreingestellte Standardeinstellung geändert werden. Diese Einstellungen können Entität oder ein Feature Verhaltensweisen, sowohl auf einem Mandanten-Ebene oder auf eine bestimmte Entitätsebene steuern. Wenn dieselbe Einstellung auf beide Mandanten geltende und bestimmte Entitätsebene definiert ist, die Einstellung der bestimmte Entität kann von der Einstellung für die gesamte Mandanten zielorientierten.  Beispielsweise die Einstellung für die gesamte Mandanten kann Gäste eingeladen werden, indem vorhandene Mitglieder von Gruppen, jedoch Einstellung für eine bestimmte Gruppe möglicherweise abmelden und nicht zulassen Gäste von Mitgliedern der Gruppe eingeladen werden sollen. Derzeit definierten Systemeinstellungen sind nur Office Gruppen Verhalten steuern.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erstellen Sie die Einstellung](../api/directorysetting_post_settings.md) | [Verzeichnisberechtigungen](directorysetting.md) |Erstellen einer Einstellungsobjekt basierend auf einer DirectorySettingTemplate. Die POST-Anforderung muss EinstellenWerte für alle in der Vorlage definierten Einstellungen angeben.|
|[Abrufen der Einstellung](../api/directorysetting_get.md) | [Verzeichnisberechtigungen](directorysetting.md) |Lesen Sie die Eigenschaften eines bestimmten Einstellung-Objekts.|
|[Einstellungen für die Liste](../api/directorysetting_list.md) | [Verzeichnisberechtigungen](directorysetting.md) -Auflistung |Listeneigenschaften aller Einstellung-Objekte.|
|[Update-Einstellung](../api/directorysetting_update.md) | [Verzeichnisberechtigungen](directorysetting.md)  |Aktualisieren eines Einstellung-Objekts. Nur EinstellenWerte können in einer Aktualisierung nicht geändert werden.|
|[Löschen Sie die Einstellung](../api/directorysetting_delete.md) | Keine |Löscht ein Einstellungsobjekt. |

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|displayName|string|Anzeigename des diese Gruppe von Einstellungen, die aus der zugeordneten Vorlage stammt. Schreibgeschützt.|
|id|string| Eindeutiger Bezeichner für diese Einstellungen. Schreibgeschützt.|
|templateId|string| Eindeutiger Bezeichner für die Vorlage verwendet, um diese Gruppe von Einstellungen zu erstellen. Schreibgeschützt.|
|values|[SettingValue](settingvalue.md) -Auflistung| Eine Auflistung von Name-Wert-Paaren. Muss enthalten, und legen Sie alle Einstellungen in der Vorlage definiert.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.directorySetting"
}-->

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "templateId": "string",
  "values": [{"@odata.type": "microsoft.graph.settingValue"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directorySetting resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->