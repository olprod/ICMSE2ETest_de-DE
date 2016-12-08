# <a name="profilephoto-resource-type"></a>Ressourcentyp profilePhoto
Ein Profilfoto von einem Benutzer, Gruppe oder ein Outlook-Kontakt auf die in Exchange Online oder Azure Active Directory (AAD) zugegriffen. Es ist nicht im Base64-codierte Binärdaten.

Zu den unterstützten Größen von HD-Fotos in Exchange Online sind wie folgt: '48 x 48', "64 x 64", '96 x 96', '120 x 120', '240 x 240', ' 360 x 360', '432 x 432', '504 x 504' und ' 648 x 648'. Klicken Sie auf AAD können Fotos alle Dimension sein.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von profilePhoto](../api/profilephoto_get.md) | [profilePhoto](profilephoto.md) |Rufen Sie die angegebenen **ProfilePhoto** oder der Metadaten (**ProfilePhoto** Eigenschaften). |
|[Update](../api/profilephoto_update.md) | [profilePhoto](profilephoto.md)  |Weisen Sie ein Foto der angegebenen Benutzer, Gruppe oder des Kontakts. Das Foto sollte in Binär. Gegebenenfalls das vorhandene Foto ersetzt. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|id|string|Schreibgeschützt.|
|height|Int32|Die Höhe des Fotos. Schreibgeschützt.|
|width|Int32|Die Breite des Fotos. Schreibgeschützt.|


## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

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
