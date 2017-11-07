# <a name="contactfolder-resource-type"></a>Ressourcentyp contactFolder

Ein Ordner, der Kontakte enthält.

## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von contactFolder](../api/contactfolder_get.md) | [contactFolder](contactfolder.md) |Abrufen von einem Kontaktordner unter Verwendung der Kontaktordner-ID.|
|[Update](../api/contactfolder_update.md) | [contactFolder](contactfolder.md) |Update ContactFolder-Objekt. |
|[Löschen](../api/contactfolder_delete.md) | Keine |ContactFolder-Objekt zu löschen. |
|[Liste childFolders](../api/contactfolder_list_childfolders.md) |[ContactFolder](contactfolder.md) -Auflistung| Rufen Sie eine Auflistung von untergeordneten Ordner unter dem angegebenen Kontaktordner.|
|[Erstellen von untergeordneten contactFolder](../api/contactfolder_post_childfolders.md) |[ContactFolder](contactfolder.md)| Erstellen einer neuen ContactFolder als untergeordnetes Element eines angegebenen Ordners an.|
|[Liste Kontakte im Ordner](../api/contactfolder_list_contacts.md) |[Kontakt](contact.md) -Auflistung| Abrufen einer Kontakte Auflistung aus den Standardordner Kontakte des angemeldeten Benutzers (`.../me/contacts`), oder aus der angegebenen Kontaktordner.|
|[Kontakt im Ordner erstellen](../api/contactfolder_post_contacts.md) |[Kontakt](contact.md)| Hinzufügen eines Kontakts in den Stammordner Kontakte oder zu den `contacts` Endpunkt von einer anderen Kontaktordner.|



## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|displayName|String|Der Name des Ordners anzeigen.|
|id|String|Eindeutiger Bezeichner des Ordners Kontakte. Schreibgeschützt.|
|parentFolderId|String|Die ID des übergeordneten Ordners des Ordners.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|childFolders|[ContactFolder](contactfolder.md) -Auflistung|Die Auflistung von untergeordneten Ordner im Ordner. Navigationseigenschaft. Schreibgeschützt. NULL-Werte zulässt.|
|Kontakte|[Kontakt](contact.md) -Auflistung|Die Kontakte im Ordner. Navigationseigenschaft. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "childFolders",
    "contacts"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.contactFolder"
}-->

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contactFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
