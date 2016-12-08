# <a name="subscription-resource-type"></a>Abonnement Ressourcentyp
Ein Abonnement ermöglicht eine Client-app zum Empfangen von Benachrichtigungen zu Daten auf das Microsoft Graph. Abonnements werden derzeit für die folgenden Datasets aktiviert:

1. E-Mail-Nachrichten, Ereignisse und Kontakte aus Outlook
1. Unterhaltungen aus Office-Gruppen.
1. Laufwerk Stammelemente aus OneDrive 


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.subscription"
}-->

```json
{
  "changeType": "string",
  "notificationUrl": "string",
  "resource": "string",
  "expirationDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "clientState": "string",
}

```
## <a name="properties"></a>Eigenschaften

| Eigenschaft           | Typ           | Beschreibung                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| changeType         | string         | Gibt den Typ der Änderung in der abonnierten Ressource, die eine Benachrichtigung auslösen wird. Die unterstützten Werte sind: `created`, `updated`, `deleted`. Mehrere Werte können eine durch Trennzeichen getrennte Liste mit kombiniert werden. Laufwerk Root Element Benachrichtigungen erfordern die Verwendung von `updated` nur.                                                                                                                                                 |
| notificationUrl    | string         | Die URL des Endpunkts, die Benachrichtigungen erhalten werden. Nutzen Sie die HTTPS muss diese URL Protocol.                                                                                                                                                                                                                                                     |
| Ressource           | string         | Gibt die Ressource, die für Änderungen überwacht werden. Enthalten nicht die base-URL (`https://graph.microsoft.com/<version>/`).                                                                                                                                                                                                                               |
| expirationDateTime | DateTimeOffset | Gibt an, Datum und Uhrzeit, wenn das Abonnement Webhook abgelaufen ist. Die Zeit in UTC ist und eine bestimmte Zeitspanne aus Abonnement erstellen, die unterschiedlich für die Ressource abonniert werden kann.  Finden Sie in der folgenden Tabelle ein Maximalwert.                                                                                                                              |
| clientState        | string         | Gibt den Wert der `clientState` Eigenschaft vom Dienst in jeder Benachrichtigung gesendet. Die maximale Länge beträgt 255 Zeichen. Der Client kann überprüfen, dass der Wert der verglichen des Diensts die Benachrichtigung stammt der `clientState` gesendet werden, mit dem Abonnement mit dem Wert der Eigenschaft der `clientState` Eigenschaft, die mit jeder Benachrichtigung empfangen wurden. |
| id                 | string         | Eindeutiger Bezeichner für das Abonnement. Schreibgeschützt.                                                                                                                                                                                                                                                                                                               |

## <a name="maximum-expiration-times-per-resource"></a>Maximale Ablauf Mal pro Ressource

| Ressource            | Maximale Ablaufzeit |
|:--------------------|:------------------------|
| E-Mails                | 4230 Minuten.           |
| Kalender            | 4230 Minuten.           |
| Kontakte            | 4230 Minuten.           |
| Gruppe Unterhaltungen | 4230 Minuten.           |
| Laufwerk Stammelemente    | 86400 Minuten.          |


## <a name="relationships"></a>Beziehungen
Keine


## <a name="methods"></a>Methoden

| Methode                                                           | Rückgabetyp                     | Beschreibung                                                                                   |
|:-----------------------------------------------------------------|:--------------------------------|:----------------------------------------------------------------------------------------------|
| [Abonnement erstellen](../api/subscription_post_subscriptions.md) | [Abonnement](subscription.md) | Abonniert Listener-Anwendung zum Empfangen von Benachrichtigungen, wenn Microsoft Graph-Daten geändert. |
| [Update-Abonnement](../api/subscription_update.md)             | [Abonnement](subscription.md) | Erneuern eines Abonnements durch den Ablaufzeitpunkt aktualisieren.                                         |
| [Erhalten-Abonnement](../api/subscription_get.md)                   | [Abonnement](subscription.md) | Lesen Sie Eigenschaften und Beziehungen Abonnement-Objekts.                                     |
| [Löschen von Abonnements](../api/subscription_delete.md)             | Keine                            | Löscht ein Abonnementobjekt.                                                                 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "subscription resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
