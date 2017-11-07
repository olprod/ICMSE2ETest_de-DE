# <a name="audio-resource-type"></a>Audio Ressourcentyp

Die Ressource **Audio** gruppiert Daten für ein Element im Zusammenhang mit Audio in eine einzelne Struktur.

## <a name="properties"></a>Eigenschaften

| Eigenschaft          | Typ    | Beschreibung                                                          |
|:------------------|:--------|:---------------------------------------------------------------------|
| Album             | string  | Der Titel für das Album für diese Audiodatei.                          |
| albumArtist       | string  | Mit dem Namen auf das Album für die Audiodatei der Künstlers auswählen.                    |
| Künstlers auswählen            | string  | Ausführen der Künstlers auswählen für die Audiodatei.                            |
| Bitrate           | string  | Bitrate in Kbit/s ausgedrückt.                                           |
| Komponisten         | string  | Der Name der Komponist der Audiodatei.                          |
| Copyright         | string  | Copyright-Informationen für die Audiodatei.                            |
| CD              | number  | Die Anzahl der Datenträger, dem diese Audiodatei stammt.                    |
| discCount         | number  | Die Gesamtzahl der Datenträger in dieses Album hoch.                             |
| duration          | number  | Dauer der Audiodatei in Millisekunden ausgedrückt                |
| Genre             | string  | Das Genre diese Audiodatei.                                        |
| hasDrm            | boolean | Gibt an, ob die Datei mit Verwaltung digitaler Rechte geschützt ist.   |
| isVariableBitrate | boolean | Gibt an, ob die Datei mit einer Variablen Bitrate codiert wird.            |
| title             | string  | Der Titel der Audiodatei.                                         |
| Nachverfolgen             | number  | Die Anzahl der den Titel auf der ursprünglichen CD für diese Audiodatei.    |
| trackCount        | number  | Die Gesamtanzahl der Spuren auf die ursprüngliche CD für diese Audiodatei. |
| Jahr              | number  | Das Jahr, das die Audiodatei aufgezeichnet wurde.                                |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.audio"
}-->
```json
{
  "album": "string",
  "albumArtist": "string",
  "artist": "string",
  "bitrate": 1024,
  "composers": "string",
  "copyright": "string",
  "disc": 1024,
  "discCount": 1024,
  "duration": 1024,
  "genre": "string",
  "hasDrm": true,
  "isVariableBitrate": true,
  "title": "string",
  "track": 1024,
  "trackCount": 1024,
  "year": 1024
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "audio resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->