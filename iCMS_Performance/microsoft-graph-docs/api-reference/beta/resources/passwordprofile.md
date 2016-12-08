# <a name="passwordprofile-resource-type"></a>Ressourcentyp passwordProfile

Das Kennwort Profil eines Benutzers enthält. Die **PasswordProfile** -Eigenschaft der Entität [Benutzer](user.md) ist ein **PasswordProfile** -Objekt.


## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|forceChangePasswordNextSignIn|Boolean| **true,** Wenn der Benutzer muss Kennwort bei der nächsten Anmeldung ändern. andernfalls **false**. |
|password|String|Das Kennwort des Benutzers. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Können aktualisiert werden, aber der Benutzer muss das Kennwort bei der nächsten Anmeldung ändern. Das Kennwort muss gemäß der Benutzereigenschaft **PasswordPolicies** Mindestanforderungen erfüllen. Standardmäßig ist ein sicheres Kennwort erforderlich.|


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.passwordprofile"
}-->

```json
{
  "forceChangePasswordNextSignIn": true,
  "password": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "passwordProfile resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->