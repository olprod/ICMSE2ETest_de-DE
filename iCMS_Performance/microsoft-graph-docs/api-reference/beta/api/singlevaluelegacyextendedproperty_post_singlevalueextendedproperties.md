# <a name="create-single-value-extended-property"></a>Erweiterte Eigenschaft einwertig erstellen

Erstellen Sie eine oder mehrere einwertig erweiterte Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource. 

Die folgenden Benutzerressourcen werden unterstützt:

- [Nachricht](../resources/message.md)
- [mailFolder](../resources/mailfolder.md)
- [Ereignis](../resources/event.md)
- [Kalender](../resources/calendar.md)
- [Wenden Sie sich an](../resources/contact.md)
- [contactFolder](../resources/contactfolder.md) 

Sowie die folgenden Gruppenressourcen:

- Gruppe- [Ereignis](../resources/event.md)
- Gruppe [Kalender](../resources/calendar.md)
- Gruppe [Buchen](../resources/post.md) 

Weitere Informationen zur Verwendung von Office 365 Daten Extensions oder erweiterten Eigenschaften und zur Angabe der erweiterter Eigenschaften finden Sie unter [Erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) .

## <a name="prerequisites"></a>Voraussetzungen

Einen der folgenden **Bereiche** ist diese API, abhängig von der Ressource ausgeführt, das Sie in die erweiterte Eigenschaft erstellen erforderlich:

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP-Anforderung
Sie können erweiterte Eigenschaften in einer neuen oder vorhandenen Ressourceninstanz erstellen.

Um eine oder mehrere erweiterte Eigenschaften in einer _neuen_ Instanz der Ressource zu erstellen, verwenden Sie die gleiche REST-Anforderung als die Instanz erstellt und enthalten Sie die Eigenschaften für die neue Ressource Instanz _und erweiterte Eigenschaft_ im Textkörper Anforderung.
Beachten Sie, dass einige Ressourcen in mehr als eine Möglichkeit der Erstellung unterstützt. Weitere Informationen zum Erstellen von diese Ressourceninstanzen finden Sie unter den entsprechenden Themen für die Erstellung einer [Nachricht](../resources/message.md), [MailFolder](../api/user_post_mailfolders.md), [Ereignis](../api/user_post_events.md), [Kalender](../api/user_post_calendars.md), [wenden Sie sich an](../api/user_post_contacts.md), [ContactFolder](../api/user_post_contactfolders.md), [Gruppe-Ereignis](../api/group_post_events.md)und [Gruppe Beitrag](../resources/post.md). 
 
Es folgt die Syntax der Anforderungen. 

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages
POST /users/<id|userPrincipalName>/messages
POST /me/mailFolders/<id>/messages

POST /me/mailFolders
POST /users/<id|userPrincipalName>/mailFolders

POST /me/events
POST /users/<id|userPrincipalName>/events

POST /me/calendars
POST /users/<id|userPrincipalName>/calendars

POST /me/contacts
POST /users/<id|userPrincipalName>/contacts

POST /me/contactFolders
POST /users/<id|userPrincipalName>/contactFolders

POST /groups/<id>/events

POST /groups/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/threads/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/reply
POST /groups/<id>/threads
POST /groups/<id>/conversations
```

So erstellen Sie eine oder mehrere erweiterte Eigenschaften in einer vorhandenen Ressourceninstanz, geben Sie die Instanz in der Anforderung und enthalten Sie die erweiterte Eigenschaft im Textkörper Anforderung.

**Hinweis** Sie können keine erweiterte Eigenschaft in einer vorhandenen Gruppe Beitrag erstellen.

<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id|userPrincipalName>/messages/<id>
PATCH /me/mailFolders/<id>/messages/<id>

PATCH /me/mailFolders/<id>
PATCH /users/<id|userPrincipalName>/mailFolders/<id>

PATCH /me/events/<id>
PATCH /users/<id|userPrincipalName>/events/<id>

PATCH /me/calendars/<id>
PATCH /users/<id|userPrincipalName>/calendars/<id>

PATCH /me/contacts/<id>
PATCH /users/<id|userPrincipalName>/contacts/<id>

PATCH /me/contactFolders/<id>
PATCH /users/<id|userPrincipalName>/contactFolders/<id>

PATCH /groups/<id>/events/<id>
```


## <a name="parameters"></a>Parameter
|**Parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|_URL-Parameter_|
|id|string|Ein eindeutiger Bezeichner für ein Objekt, das durch seine **Id** -Eigenschaft in der entsprechenden Auflistung dargestellt. Erforderlich.|
|_Textkörper-Parameter_|
|singleValueExtendedProperties|[SingleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md) -Auflistung| Ein Array von mindestens ein einwertiges erweiterte Eigenschaften. |
|id|String|Geben Sie für jede Eigenschaft in der Auflistung **SingleValueExtendedProperties** diese Option, damit die Eigenschaft ermitteln. Es muss eine der unterstützten Formate folgen. Weitere Informationen finden Sie unter [Outlook erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) . Erforderlich.|
|value|string|Geben Sie für jede Eigenschaft in der Auflistung **SingleValueExtendedProperties** Wert der Eigenschaft. Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|
| Inhaltstyp | Application/json |

