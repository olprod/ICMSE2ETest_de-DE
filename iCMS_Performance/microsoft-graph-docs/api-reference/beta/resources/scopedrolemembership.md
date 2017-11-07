# <a name="scopedrolemembership-resource-type"></a>Ressourcentyp scopedRoleMembership

Eine Mitgliedschaft in Datenbankrolle bereichsbezogenen beschreibt des Benutzers Mitgliedschaft einer Directory-Rolle, die weiter zu einer administrativen Unit (AU) ausgelegt ist.  Dies bietet einen Mechanismus, um einen Mandanten gesamte Unternehmen Adminsistrator delegieren Administratorrechte verfügen, um einem Benutzer das Verwalten von Benutzern und Gruppen in einer Teilmenge der Organisation (der Teilmenge von einer AU definiert wird) zu ermöglichen. 

## <a name="methods"></a>Methoden
Direkte Abfragen an diese Ressource werden nicht unterstützt.  Finden Sie im Thema [Administrative Einheiten](administrativeunit.md) zu Informationen zum Abfrage für bezogenen Rollenmitgliedschaften sowie hinzufügen und Entfernen von bezogenen-Rollenmitgliedschaften finden Sie unter. 

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|administrativeUnitId|string|Eindeutiger Bezeichner für die administrative Einheit, der die Directory-Rolle zugeordnet ist|
|id|string| Eindeutiger Bezeichner für die Mitgliedschaft bezogenen-Rolle. Schreibgeschützt.|
|roleId|string| Eindeutiger Bezeichner für die Directory-Rolle, der in der Member ist.|
|roleMemberInfo|[identityInfo](identityinfo.md)| Rolle Mitglied Identitätsinformationen, die den Benutzer, der Mitglied dieser bezogenen-Rolle ist darstellen.|

## <a name="relationships"></a>Beziehungen
Keine


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.scopedrolemembership"
}-->

```json
{
  "administrativeUnitId": "string",
  "id": "string (identifier)",
  "roleId": "string",
  "roleMemberInfo": {"@odata.type": "microsoft.graph.identityInfo"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "scopedRoleMembership resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->