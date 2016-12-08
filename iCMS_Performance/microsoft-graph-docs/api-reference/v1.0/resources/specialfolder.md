# <a name="specialfolder-resource-type"></a>SpecialFolder Ressourcentyp

Die **SpecialFolder** Facetten enthält Informationen zu wie ein Ordners über die [spezielle Folders-Auflistung](../api/drive_special.md)zugegriffen werden kann.

Spezialordner einfache Aliase bekannte Ordner in OneDrive ohne die Notwendigkeit der Ordner durch Pfad Nachschlagen (die Lokalisierung erforderlich wäre) für den Zugriff bereitstellen oder verweisen auf den Ordner mit einer ID Ein Ordner mit Sonderfunktion umbenannt oder an eine andere Position innerhalb des Laufwerks verschoben wird, wird diese Syntax weiterhin den Ordner suchen.

Spezialordner werden automatisch beim ersten erstellt, die eine Anwendung zum Schreiben in ein einziges versucht, sofern er nicht bereits vorhanden. Wenn ein Benutzer eine löscht, wird es neu erstellt, wenn nicht neu geschrieben.

**Hinweis:** Wenn Ihre app nur **Files.Read** Bereich angefordert hat und fordert einen speziellen Ordner, der nicht vorhanden ist, gibt die Antwort wird ein `403 Forbidden` Fehler.

## <a name="properties"></a>Eigenschaften
| Eigenschaft  | Typ   | Beschreibung                                                            |
|:----------|:-------|:-----------------------------------------------------------------------|
| name      | string | Der eindeutige Bezeichner für dieses Element in der `/drive/special` Auflistung |

## <a name="json-representation"></a>JSON-Darstellung

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.specialFolder"
}-->
```json
{
  "name": "string"
}

```

## <a name="special-folders"></a>Spezialordner

Hier sind die Ordner mit Sonderfunktion in OneDrive persönlich und OneDrive für Unternehmen verfügbar.

| Name        | Ordner-id    | Beschreibung                                                              |
|:------------|:-------------|:-------------------------------------------------------------------------|
| App-Stamm    | `approot`    | Persönliche Ordner der Anwendung. In der Regel in`/Apps/{Application Name}` |
| Kamera Blogroll (engl.) | `cameraroll` | Die Kamera ein Rollback Sicherungsordner. In OneDrive für Unternehmen nicht verfügbar.   |
| Documents   | `documents`  | Der Ordner Dokumente.                                                    |
| Musik       | `music`      | Der Ordner Musik. In OneDrive für Unternehmen nicht verfügbar.                |
| Fotos      | `photos`     | Der Ordner Fotos.                                                       |


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "specialFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
