# <a name="profilephoto-resource-type"></a>profilePhoto resource type
A profile photo of a user, group or an Outlook contact accessed from Exchange Online. It's binary data not encoded in base-64.

The supported sizes of HD photos on Exchange Online are as follows: '48x48', '64x64', '96x96', '120x120', '240x240', '360x360','432x432', '504x504', and '648x648'. 

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Get profilePhoto](../api/profilephoto_get.md) | [profilePhoto](profilephoto.md) |Get the specified **profilePhoto** or its metadata (profilePhoto properties).|
|[Update](../api/profilephoto_update.md) | [profilePhoto](profilephoto.md)  |Assign a photo to the specified user, group, or contact. The photo should be in binary. It replaces the existing photo, if any.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|ReadOnly|
|height|Int32|The height of the photo. Read-only.|
|width|Int32|The width of the photo. Read-only.|


## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON representation

Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.profilePhoto"
}-->

```json
{
  "id": "240X240",
  "height": 240,
  "width": 240
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "profilePhoto resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
