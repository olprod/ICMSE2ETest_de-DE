# <a name="directorysettingtemplate-resource-type"></a>Ressourcentyp directorySettingTemplate

Verzeichnis Einstellung Vorlagen darstellen systemdefinierte Einstellungen für den Mandanten verfügbar. [Directory-Einstellungen](directorysetting.md) können anhand der verfügbaren DirectorySettingTemplates und Werte geändert voreingestellten Standardwerte von erstellt werden. Vorlagen für Verzeichnis festlegen können nicht erstellt, aktualisiert oder gelöscht werden. Diese Einstellungen können Mandanten geltende Einstellungen darstellen, oder bestimmte Entität Einstellungen können darstellen.  Derzeit nur verfügbaren Vorlagen gelten für Office-Gruppen und zählen Einstellungen wie gibt an, ob Benutzer Gruppen erstellen oder Gäste außerhalb der Organisation, die Mitglied einer Gruppe werden einladen können.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von directorySettingTemplate](../api/directorysettingtemplate_get.md) | [directorySettingTemplate](directorysettingtemplate.md) |Lesen Sie die bestimmten Eigenschaften des eines der Objekte DirectorySettingTemplate System definiert.|
|[Liste directorySettingTemplate](../api/directorysettingtemplate_list.md) | [Auflistung von directorySettingTemplate](directorysettingtemplate.md) |Listen Sie aller vom System definierten DirectorySettingTemplate Objekte auf.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|description|string|Beschreibung der Vorlage. Schreibgeschützt.|
|displayName|string|Anzeigename der Vorlage. Schreibgeschützt. |
|id|string| Eindeutiger Bezeichner für die Vorlage. Schreibgeschützt.|
|values|[SettingTemplateValue](settingtemplatevalue.md) -Auflistung| Auflistung von SettingTemplateValues, die den Satz von verfügbaren Einstellungen, Standardeinstellungen und Typen, die diese Vorlage bilden auflisten.  Schreibgeschützt. |

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.directorySettingTemplate"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "values": [{"@odata.type": "microsoft.graph.settingTemplateValue"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directorySettingTemplate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->