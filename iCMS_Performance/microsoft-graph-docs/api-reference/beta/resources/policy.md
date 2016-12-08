# <a name="policy-resource-type"></a>richtlinienressourcentyp

Stellt eine Azure AD-Richtlinie. Richtlinien sind benutzerdefinierte Regeln, die auf Applications, Service Prinzipale, Gruppen oder der gesamten Organisation, den, der Sie zugewiesen sind, erzwungen werden können. Derzeit ist nur ein Typ der Richtlinie verfügbar:
- Token Richtlinien für die Gültigkeitsdauer: Gibt an, die Lebensdauer Dauer der VBA-und Dienstprinzipale ausgestellten Token

Mit dieser Richtlinie wird ausführlich beschrieben.

### <a name="methods"></a>Methoden
| Methode       | Rückgabetyp  |Beschreibung|
|:---------------|:--------|:----------|
| [Abrufen von Gruppenrichtlinien](../api/policy_get.md) |Richtlinie|Lesen Sie Eigenschaften und Beziehungen des Benutzerobjekts.|
|[Richtlinie erstellen](../api/policy_post.md)|Richtlinie|Erstellen Sie ein neues Gruppenrichtlinienobjekt.|
|[Update-Richtlinie](../api/policy_update.md)|Keine|Group Policy Object zu aktualisieren.|
|[Löschrichtlinie](../api/policy_delete.md)|Keine|Löschen Sie Richtlinienobjekt.|
|[Zuweisen der Richtlinie](../api/policy_assign.md)|Keine|Zuweisen einer Richtlinie zu einer Anwendung Dienstprinzipal.|
|[Listenrichtlinien](../api/policy_list.md)|Auflistung von Gruppenrichtlinien|Rufen Sie aller Gruppenrichtlinienobjekte in der Organisation ab.|
|[Zugewiesen-Listenrichtlinien](../api/policy_list_assigned.md)|Auflistung von Gruppenrichtlinien|Rufen Sie alle Richtlinienobjekte an eine Anwendung oder Dienstprinzipal zugewiesen.|


### <a name="common-properties"></a>Allgemeine Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Definition|String|Die Version der bestimmte Richtlinie Zeichenfolge. Finden Sie weiter unten. Erforderlich.|
|displayName|String|Ein benutzerdefinierter Name für die Richtlinie ein. Erforderlich.|
|IsOrganizationDefault|Boolean|Wenn auf true ist, wird diese Richtlinie aktiviert festgelegt. Viele Richtlinien für die gleichen Richtlinientyp kann, jedoch nur eine unverändert Organisation aktiviert werden kann. Optional, wird Standardwert "false".|
|Typ|String|Gibt den Typ der Richtlinie an. Derzeit muss "TokenLifetimePolicy". Erforderlich.|

#### <a name="common-relationships"></a>Allgemeine Beziehungen
|Beziehung|Typ|Beschreibung|
|:-------------|:-----------|:-----------|
|appliesTo|[DirectoryObject](../resources/directoryObject.md) -Auflistung|Die Anwendungen, Dienstprinzipale, Gruppen oder Organisation wird die Richtlinie betrifft.|

## <a name="token-lifetime-policy"></a>Gültigkeitsdauer von Token-Richtlinie
Gibt die Lebensdauer der für verschiedene Zwecke ausgestellten Token. Diese Art der Richtlinie kann Anwendungen und Dienstprinzipale [zugewiesen](../api/policy_assign.md) sein. Es gibt vier Arten von Token, deren Lebensdauer konfiguriert werden können. Access/aktualisieren token-Paare werden während der Authentifizierung über einen Client abgerufen, während die ID-Sitzung token-Paare während der Authentifizierung über einen Browser abgerufen werden.

- **Access-Token** enthält Informationen über die Identität und die Berechtigungen für ein Benutzerkonto, das Zugriff auf geschützte Ressourcen wie Anwendungen von Clients verwendet wird.
- **Token aktualisieren** wird zusammen mit der Zugriffstoken abgerufen, wenn ein Benutzer mit Azure AD über einen Client Zugriff auf eine geschützte Ressource authentifiziert. Während es ist nicht gesperrt oder nicht verwendete von für mehr als die MaxInactiveTime (siehe unten links), können sie ein neues Access/aktualisieren Paar token erhalten, wenn das aktuelle Zugriffstoken läuft ab verwendet werden.
- **Token-ID** verhält sich wie ein Zugriffstoken, jedoch über den Browser abgerufen.
- **Sitzung Token** verhält sich wie ein Aktualisierungstoken, aber über den Browser abgerufen.

