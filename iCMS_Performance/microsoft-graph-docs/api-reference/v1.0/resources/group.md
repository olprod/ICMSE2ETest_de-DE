# <a name="group-resource-type"></a>Gruppe Ressourcentyp

Stellt eine Azure Active Directory-Gruppe, die ein Office 365-Gruppe, dynamische Gruppe oder Sicherheitsgruppe sein kann.
Erbt vom [DirectoryObject](directoryobject.md).


## <a name="methods"></a>Methoden

| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
|[Gruppe erstellen](../api/group_post_groups.md) | [Gruppe](group.md) |Erstellen einer neuen Gruppe wie angegeben. Sie können ein Office 365, dynamische Gruppe oder Sicherheitsgruppe sein.|
|[Erste Gruppe](../api/group_get.md) | [Gruppe](group.md) |Eigenschaften lesen und Beziehungen des Group-Objekt.|
|[Aktualisierungsgruppe](../api/group_update.md) | [Gruppe](group.md) |Aktualisieren Sie die Eigenschaften eines Group-Objekts. |
|[Gruppe löschen](../api/group_delete.md) | Keine |Group-Objekt gelöscht werden. |
|[Liste Besitzer](../api/group_list_owners.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Besitzer der Gruppe aus der Navigationseigenschaft **Besitzer** .|
|[Besitzer hinzufügen](../api/group_post_owners.md) |[directoryObject](directoryobject.md)| Fügen Sie einen neuen Besitzer für die Gruppe, indem das Veröffentlichen in der **Besitzer** Navigationseigenschaft (für Sicherheitsgruppen und e-Mail-aktivierte Sicherheitsgruppen nur unterstützt).|
|[Mitglieder der Liste](../api/group_list_members.md) |[DirectoryObject](directoryobject.md) -Auflistung| Rufen Sie die Benutzer und Gruppen, die direkte Mitglieder aus der Navigationseigenschaft **Mitglieder** dieser Gruppe sind.|
|[Mitglied hinzufügen](../api/group_post_members.md) |[directoryObject](directoryobject.md)| Fügen Sie einen Benutzer oder eine Gruppe dieser Gruppe durch das Veröffentlichen in der **Mitglieder** Navigationseigenschaft (für Sicherheitsgruppen und e-Mail-aktivierte Sicherheitsgruppen nur unterstützt).|
|[Entfernen von Mitgliedern](../api/group_delete_members.md) | Keine |Entfernen Sie ein Mitglied aus einer Office 365, eine Sicherheitsgruppe oder eine e-Mail-aktivierte Sicherheitsgruppe über die **Mitglieder** Navigation-Eigenschaft. Sie können Benutzer oder andere Gruppen entfernen. |
|[Liste Mitglied](../api/group_list_memberof.md) |[DirectoryObject](directoryobject.md) -Auflistung| Abrufen von Gruppen, dass diese Gruppe direktes Mitglied, aus der Navigationseigenschaft **Mitglied** ist.|
|[checkMemberGroups](../api/group_checkmembergroups.md)|String-Auflistung|Überprüfen Sie die Mitgliedschaft in einer Liste von Gruppen. Die Funktion ist transitiv.|
|[getMemberGroups](../api/group_getmembergroups.md)|String-Auflistung|Zurückgeben Sie aller Gruppen, denen die Gruppe ein Mitglied ist. Die Funktion ist transitiv.|
|[getMemberObjects](../api/group_getmemberobjects.md)|String-Auflistung|Zurückgeben Sie aller Gruppen, denen die Gruppe ein Mitglied ist. Die Funktion ist transitiv. |
|[List-Ereignisse](../api/group_list_events.md) |[Ereignissammlung](event.md)| Rufen Sie eine Auflistung der Ereignis-Objekts.|
|[Ereignis erstellen](../api/group_post_events.md) |[Ereignis](event.md)| Erstellen Sie ein neues Ereignis, indem Sie das Veröffentlichen in der Auflistung Ereignisse.|
|[Liste calendarView](../api/group_list_calendarview.md) |[Ereignissammlung](event.md)| Rufen Sie eine Auflistung von Ereignissen in einem angegebenen Zeitfenster.|
|[Liste Unterhaltungen](../api/group_list_conversations.md) |[Unterhaltung](conversation.md) -Auflistung| Rufen Sie eine Auflistung der Unterhaltung-Objekts.|
|[Unterhaltung erstellen](../api/group_post_conversations.md) |[Unterhaltung](conversation.md)| Erstellen Sie eine neue Unterhaltung durch das Veröffentlichen in der Auflistung Unterhaltungen.|
|[Liste threads](../api/group_list_threads.md) |[ConversationThread](conversationthread.md) -Auflistung| Rufen Sie alle Threads einer Gruppe.|
|[Liste acceptedSenders](../api/group_list_acceptedsenders.md) |[DirectoryObject](directoryobject.md) -Auflistung| Abrufen einer Liste von Benutzern oder Gruppen, die in der Liste AcceptedSenders für diese Gruppe sind.|
|[AcceptedSender hinzufügen](../api/group_post_acceptedsenders.md) |[directoryObject](directoryobject.md)| Fügen Sie einen Benutzer oder eine Gruppe zur AcceptSenders-Auflistung hinzu.|
|[AcceptedSender entfernen](../api/group_delete_acceptedsenders.md) |[directoryObject](directoryobject.md)| Entfernen Sie einen Benutzer oder eine Gruppe aus der AcceptedSenders-Auflistung.|
|[Liste rejectedSenders](../api/group_list_rejectedsenders.md) |[DirectoryObject](directoryobject.md) -Auflistung| Abrufen einer Liste von Benutzern oder Gruppen, die in der Liste RejectedSenders für diese Gruppe sind.|
|[RejectedSender hinzufügen](../api/group_post_rejectedsenders.md) |[directoryObject](directoryobject.md)| Fügen Sie der RejectedSenders-Auflistung einen neuen Benutzer oder eine Gruppe hinzu.|
|[RejectedSender entfernen](../api/group_delete_rejectedsenders.md) |[directoryObject](directoryobject.md)| Entfernen Sie die neue neuen Benutzer oder eine Gruppe aus der RejectedSenders-Auflistung.|
|[addFavorite](../api/group_addfavorite.md)|Keine|Fügen Sie die Gruppe, zu der Liste der bevorzugten Gruppen des aktuellen Benutzers. Unterstützt nur die Office 365-Gruppen.|
|[removeFavorite](../api/group_removefavorite.md)|Keine|Entfernen Sie die Gruppe aus der Liste der bevorzugten Gruppen des aktuellen Benutzers. Unterstützt nur die Office 365-Gruppen.|
|[subscribeByMail](../api/group_subscribebymail.md)|Keine|Die IsSubscribedByMail-Eigenschaft auf **true**festgelegt. Aktivieren den aktuellen Benutzer zum Empfangen von e-Mail-Unterhaltungen. Unterstützt nur die Office 365-Gruppen.|
|[unsubscribeByMail](../api/group_unsubscribebymail.md)|Keine|Legen Sie die IsSubscribedByMail-Eigenschaft auf **false fest**. Deaktivieren den aktuellen Benutzer aus e-Mail-Unterhaltungen empfangen. Unterstützt nur die Office 365-Gruppen.|
|[resetUnseenCount](../api/group_resetunseencount.md)|Keine|Setzen Sie die UnseenCount auf 0 der alle Beiträge, die der aktuelle Benutzer seit seinem letzten Besuch nicht erkannt wurde. Unterstützt nur die Office 365-Gruppen.|


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|Standard ist **false**. Gibt an, ob externe Mitglieder e-Mail an Gruppe senden können. Sie können diese Eigenschaft in einer PATCH-Anforderung für die Gruppe festgelegt. Legen Sie sie nicht in der anfänglichen POST-Anforderung, die die Gruppe erstellt.|
|autoSubscribeNewMembers|Boolean|Standard ist **false**. Gibt an, ob neue Mitglieder der Gruppe hinzugefügt automatisch zum Empfangen von e-Mail-Benachrichtigungen abonniert werden. Sie können diese Eigenschaft in einer PATCH-Anforderung für die Gruppe festgelegt. Legen Sie sie nicht in der anfänglichen POST-Anforderung, die die Gruppe erstellt.|
|description|String|Eine optionale Beschreibung für die Gruppe. |
|displayName|String|Der Anzeigename für die Gruppe. Diese Eigenschaft ist erforderlich, wenn eine Gruppe erstellt wird und kann nicht während des Updates deaktiviert werden. Unterstützt $filter und $orderby.|
|groupTypes|String-Auflistung| Gibt den Typ der Gruppe zu erstellen. Mögliche Werte sind **Unified** zum Erstellen einer Gruppe von Office 365 oder **DynamicMembership** für dynamische Gruppen.  Für alle anderen Gruppe Typen, wie Sicherheit-aktivierten Gruppen und e-Mail-aktivierte Sicherheitsgruppen diese Eigenschaft nicht festlegen.|
|id|String|Der eindeutige Bezeichner für die Gruppe. Geerbt von [DirectoryObject](directoryobject.md). -Taste. Nicht NULL-Werte zulässt. Schreibgeschützt.|
|isSubscribedByMail|Boolean|Standardwert ist **true**. Gibt an, ob der aktuelle Benutzer zum Empfangen von e-Mail-Unterhaltungen abonniert ist.|
|Mail|String|Die SMTP-Adresse für die Gruppe "serviceadmins@contoso.onmicrosoft.com". schreibgeschützt. $Filter unterstützt.|
|mailEnabled|Boolean|Gibt an, ob die Gruppe e-Mail-aktiviert ist. Wenn auch die **SecurityEnabled** -Eigenschaft **true**ist, ist die Gruppe eine e-Mail-aktivierte Sicherheitsgruppe; Andernfalls ist die Gruppe eine Verteilergruppe Microsoft Exchange.|
|mailNickname|String|Der e-Mail-Alias für die Gruppe. Diese Eigenschaft muss angegeben werden, wenn eine Gruppe erstellt wird. $Filter unterstützt.|
|onPremisesLastSyncDateTime|DateTimeOffset|Gibt das letzte Mal an dem das Objekt mit dem lokalen Verzeichnis synchronisiert wurde. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise könnte Uhr UTC auf 1 Jan 2014 wie folgt aussehen: `'2014-01-01T00:00:00Z'`. Schreibgeschützt. $Filter unterstützt.|
|onPremisesSecurityIdentifier|String|Enthält die lokale Sicherheits-ID (SID) für die Gruppe, die lokal in der Cloud synchronisiert wurde. Schreibgeschützt. |
|onPremisesSyncEnabled|Boolean|**true,** Wenn dieses Objekt aus einem lokalen Verzeichnis synchronisiert ist. **false,** Wenn dieses Objekt ursprünglich aus einem lokalen Verzeichnis synchronisiert wurde, aber nicht mehr synchronisiert ist. **null,** Wenn dieses Objekt aus einem lokalen Verzeichnis (Standard) nie synchronisiert wurden. Schreibgeschützt. $Filter unterstützt.|
|Proxyadressen|String-Auflistung| Der **any** -Operator ist für Filterausdrücke auf mehrwertige Eigenschaften erforderlich. Schreibgeschützt. Nicht NULL-Werte zulässt. $Filter unterstützt. |
|securityEnabled|Boolean|Gibt an, ob die Gruppe eine Sicherheitsgruppe ist. Wenn auch die **MailEnabled** -Eigenschaft true ist, ist die Gruppe eine e-Mail-aktivierte Sicherheitsgruppe an. Andernfalls handelt es sich um eine Sicherheitsgruppe. **"False"** für Office 365-Gruppen muss sein. $Filter unterstützt.|
|unseenCount|Int32|Anzahl der Beiträge, die der aktuelle Benutzer seit der letzten Besuch nicht erkannt wurde.|
|visibility|String| Gibt die Sichtbarkeit einer Office 365-Gruppe. Mögliche Werte sind: **Private**, **Public**oder leer (die als **Öffentliche**interpretiert wird).|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|acceptedSenders|[DirectoryObject](directoryobject.md) -Auflistung|Die Liste der Benutzer oder Gruppen, die zum Erstellen des Post oder Ereignisse im Kalender in dieser Gruppe zulässig sind. Wenn diese Liste nicht leer ist nur Benutzer oder Gruppen, die hier aufgeführten dürfen bereitstellen.|
|calendar|[Kalender](calendar.md)|Die Gruppe Kalender. Schreibgeschützt.|
|calendarView|[Ereignissammlung](event.md)|Die Kalenderansicht für den Kalender. Schreibgeschützt.|
|Gespräche|[Unterhaltung](conversation.md) -Auflistung|Unterhaltungen der Gruppe.|
|createdOnBehalfOf|[directoryObject](directoryobject.md)| Schreibgeschützt.|
|Laufwerk|[Laufwerk](drive.md)|Laufwerk der Gruppe. Schreibgeschützt.|
|Ereignisse|[Ereignissammlung](event.md)|Ereignisse, die der Gruppe.|
|Mitglied|[DirectoryObject](directoryobject.md) -Auflistung|Gruppen, denen dieser Gruppe ein Mitglied ist. HTTP-Methoden: ABRUFEN (unterstützt für alle Gruppen). Schreibgeschützt. NULL-Werte zulässt.|
|Member|[DirectoryObject](directoryobject.md) -Auflistung| Benutzer, Kontakte und Gruppen, die Mitglieder dieser Gruppe sind. HTTP-Methoden: ABRUFEN (unterstützt für alle Gruppen), POST (unterstützt für Sicherheitsgruppen und e-Mail-aktivierten Sicherheitsgruppen), DELETE (unterstützt nur für Sicherheitsgruppen) schreibgeschützt. NULL-Werte zulässt.|
|Besitzer|[DirectoryObject](directoryobject.md) -Auflistung|Der Besitzer der Gruppe. Die Besitzer sind eine Reihe von nicht-Administrator-Benutzer, die berechtigt sind, dieses Objekt zu ändern. HTTP-Methoden: ABRUFEN (unterstützt für alle Gruppen), POST (unterstützt für Sicherheitsgruppen und e-Mail-aktivierten Sicherheitsgruppen), DELETE (unterstützt nur für Sicherheitsgruppen) schreibgeschützt. NULL-Werte zulässt.|
|Foto|[profilePhoto](profilephoto.md)| Die Gruppe Profilfoto |
|rejectedSenders|[DirectoryObject](directoryobject.md) -Auflistung|Die Liste der Benutzer oder Gruppen, die zum Erstellen von Beiträgen oder Ereignisse im Kalender in dieser Gruppe nicht zulässig sind. Nullwerte zulassen|
|Threads|[ConversationThread](conversationthread.md) -Auflistung| Die Gruppe Unterhaltung Threads. NULL-Werte zulässt.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "acceptedSenders",
    "appRoleAssignments",
    "calendar",
    "calendarView",
    "conversations",
    "createdOnBehalfOf",
    "drive",
    "events",
    "memberOf",
    "members",
    "owners",
    "photo",
    "rejectedSenders",
    "threads"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.group"
}-->

```json
{
  "allowExternalSenders": true,
  "autoSubscribeNewMembers": true,
  "description": "string",
  "displayName": "string",
  "groupTypes": ["string"],
  "id": "string (identifier)",
  "isSubscribedByMail": true,
  "mail": "string",
  "mailEnabled": true,
  "mailNickname": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "string",
  "onPremisesSyncEnabled": true,
  "proxyAddresses": ["string"],
  "securityEnabled": true,
  "unseenCount": 1024,
  "visibility": "string",
  "acceptedSenders": [ { "@odata.type": "microsoft.graph.directoryObject"} ],
  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "conversations": [ { "@odata.type": "microsoft.graph.conversation" }],
  "createdOnBehalfOf": { "@odata.type": "microsoft.graph.directoryObject" },
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [ { "@odata.type": "microsoft.graph.event" }],
  "memberOf": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "members": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "owners": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "rejectedSenders": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "threads": [ { "@odata.type": "microsoft.graph.conversationThread" }]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
