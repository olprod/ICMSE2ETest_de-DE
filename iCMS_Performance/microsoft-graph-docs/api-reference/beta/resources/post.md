# <a name="post-resource-type"></a>POST-Ressourcentyp

Stellt ein einzelnes Post-Element innerhalb einer [ConverstaionThread](conversationthread.md) Entität dar.

Eine neue Bereitstellung wird erstellt, wenn Sie:

- [Antworten Sie auf einen vorhandenen Beitrag](../api/post_reply.md) 
- [Antworten Sie auf einen vorhandenen thread](../api/conversationthread_reply.md) 
- [Erstellen eines Threads in einer neuen Unterhaltung](../api/group_post_threads.md)
- [Erstellen einer neuen Unterhaltung](../api/group_post_conversations.md)
 

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "extensions",
    "inReplyTo"
  ],
  "@odata.type": "microsoft.graph.post"
}-->

```json
{
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "categories": ["string"],
  "changeKey": "string",
  "conversationId": "string",
  "conversationThreadId": "string",
  "createdDateTime": "String (timestamp)",
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "newParticipants": [{"@odata.type": "microsoft.graph.recipient"}],
  "receivedDateTime": "String (timestamp)",
  "sender": {"@odata.type": "microsoft.graph.recipient"}
}

```
## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|body|[itemBody](itembody.md)|Der Inhalt des Beitrags. Dies ist eine Standardeigenschaft. Diese Eigenschaft kann null sein.|
|Kategorien|String-Auflistung|Die Kategorien, die im Beitrag zugeordnet.|
|changeKey|String|Gibt die Version des Beitrags. Jedes Mal, wenn der Beitrag geändert wird, ändert ChangeKey sowie. Dies ermöglicht Exchange zu Änderungen an die richtige Version des Objekts zu übernehmen.|
|conversationId|String|Eindeutige ID der Unterhaltung. Schreibgeschützt.|
|conversationThreadId|String|Eindeutige ID des Unterhaltungsthreads. Schreibgeschützt.|
|createdDateTime|DateTimeOffset|Gibt an, wann der Post erstellt wurde. Typ DateTimeOffset stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|from|[Empfänger](recipient.md)|In Access-Szenarien Delegaten verwendet. Gibt an, die die Nachricht im Auftrag eines anderen Benutzers bereitgestellt. Dies ist eine Standardeigenschaft.|
|hasAttachments|Boolean|Gibt an, ob der Post mindestens eine Anlage hat. Dies ist eine Standardeigenschaft.|
|id|String| Schreibgeschützt.|
|lastModifiedDateTime|DateTimeOffset|Gibt an, wann der Post zuletzt geändert wurde. Typ DateTimeOffset stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|newParticipants|[Empfänger](recipient.md) -Auflistung|Teilnehmer einer Unterhaltung, die die Thread im Rahmen dieser Beitrag hinzugefügt wurden.|
|receivedDateTime|DateTimeOffset|Gibt an, wann die POST-Anforderung empfangen wurde. Typ DateTimeOffset stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Absender|[Empfänger](recipient.md)|Enthält die Adresse des Absenders. Der Wert des Absenders wird davon ausgegangen, dass die Adresse des authentifizierten Benutzers im Fall sein, wenn der Absender nicht angegeben ist. Dies ist eine Standardeigenschaft.|


## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Anlagen|[Anlage](attachment.md) -Auflistung|Die Auflistung von [FileAttachment](fileattachment.md), [ItemAttachment](itemattachment.md)und [ReferenceAttachment](referenceAttachment.md) Anlagen für die Bereitstellung. Schreibgeschützt. NULL-Werte zulässt.|
|Erweiterungen|[Erweiterungssammlung](extension.md)|Die Auflistung der offenen Typ Daten Erweiterungen für die Bereitstellung definiert sind. Schreibgeschützt. NULL-Werte zulässt.|
|inReplyTo|[Bereitstellen](post.md)|Früheren Beitrags, den dieser Beitrag der [ConversationThread](conversationthread.md)beantwortet wird. Schreibgeschützt.|
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der Mehrfachwert erweiterte Eigenschaften für die Bereitstellung definiert sind. Schreibgeschützt. NULL-Werte zulässt.|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) -Auflistung| Die Auflistung der einwertig erweiterte Eigenschaften für die Bereitstellung definiert sind. Schreibgeschützt. NULL-Werte zulässt.|


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Liste Beiträge](../api/conversationthread_list_posts.md) | [Bereitstellen](post.md) |Rufen Sie die Beiträge des angegebenen Threads. |
|[POST-Anforderung erhalten möchten](../api/post_get.md) | [Bereitstellen](post.md) |Rufen Sie die Eigenschaften und die Beziehungen eines Beitrags in einem angegebenen Thread.|
|[Antwort](../api/post_reply.md)|Keine|Antworten auf eine Nachricht ein, und fügen Sie eine neue Bereitstellung auf den angegebenen Thread bei einer gruppenunterhaltung.|
|[Weiterleiten](../api/post_forward.md)|Keine|Weiterleiten Sie eine POST-Anforderung an einem Empfänger.|
|[Anlagen auflisten](../api/post_list_attachments.md) |[Anlage](attachment.md) -Auflistung| Rufen Sie eine Liste der Attachment-Objekte, die auf einen Beitrag angefügt.|
|[Anlage erstellen](../api/post_post_attachments.md) |[Anlage](attachment.md)| Hinzufügen einer Anlage auf einen Beitrag. |
|[Erstellen von Daten-Erweiterung](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| Erstellen Sie eine Erweiterung der offenen Typ Daten und Hinzufügen von benutzerdefinierten Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource.|
|[Abrufen von Daten-Erweiterung](../api/opentypeextension_get.md) |[OpenTypeExtension](opentypeextension.md) -Auflistung| Rufen Sie ein **OpenTypeExtension** oder Objekte nach Name oder den vollqualifizierten Namen identifiziert.|
|[Erweiterte Eigenschaft einwertig erstellen](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[Bereitstellen](post.md)  |Erstellen Sie eine oder mehrere einwertig erweiterte Eigenschaften in einem neuen oder vorhandenen Beitrag.   |
|[Abrufen von Post mit erweiterten Eigenschaft einwertig](../api/singlevaluelegacyextendedproperty_get.md)  | [Bereitstellen](post.md) | Abrufen von Beiträge, die einen erweiterte Eigenschaft mithilfe von Single-Wert enthalten `$expand` oder `$filter`. |
|[Erstellen von erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [Bereitstellen](post.md) | Erstellen Sie mindestens einen erweiterte mehrwertige Eigenschaften in einem neuen oder vorhandenen Beitrag.  |
|[Abrufen von Post mit erweiterten Eigenschaft mit mehreren Werten](../api/multivaluelegacyextendedproperty_get.md)  | [Bereitstellen](post.md) | Abrufen einer POST-Anforderung, die mithilfe eine erweiterte Eigenschaft mit mehreren Werte enthält `$expand`. |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "post resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->