#### <a name="properties"></a>Eigenschaften
Die folgenden Eigenschaften bilden das JSON-Objekt, das eine Richtlinie Gültigkeitsdauer von token darstellt. Diese JSON-Objekt muss **in eine Zeichenfolge mit Anführungszeichen Escapezeichen konvertiert** in der Eigenschaft "Definition" allgemeine Richtlinie eingefügt werden soll. Ein Beispiel ist unten aufgeführt:

>Hinweis: Es werden alle Zeitdauern in diese Eigenschaften im Format "TT.hh" angegeben.

>Hinweis: Max-Werte für Eigenschaften in "Tagen" gekennzeichnet sind 1 Sekunde kleiner als die bezeichnet Anzahl von Tagen. Beispielsweise wird der maximale Wert von 1 Tagen angegeben, als "23: 59:59".

| Eigenschaft     | Typ   |Beschreibung| Mindestwert | Max-Wert | Standardwert|
|:---------------|:--------|:----------|:--------|:--------|:----|
|AccessTokenLifetime|String|Steuert, wie lange **Zugriff und ID-Token** als gültig betrachtet werden.|10 Minuten|1 Tag|1 Stunde|
|MaxInactiveTime|String|Steuert, wie ALT ein Aktualisierungstoken sein kann, bevor ein Client nicht mehr zum Abrufen eines neuen Access/aktualisieren token Paars Zugriff auf eine Ressource verwenden kann.|10 Minuten|90 Tage|14 Tage|
|MaxAgeSingleFactor|String|Steuerelemente wie lange kann Benutzer weiterhin Aktualisierungstoken verwenden, um neue Access/aktualisieren abzurufen token-Paare nach dem letzten Mal, das Sie authentifiziert, erfolgreich mit nur einem einzigen Faktor. Da einfache weniger als mehrstufige Authentifizierung sicher angesehen wird, wird empfohlen, dass diese Richtlinie auf einen Wert gleich oder kleiner als der MultiFactorRefreshTokenMaxAge festgelegt ist.|10 Minuten|erst gesperrt|365 Tage oder erst gesperrt|
|MaxAgeMultiFactor|String|Aktualisierungstoken verwenden, um neue Access/aktualisieren abzurufen token-Paare nach dem letzten Mal, das Sie authentifiziert, erfolgreich mit mehreren Faktoren kann Steuerelemente wie lange ein Benutzer weiterhin.|10 Minuten|erst gesperrt|365 Tage oder erst gesperrt|
|MaxAgeSessionSingleFactor|String|Steuerelemente wie lange kann Benutzer weiterhin Sitzungstoken verwenden, um neue ID-Sitzung-Token abzurufen, nach dem Zeitpunkt der letzten sie mit nur einem einzigen Faktor erfolgreich authentifiziert. Da einfache weniger als mehrstufige Authentifizierung sicher angesehen wird, wird empfohlen, dass diese Richtlinie auf einen Wert gleich oder kleiner als der MultiFactorSessionTokenMaxAge festgelegt ist|10 Minuten|erst gesperrt|365 oder erst gesperrt|
|MaxAgeSessionMultiFactor|String|Steuerelemente wie lange kann Benutzer weiterhin Sitzungstoken verwenden, um neue ID-Sitzung Token nach dem Zeitpunkt der letzten abrufen, die sie mit mehreren Faktoren erfolgreich authentifiziert.|10 Minuten|erst gesperrt|365 oder erst gesperrt|
|Version|Integer|Der Wert 1 festgelegt. Erforderlich.|Keine|Keine|Keine|

### <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

```json
{
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\",\"MaxInactiveTime\":\"20:00:00\",}}"],
  "displayName":"Test Policy",
  "isOrganizationDefault":false,
  "type":"TokenLifetimePolicy",
}
```
