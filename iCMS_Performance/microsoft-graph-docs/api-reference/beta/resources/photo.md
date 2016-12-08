# <a name="photo-resource-type"></a>Foto Ressourcentyp

Die Ressource **Foto** Fotos und Kamera stellt Eigenschaften bereit, beispielsweise EXIF-Metadaten auf eine [DriveItem](driveitem.md).


## <a name="properties"></a>Eigenschaften
| Eigenschaft                | Typ                      | Beschreibung                                                     |
|:------------------------|:--------------------------|:----------------------------------------------------------------|
| **takenDateTime**       | DateTimeOffset            | Stellt das Datum und die Zeit, die das Foto durchgeführt wurde. Schreibgeschützt.               |
| **cameraMake**          | String                    | Kamerahersteller. Schreibgeschützt.                                            |
| **cameraModel**         | String                    | Kamera-Objektmodell. Schreibgeschützt.                                                   |
| **fNumber**             | Double                    | Der von der Kamera f-stop-Wert. Schreibgeschützt.                               |
| **exposureDenominator** | Int32                     | Die als Nenner für den Bruch Belichtung Zeit aus der Kamera. Schreibgeschützt. |
| **exposureNumerator**   | Int32                     | Die Zähler für die Belichtung Zeit Teiler von der Kamera. Schreibgeschützt.   |
| **focalLength**         | Double                    | Die Zeitdauer, von der Kamera Mittelpunkt. Schreibgeschützt.                               |
| **ISO**                 | Int32                     | Der von der Kamera ISO-Wert. Schreibgeschützt.                                  |

## <a name="json-representation"></a>JSON-Darstellung

<!-- {
  "blockType": "resource",
  "optionalProperties": [  ],
  "@odata.type": "microsoft.graph.photo"
}-->
```json
{
  "cameraMake": "string",
  "cameraModel": "string",
  "exposureDenominator": 1024,
  "exposureNumerator": 1024,
  "fNumber": 1024,
  "focalLength": 1024,
  "iso": 1024,
  "takenDateTime": "String (timestamp)"
}
```

## <a name="remarks"></a>Hinweise
OneDrive für Unternehmen und SharePoint, nur die **TakenDateTime** -Eigenschaft zurückgegeben.


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "photo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
