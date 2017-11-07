# <a name="administrativeunit-resource-type"></a>Ressourcentyp administrativeUnit

Eine administrative Einheit stellt einen konzeptionellen Container für Benutzer- und Verzeichnisobjekte. Verwenden von administrativen Einheiten, ein Unternehmensadministrator delegieren kann jetzt administrative Aufgaben zum Verwalten von Benutzern und Gruppen innerhalb oder auf eine administrative Einheit an einen Administrator regionalen oder auf Abteilungsebene bereichsbezogenen. 

Sehen wir uns ein Beispiel. Angenommen Sie, Contoso Corp aus zwei Abschnitte - Division Süd und eine Division Nord besteht. Verzeichnis Rollen bei Contoso sind auf den gesamten Mandanten beschränkt. Kelly einer Unternehmens-Administrator von Contoso möchte Verwaltungsaufgaben delegieren, aber die Division Süd oder die Division Nord festlegen.  Kelly kann *Süd Admistrative Einheit* erstellt und alle Süd Benutzer in dieser administrative Einheit platzieren.  Ebenso kann Kelly eine *Nord administrative Einheit*erstellen.  Nun können Kelly, starten Delegieren von Verwaltungsaufgaben an andere Personen, aber in die neuen administrativen Einheiten **bezogenen** er erstellt wird. Kelly platziert zur Verfügung, in eine *Helpdeskadministrator* Rolle **als Bereich** der *Süd administrative Einheit*.  Dadurch wird zur Verfügung, Kennwort des Benutzers, aber nur, wenn diese Benutzer in der *Süd administrative Einheit*sind zurücksetzen.  In ähnlicher Weise platziert Kelly Dave in einen *Benutzer Kontoadministrator* Rolle **bezogenen** zur *Nord administrative Einheit*.  Dies ermöglicht Dave Benutzer aktualisieren, Zuweisen von Lizenzen und Zurücksetzen des Kennworts des Benutzers, aber nur, wenn die Benutzer in der *Nord administrative Einheit sind*. Video mit einer Übersicht finden Sie unter [Einführung in Azure Active Directory Administrative Einheiten](https://channel9.msdn.com/Series/Windows-Azure-Active-Directory/Introduction-to-Azure-Active-Directory-Administrative-Units).

Dieses Thema enthält eine Beschreibung der deklarierte Eigenschaften und Navigationseigenschaften verfügbar gemacht werden, durch die AdministrativeUnit-Entität als auch die Vorgänge und Funktionen, die für die Ressource AdministrativeUnits aufgerufen werden können.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Erstellen von administrativeUnit](../api/administrativeunit_post_administrativeunits.md) | [administrativeUnit](administrativeunit.md) | Erstellen Sie eine neue administrative Einheit.|
|[Liste administrativeUnits](../api/administrativeunit_list.md) | [AdministrativeUnit](administrativeunit.md) -Auflistung |Aller AdministrativeUnits-Listeneigenschaften.|
|[Abrufen von administrativeUnit](../api/administrativeunit_get.md) | [administrativeUnit](administrativeunit.md) |Lesen Sie Eigenschaften und die Beziehungen eines bestimmten AdministrativeUnit-Objekts.|
|[Aktualisieren adminstrativeUnit](../api/administrativeunit_update.md) | [administrativeUnit](administrativeunit.md)  |AdministrativeUnit-Objekt zu aktualisieren. |
|[AdminstrativeUnit löschen](../api/administrativeunit_delete.md) | Keine |AdministrativeUnit-Objekt zu löschen. |
|[Hinzufügen eines Mitglieds](../api/administrativeunit_post_members.md) |[directoryObject](directoryObject.md)| Fügen Sie ein Mitglied (Benutzer oder Gruppe).|
|[Mitglieder der Liste](../api/administrativeunit_list_members.md) |[DirectoryObject](directoryObject.md) -Auflistung| Rufen Sie die Liste der Elemente (Benutzer und Gruppen).|
|[Abrufen eines Elements](../api/administrativeunit_get_members.md) |[directoryObject](directoryObject.md)| Rufen Sie ein bestimmtes Element.|
|[Entfernen eines Mitglieds](../api/administrativeunit_delete_members.md) |[directoryObject](directoryObject.md)| Entfernen eines Mitglieds.|
|[Administrator bezogenen Rolle hinzufügen](../api/administrativeunit_post_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| Fügen Sie ein Administrator bezogenen-Rolle hinzu.|
|[Liste bezogenen Rolle Administratoren](../api/administrativeunit_list_scopedadministrators.md) |[ScopedRoleMembership](scopedrolemembership.md) -Auflistung| Rufen Sie die Liste der Administratoren bezogenen-Rolle.|
|[Einen Administrator bezogenen Rolle abrufen](../api/administrativeunit_get_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| Rufen Sie einen bestimmten bezogenen-Role-Administrator.|
|[Entfernen einer bezogenen Rolle Administrators](../api/administrativeunit_delete_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| Einen Administrator bezogenen Rolle zu entfernen.|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|description|string|Eine optionale Beschreibung für die administrative Einheit.|
|displayName|string|Der Anzeigename für die administrative Einheit.|
|id|string|Eindeutiger Bezeichner für die administrative Einheit. Schreibgeschützt.|
|visibility|string|Steuert, ob die administrative Einheit und seine Member ausgeblendet sind oder öffentlich. Kann auf HiddenMembership oder öffentlichen festgelegt sein. Wenn nicht festgelegt, Standardverhalten öffentlich. Bei Festlegung auf HiddenMembership, können nur Mitglieder der administrative Einheit andere Mitglieder der administrative Einheit anbieten.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Member|[DirectoryObject](directoryObject.md) -Auflistung|Benutzer und Gruppen, die Mitglieder dieser Adminsitrative Einheit sind. HTTP-Methoden: ABRUFEN (Listenmitglieder) POST (Mitglieder hinzufügen), DELETE (Entfernen von Mitgliedern).|
|scopedAdministrators|[ScopedRoleMembership](scopedrolemembership.md) -Auflistung| Bereichsbasierte Administratoren dieser Administrative Einheit.  HTTP-Methoden: ABRUFEN (Liste ScopedRoleMemberships), POST (ScopedRoleMembership hinzufügen), DELETE (Entfernen ScopedRoleMembership). |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.administrativeunit"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "visibility": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "administrativeUnit resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->