# <a name="mailfolder-resource-type"></a>Ressourcentyp mailFolder

Ein MailFolder im Postfach eines Benutzers, wie Posteingang, Entwürfe und gesendete Objekte. MailFolders können Nachrichten und untergeordneten MailFolders enthalten.


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von mailFolder](../api/mailfolder_get.md) | [mailFolder](mailfolder.md) |Lesen Sie Eigenschaften und Beziehungen des MailFolder-Objekts.|
|[MailFolder erstellen](../api/mailfolder_post_childfolders.md) |[mailFolder](mailfolder.md)| Erstellen Sie eine neue MailFolder unter der aktuellen Unterhaltung durch die Veröffentlichung auf der ChildFolders-Auflistung.|
|[Liste childFolders](../api/mailfolder_list_childfolders.md) |[MailFolder](mailfolder.md) -Auflistung| Rufen Sie die Ordner-Auflistung, unter dem angegebenen Ordner. Sie können die `.../me/MailFolders` Verknüpfung mit die Ordner der obersten Ebene-Auflistung abrufen und navigieren zu einem anderen Ordner.|
|[Nachricht erstellen](../api/mailfolder_post_messages.md) |[Nachricht](message.md)| Erstellen Sie eine neue Nachricht in der aktuellen MailFolder durch die Veröffentlichung auf der Nachrichten-Auflistung.|
|[Listennachrichten](../api/mailfolder_list_messages.md) |[Nachricht](message.md) -Auflistung| Rufen Sie alle Nachrichten im Postfach des angemeldeten Benutzers oder diese Nachrichten in einem angegebenen Ordner im Postfach.|
|[Update](../api/mailfolder_update.md) | [mailFolder](mailfolder.md)|Aktualisiert das angegebene MailFolder-Objekt. |
|[Löschen](../api/mailfolder_delete.md) | Keine |Das angegebene MailFolder-Objekt gelöscht. |
|[Kopie](../api/mailfolder_copy.md)|[mailFolder](mailfolder.md)|Kopieren Sie eine MailFolder und seinen Inhalt zu einer anderen MailFolder ein.|
|[Verschieben](../api/mailfolder_move.md)|[mailFolder](mailfolder.md)|Verschieben Sie ein MailFolder und seinen Inhalt zu einer anderen MailFolder.|
|[Erweiterte Eigenschaft einwertig erstellen](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[mailFolder](mailFolder.md)  |Erstellen Sie mindestens einen Single-Wert erweiterte Eigenschaften in einer neuen oder vorhandenen MailFolder.   |
|[Abrufen von MailFolder mit erweiterten einwertig-Eigenschaft](../api/singlevaluelegacyextendedproperty_get.md)  | [mailFolder](mailFolder.md) | Erhalten möchten, das einen Single-Wert erweiterte Eigenschaft mit enthalten MailFolders `$expand` oder `$filter`. |
|[Erstellen von erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [mailFolder](mailFolder.md) | Erstellen Sie eine oder mehrere erweiterte mehrwertige Eigenschaften in einem neuen oder vorhandenen MailFolder.  |
|[Abrufen von MailFolder mit erweiterten Mehrfachwert-Eigenschaft](../api/multivaluelegacyextendedproperty_get.md)  | [mailFolder](mailFolder.md) | Abrufen einer MailFolder an, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`. |


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|childFolderCount|Int32|Die Anzahl der MailFolders in der aktuellen MailFolder direkt untergeordnet.|
|displayName|String|Anzeigename der MailFolder.|
|id|String|Eindeutiger Bezeichner der MailFolder. Sie können die folgenden bekannten Namen verwenden, um Zugriff auf den entsprechenden Ordner: Posteingang, Entwürfe, gesendete Elemente, DeletedItems.|
|parentFolderId|String|Der eindeutige Bezeichner für die MailFolder übergeordneten MailFolder.|
|totalItemCount|Int32|Die Anzahl der Elemente in der MailFolder.|
|unreadItemCount|Int32|Die Anzahl der Elemente in der MailFolder als ungelesen markiert.|

**Access-Element zählt effizient**

TotalItemCount und UnreadItemCount der Eigenschaften eines Ordners können Sie bequem die Anzahl der gelesenen Elemente im Ordner Statistik.
Sie können Sie die Abfragen wie folgt zu vermeiden, die erhebliche Wartezeiten auftreten kann:
```
https://outlook.office.com/api/v1.0/me/folders/inbox/messages?$count=true&$filter=isread%20eq%20false
```
MailFolders in Outlook kann mehrere Typen von Elementen enthalten, beispielsweise der Posteingang enthalten kann Anforderung Besprechungselemente vom e-Mail-Elemente darstellen. TotalItemCount und UnreadItemCount einschließen Elemente in einer MailFolder unabhängig von deren Elementtypen.


## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|childFolders|[MailFolder](mailfolder.md) -Auflistung|Die Auflistung von untergeordneten Ordner in der MailFolder.|
|Nachrichten|[Nachricht](message.md) Auflistung|Die Auflistung von Nachrichten in der MailFolder.|
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der Mehrfachwert erweiterte Eigenschaften für die MailFolder definiert ist. Schreibgeschützt. NULL-Werte zulässt.|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der einwertig erweiterte Eigenschaften für die MailFolder definiert ist. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "childFolders",
    "messages"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.mailFolder"
}-->

```json
{
  "childFolderCount": 1024,
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string",
  "totalItemCount": 1024,
  "unreadItemCount": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "mailFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
