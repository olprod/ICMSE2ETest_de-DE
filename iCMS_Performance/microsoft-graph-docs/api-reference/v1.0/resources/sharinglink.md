# <a name="sharinglink-resource-type"></a>Ressourcentyp sharingLink

Enthält Informationen für ein Element eine Freigabe Verknüpfung.


## <a name="properties"></a>Eigenschaften

| Eigenschaft    | Typ                    | Beschreibung                                                                                                                                                                                             |
|:------------|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| application | [Identität](identity.md) | Die app den Link zugeordnet ist.                                                                                                                                                                    |
| Typ        | String                  | Der Typ der Verknüpfung erstellt.                                                                                                                                                                           |
| Bereich       | String                  | Der Bereich der von dieser Berechtigung dargestellte Verknüpfung. Wert `anonymous` gibt an, die Verknüpfung kann durch jeden Benutzer verwendet werden `organization` gibt an, der Link kann nur für Benutzer angemeldet haben den gleichen Mandanten verwendet werden. |
| webUrl      | String                  | Eine URL, die das Element im Browser auf der OneDrive-Website wird geöffnet.                                                                                                                                       |


## <a name="type-enumeration"></a>Typ-Aufzählung

Die folgende Tabelle sind die möglichen Werte für die **Type** -Eigenschaft definiert:

| Wert   | Funktion    | Beschreibung                                                                     |
|:--------|:--------|:--------------------------------------------------------------------------------|
| `view`  | `read`  | Leserechten Freigabe Link, schreibgeschützten Zugriff zulassen.                            |
| `edit`  | `write` | Eine Änderung Freigabe Link, Lese-/ Schreibzugriff zulassen.                               |

## <a name="scope-enumeration"></a>Bereichs-Aufzählung

| Wert          | Beschreibung                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `anonymous`    | Der Freigabe Link ist für alle Benutzer verwenden verfügbar.                                                                            |
| `organization` | Der Freigabe Link ist verfügbar für jede Person in derselben Organisation (Mandant) verwendet. Nicht verfügbar für OneDrive persönlich. |


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "application", "scope" ],
  "@odata.type": "microsoft.graph.sharingLink"
}-->

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "type": "view | edit",
  "scope": "anonymous | organization",
  "webUrl": "url"
}
```



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharingLink resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
