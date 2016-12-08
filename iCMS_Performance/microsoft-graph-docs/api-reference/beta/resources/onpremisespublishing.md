# <a name="onpremisespublishing-resource-type"></a>Ressourcentyp onPremisesPublishing




## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|customDomainCertificate|String|Details des Zertifikats mit der Anwendung verbunden sind, wenn eine benutzerdefinierte Domäne verwendet wird. NULL, wenn die Standarddomäne zu verwenden.|
|externalAuthenticationType|String|Details der Vorauthentifizierung-Einstellung für die Anwendung möglichen Werte sind: `passthru`, `aadPreAuthentication`.|
|externalUrl|String|Die veröffentlichten externe Url für die Anwendung. Beispielsweise https://intranet-contoso.msappproxy.net/  |
|internalUrl|String|Die interne Url der Anwendung. Beispielsweise http://intranet/|
|isOnPremPublishingEnabled|Boolean|Gibt an, ob die Anwendung derzeit oder nicht veröffentlicht wird.|
|isTranslateHostHeaderEnabled|Boolean|Gibt an, ob die Anwendung Urls in der Antwort-Headern übersetzen sollten. Dies beinhaltet das Festlegen der richtigen Website für Cookies.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.onPremisesPublishing"
}-->

```json
{
  "customDomainCertificate": "String",
  "externalAuthenticationType": "String",
  "externalUrl": "String",
  "internalUrl": "String",
  "isOnPremPublishingEnabled": true,
  "isTranslateHostHeaderEnabled": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "onPremisesPublishing resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->