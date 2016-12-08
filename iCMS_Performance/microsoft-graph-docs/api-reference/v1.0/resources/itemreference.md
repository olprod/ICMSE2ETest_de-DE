# <a name="itemreference-resource-type"></a>ItemReference Ressourcentyp

 Die Daten auf einer [DriveItem](driveitem.md) mithilfe der API zu verweisen.

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ   | Beschreibung                                                                   |
|:---------|:-------|:------------------------------------------------------------------------------|
| Laufwerks  | String | Eindeutiger Bezeichner der OneDrive-Instanz, die das Element enthält. Schreibgeschützt. |
| id       | String | Eindeutiger Bezeichner des Elements in das Laufwerk. Schreibgeschützt.            |
| Pfad     | String | Pfad, der verwendet werden kann, um das Element zu navigieren. Schreibgeschützt.                     |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "path" ],
  "@odata.type": "microsoft.graph.itemReference"
}-->

```json
{
  "driveId": "string",
  "id": "string",
  "path": "string"
}
```

## <a name="remarks"></a>Hinweise

Um ein Element aus einer **ItemReference** Instanz zu beheben, erstellen Sie eine URL im Format:

```http
GET https://graph.microsoft.com/v1.0/drives/<driveId>/items/<id>
```

Der Wert der **Path** ist ein API-Pfad relativ zu dem Ziellaufwerk, zum Beispiel: `/drive/root:/Documents/myfile.docx`.

Zum Abrufen des lesbare Pfads für Breadcrumb können Sie ignorieren alles bis zum ersten `:` in der Pfadzeichenfolge.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "itemReference resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
