# <a name="shared-resource-type"></a>freigegebene Ressource-Typ

Gibt an, dass ein Element für andere Personen freigegeben wurde. Enthält Informationen, wie das Element freigegeben werden.

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Typ                          | Beschreibung                                                                                        |
|:---------|:------------------------------|:---------------------------------------------------------------------------------------------------|
| Besitzer    | [IdentitySet](identityset.md) | Die Identität des Besitzers des freigegebenen Elements. Schreibgeschützt.                                           |
| Bereich    | String                        | Gibt den Bereich des wie das Element freigegeben werden: `anonymous`, `organization`, oder `users`. Schreibgeschützt. |

## <a name="scope-values"></a>Bereichswerte

| Wert        | Beschreibung                                                                           |
|:-------------|:--------------------------------------------------------------------------------------|
| Öffentliche       | Das Element wird mithilfe eines Links, das für alle Benutzer mit den Link funktioniert gemeinsam genutzt.               |
| Organisation | Das Element wird mithilfe eines Links, das für alle Benutzer in den Besitzer Organisation arbeitet gemeinsam genutzt. |
| Benutzer        | Das Element ist für bestimmte Benutzer nur freigegeben.                                          |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.shared"
}-->
```json
{
  "owner": {"@odata.type": "microsoft.graph.identitySet"},
  "scope": "public | organization | users"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "shared resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
