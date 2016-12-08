# <a name="opentypeextension-resource-type"></a>Ressourcentyp openTypeExtension

Ein **OpenTypeExtension** ist ein OData v4 öffnen Typ, der zur Laufzeit benutzerdefinierte Daten in Instanzen von Ressourcen im Datenmodell Entität definierten angeben kann. Dadurch sparen Sie Zeit, in der Definition des neuen Entitätstypen nur für diesen Zweck.

Sie können Daten Extensions vom Typ **OpenTypeExtension** in einer [Meldung](message.md), [Ereignis](event.md)oder [wenden Sie sich](contact.md) im Postfach des angemeldeten Benutzers oder in einem **Ereignis** in einer Organisation einen Gruppenkalender erstellen. In den einzelnen Benutzerkontext kann das Konto des Benutzers in Office 365 oder einem Microsoft-Konto (Hotmail.com, Live.com, MSN-, Outlook.com und Passport.com) sein.

Diese Ressource wird von [der abstrakten Erweiterungstyp](extension.md) abgeleitet und verfügt über zusätzliche **.-Kennung Erweiterungsname** -Eigenschaft.
Die **.-Kennung Erweiterungsname** -Eigenschaft ist die einzige vordefinierte, sofern nicht schreibgeschützte Eigenschaft für alle Extensions. Eine Möglichkeit, sorgen dafür, dass die Erweiterungsnamen sind eindeutig ist eine reverse Domain Name System (DNS)-Methode verwenden, beispielsweise _Ihre eigene Domäne_, abhängig ist `Com.Contoso.Contact`. Verwenden Sie die Microsoft-Domäne in einen Erweiterungsnamen nicht.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.opentypeextension"
}-->

```json
{
  "extensionName": "string",
  "id": "string (identifier)"
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|.-Kennung Erweiterungsname|String|Eine eindeutige ID Erweiterung Daten offener Typ. Erforderlich.|
|id|String| Ein vollqualifizierten Bezeichner, der den Erweiterungstyp mit der **.-Kennung Erweiterungsname**verkettet. Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Bereitstellen](../api/opentypeextension_post_opentypeextension.md) | [OpenTypeExtension](opentypeextension.md), oder [Meldung](../resources/message.md), [Ereignis](../resources/event.md)oder [wenden Sie sich an](../resources/contact.md) , die ein OpenTypeExtension Objekt enthält. | Erstellen Sie ein OpenTypeExtension Objekt in eine vorhandene oder neue Ressourceninstanz.| 
|[Erhalten](../api/opentypeextension_get.md) | [openTypeExtension](opentypeextension.md) |Lesen Sie Eigenschaften und Beziehungen des OpenTypeExtension-Objekts.|
|[Update](../api/opentypeextension_update.md) | [openTypeExtension](opentypeextension.md)   |Update OpenTypeExtension-Objekt. |
|[Löschen](../api/opentypeextension_delete.md) | Keine |OpenTypeExtension-Objekt zu löschen. |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "openTypeExtension resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->