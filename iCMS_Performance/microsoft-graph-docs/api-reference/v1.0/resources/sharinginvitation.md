# <a name="sharinginvitation-resource-type"></a>Ressourcentyp sharingInvitation

Stellt Informationen über eine freigabeeinladung für einen Satz von Berechtigungen. Dieses Objekt ist schreibgeschützt.


## <a name="properties"></a>Eigenschaften

| Name der Eigenschaft  | Typ                          | Beschreibung                                                                                                                   |
|:---------------|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| E-Mail          | String                        | Die e-Mail-Adresse für den Empfänger die Einladung zur Freigabe bereitgestellt. Schreibgeschützt.                                          |
| invitedBy      | [identitySet](identityset.md) | Enthält Informationen zu den Absender der Einladung, das diese Berechtigung erstellt, sofern diese Information verfügbar ist. Schreibgeschützt. |
| signInRequired | Boolean                       | Wenn `true` der Empfänger der Einladung anmelden, um das freigegebene Element zugreifen muss. Schreibgeschützt.                     |

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sharingInvitation"
}-->

```json
{
  "email": "string",
  "redeemedBy": "string",
  "signInRequired": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharingInvitation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