## <a name="request-body"></a>Anforderungstext

Geben Sie einen JSON Rumpf jedes [SingleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md) -Objekts in der **SingleValueExtendedProperties** Collection-Eigenschaft einer Instanz der Ressource.

Beim Erstellen einer erweiterten Eigenschaft in einer _neuen_ Instanz der Ressource, zusätzlich zu der neuen **SingleValueExtendedProperties** -Auflistung geben Sie an, eine JSON-Darstellung der Ressourceninstanz (d. h., eine [Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md)usw.)

## <a name="response"></a>Antwort

#### <a name="response-code"></a>Antwortcode
Ein Vorgang erfolgreich bei der Erstellung einer erweiterten Eigenschaft in einer neuen Ressourceninstanz gibt `201 Created`, mit der Ausnahme in einer neuen Gruppe Post, abhängig von der Methode verwendet, die Operation zurückgeben kann `200 OK` oder `202 Accepted`.

In eine vorhandene Ressourceninstanz Erstellen einer erfolgreichen Vorgang gibt `200 OK`. 


#### <a name="response-body"></a>Antworttext

Beim Erstellen einer erweiterten Eigenschaft enthält die Antwort nur die neuen oder vorhandenen Instanz jedoch nicht die neue erweiterte Eigenschaft. Sehen Sie die neu erstellte erweiterte Eigenschaft, [die mit der erweiterten Eigenschaft erweiterte Instanz abzurufen](../api/singlevaluelegacyextendedproperty_get.md).

Beim Erstellen einer erweiterten Eigenschaft in einer _neuen_ [Gruppe Post](../resources/post.md) von Antworten auf einen Thread oder Post enthält die Antwort nur ein Antwortcode aber nicht die neue Bereitstellung noch die erweiterte Eigenschaft.



## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1

Im erste Beispiel erstellt ein neues Ereignis und einer erweiterten Eigenschaft Single-Wert in der gleichen POST-Operation. Abgesehen von den Eigenschaften, die Sie normalerweise für ein neues Ereignis aufnehmen möchten, enthält der Anforderungstext **SingleValueExtendedProperties** -Auflistung, die eine erweiterte einwertig-Eigenschaft und die folgenden für die Eigenschaft enthält:

- **ID** gibt den Eigenschaftstyp als an `String`, die GUID und die Eigenschaft mit dem Namen `Fun`.
- **Wert** gibt `Food` als Wert für die `Fun` Eigenschaft. 

<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/events
Content-Type: application/json

{
  "subject": "Celebrate Thanksgiving",
  "body": {
    "contentType": "HTML",
    "content": "Let's get together!"
  },
  "start": {
      "dateTime": "2015-11-26T18:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-26T23:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "Terrie@contoso.com",
        "name": "Terrie Barrera"
      },
      "type": "Required"
    }
  ],
  "singleValueExtendedProperties": [
     {
           "id":"String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
           "value":"Food"
     }
  ]
}
```

##### <a name="response-1"></a>Antwort 1

Eine erfolgreiche Antwort wird angegeben, indem eine `HTTP 201 Created` Antwortcode, und enthält das neue Ereignis in der Antworttext, ähnelt die Antwort von [nur ein Ereignis erstellen](../api/user_post_events.md). Die Antwort enthält keine neu erstellte erweiterte Eigenschaften.

Sehen Sie die neu erstellte erweiterte Eigenschaft, die [das Ereignis erweitert mit der erweiterten Eigenschaft erhalten möchten](../api/singlevaluelegacyextendedproperty_get.md).


****

##### <a name="request-2"></a>Anfordern von 2

Im zweite Beispiel erstellt einen Single-Wert, erweiterte Eigenschaft für die angegebene vorhandene Nachricht. Mit der erweiterten Eigenschaft ist das einzige Element im Array **SingleValueExtendedProperties** . Textkörper der Anforderung umfasst folgende für die erweiterte Eigenschaft:
- **ID** gibt an, welche Eigenschaft als `String`, die GUID und die Eigenschaft mit dem Namen `Color`.
- **Wert** gibt `Green` als Wert für die `Color` Eigenschaft.

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')

Content-Type: application/json

{
  "singleValueExtendedProperties": [
      {
         "id":"String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
         "value":"Green"
      }
    ]
}
```

##### <a name="response-2"></a>Antwort 2

Eine erfolgreiche Antwort wird angegeben, indem eine `HTTP 200 OK` Antwortcode, und die angegebene Meldung im Antworttext, ähnelt die Antwort aktualisieren [einer Nachricht](../api/message_update.md)enthält. Die Antwort enthält das neu erstellte keinen erweiterten Eigenschaft.

Sehen Sie die neu erstellte erweiterte Eigenschaft, [die mit der erweiterten Eigenschaft erweiterte ausgegeben werden](../api/singlevaluelegacyextendedproperty_get.md).

<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create a single-value extended property",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

