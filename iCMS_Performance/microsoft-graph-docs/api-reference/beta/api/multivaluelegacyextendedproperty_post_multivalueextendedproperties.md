# <a name="create-multi-value-extended-property"></a>Erstellen von erweiterten Eigenschaft mit mehreren Werten

Erstellen Sie eine oder mehrere erweiterte mehrwertige Eigenschaften in einer neuen oder vorhandenen Instanz einer Ressource. 

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
|multiValueExtendedProperties|[MultiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md) -Auflistung| Ein Array mit mehreren Werten erweiterte Eigenschaften. |
|id|String|Geben Sie für jede Eigenschaft in der Auflistung **MultiValueExtendedProperties** diese Option, damit die Eigenschaft ermitteln. Es muss eine der unterstützten Formate folgen. Weitere Informationen finden Sie unter [Outlook erweiterte Eigenschaften (Übersicht)](../resources/extended-properties-overview.md) . Erforderlich.|
|value|string|Geben Sie für jede Eigenschaft in der Auflistung **MultiValueExtendedProperties** Wert der Eigenschaft. Erforderlich.|


## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert |
|:---------------|:----------|
| Autorisierung | Bearer token %|
| Inhaltstyp | Application/json |

## <a name="request-body"></a>Anforderungstext

Geben Sie einen JSON Rumpf jedes [MultiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md) -Objekts in der **MultiValueExtendedProperties** Collection-Eigenschaft einer Instanz der Ressource.

Beim Erstellen einer erweiterten Eigenschaft in einer _neuen_ Instanz der Ressource, zusätzlich zu der neuen **MultiValueExtendedProperties** -Auflistung geben Sie an, eine JSON-Darstellung der Ressourceninstanz (d. h., eine [Nachricht](../resources/message.md), [MailFolder](../resources/mailfolder.md), [Ereignis](../resources/event.md)usw.)

## <a name="response"></a>Antwort

#### <a name="response-code"></a>Antwortcode
Ein Vorgang erfolgreich bei der Erstellung einer erweiterten Eigenschaft in einer neuen Ressourceninstanz gibt `201 Created`, mit der Ausnahme in einer neuen Gruppe Post, abhängig von der Methode verwendet, die Operation zurückgeben kann `200 OK` oder `202 Accepted`.

In eine vorhandene Ressourceninstanz Erstellen einer erfolgreichen Vorgang gibt `200 OK`. 


#### <a name="response-body"></a>Antworttext

Beim Erstellen einer erweiterten Eigenschaft in einem unterstützten Ressource als [Gruppe Post](../resources/post.md)enthält die Antwort nur die neuen oder vorhandenen Instanz jedoch nicht die neue erweiterte Eigenschaft. Sehen Sie die neu erstellte erweiterte Eigenschaft, [die mit der erweiterten Eigenschaft erweiterte Instanz abzurufen](../api/multivaluelegacyextendedproperty_get.md).

Beim Erstellen einer erweiterten Eigenschaft in eine _neue_ Gruppe Bereitstellung enthält die Antwort nur ein Antwortcode aber nicht die neue Bereitstellung noch die erweiterte Eigenschaft. Sie können nicht in einer vorhandenen Gruppe Beitrag eine erweiterte Eigenschaft erstellen.


## <a name="example"></a>Beispiel
##### <a name="request-1"></a>Anforderung 1

Im ersten Beispiel wird eine erweiterte Eigenschaft in ein neues Ereignis alle in der gleiche Vorgang der POST-ANFORDERUNG mit mehreren Werten. Abgesehen von den Eigenschaften, die Sie normalerweise für ein neues Ereignis aufnehmen möchten, enthält der Anforderungstext **MultiValueExtendedProperties** -Auflistung, die eine erweiterte Eigenschaft enthält. Textkörper der Anforderung enthält für erweiterte mehrwertige Eigenschaft Folgendes:

- **Id** die Eigenschaft als ein Array von gibt Zeichenfolgen mit der angegebenen GUID und den Namen der `Recreation`. 
- **Wert** , der gibt `Recreation` als Array von String-Werten 3, `["Food", "Hiking", "Swimming"]`.
 

<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/events
Content-Type: application/json

{
  "subject": "Family reunion",
  "body": {
    "contentType": "HTML",
    "content": "Let's get together this Thanksgiving!"
  },
  "start": {
      "dateTime": "2015-11-26T09:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-29T21:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "Terrie@contoso.com",
        "name": "Terrie Barrera"
      },
      "type": "Required"
    },
    {
      "emailAddress": {
        "address": "Lauren@contoso.com",
        "name": "Lauren Solis"
      },
      "type": "Required"
    }
  ],
  "multiValueExtendedProperties": [
     {
           "id":"StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
           "value": ["Food", "Hiking", "Swimming"]
     }
  ]
}
```

##### <a name="response-1"></a>Antwort 1

Eine erfolgreiche Antwort wird angegeben, indem eine `HTTP 201 Created` Antwortcode, und enthält das neue Ereignis in der Antworttext, ähnelt die Antwort von [nur ein Ereignis erstellen](../api/user_post_events.md). Die Antwort enthält keine neu erstellte erweiterte Eigenschaften.

Sehen Sie die neu erstellte erweiterte Eigenschaft, die [das Ereignis erweitert mit der erweiterten Eigenschaft erhalten möchten](../api/multivaluelegacyextendedproperty_get.md).


****

##### <a name="request-2"></a>Anfordern von 2

Im zweite Beispiel erstellt eine erweiterte Eigenschaft für die angegebene Nachricht mit mehreren Werten. Die erweiterte Eigenschaft ist das einzige Element in der Auflistung **MultiValueExtendedProperties** . Textkörper der Anforderung umfasst folgende für die erweiterte Eigenschaft:
- **ID** gibt die Eigenschaft als ein Array von Zeichenfolgen mit der angegebenen GUID und den Namen `Palette`.
- **Wert** gibt `Palette` als Array von String-Werten 3, `["Green", "Aqua", "Blue"]`.

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2_as77AACHsLrBBBA=')

Content-Type: application/json

{
  "multiValueExtendedProperties": [
      {
         "id":"StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
         "value":["Green", "Aqua", "Blue"]
      }
    ]
}
```

##### <a name="response-2"></a>Antwort 2

Eine erfolgreiche Antwort wird angegeben, indem eine `HTTP 200 OK` Antwortcode, und die angegebene Meldung im Antworttext, ähnelt die Antwort aktualisieren [einer Nachricht](../api/message_update.md)enthält. Die Antwort enthält das neu erstellte keinen erweiterten Eigenschaft.

Sehen Sie die neu erstellte erweiterte Eigenschaft, [die mit der erweiterten Eigenschaft erweiterte ausgegeben werden](../api/multivaluelegacyextendedproperty_get.md).


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




