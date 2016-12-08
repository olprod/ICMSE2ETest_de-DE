# <a name="update-user"></a>Benutzer aktualisieren

Aktualisieren Sie die Eigenschaften des Benutzerobjekts an.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *User.ReadWrite; User.ReadWrite.All; Directory.ReadWrite.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /users/<id | userPrincipalName>
```
## <a name="request-headers"></a>Anforderungsheader
| Kopfzeile       | Wert|
|:-----------|:------|
| Autorisierung  | Bearer <token>. Erforderlich.  |
| Inhaltstyp  | Application/json  |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind verwalten ihre vorherigen Werte oder neu berechnet auf der Grundlage Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Mich-Seite|String|Eine Freihandform Texteingabefeld für den Benutzer selbst beschreiben.|
|accountEnabled|Boolean| **true,** Wenn das Konto aktiviert ist. anderenfalls **false**. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. $Filter unterstützt.    |
|assignedLicenses|[AssignedLicense](../resources/assignedlicense.md) -Auflistung|Die Lizenzen, die dem Benutzer zugewiesen sind. Nicht auf NULL festgelegt.            |
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Ort|String|Stadt ein, in denen der Benutzer befindet. $Filter unterstützt.|
|Land|String|Land/Region in das sich der Benutzer befindet; "USA" oder "UK". $Filter unterstützt.|
|Abteilung|String|Der Name für die Abteilung, in der der Benutzer arbeitet. $Filter unterstützt.|
|displayName|String|Der Name im Adressbuch für den Benutzer angezeigt. Dies ist in der Regel die Kombination aus den Vornamen des Benutzers, mittleren ersten und letzten Namen. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt und kann nicht während des Updates deaktiviert werden. Unterstützt $filter und $orderby.|
|Vorname|String|Dem angegebenen Namen (Vorname) des Benutzers. $Filter unterstützt.|
|hireDate|DateTimeOffset|Das Einstellungsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Uhr UTC auf 1 Jan 2014 würde beispielsweise wie folgt aussehen:`'2014-01-01T00:00:00Z'`|
|Interessen|Zeichenfolgenauflistung|Eine Liste der Benutzer ihre Interessen zu beschreiben.|
|jobTitle|String|Position des Benutzers. $Filter unterstützt.|
|mailNickname|String|E-Mail-Alias für den Benutzer. Diese Eigenschaft muss angegeben werden, wenn ein Benutzer erstellt wird. $Filter unterstützt.|
|mobilePhone|String|Die Anzahl der primären Mobiltelefon für den Benutzer.|
|MeineWebsite|String|Die URL für den Benutzer persönliche Websites.|
|officeLocation|String|Der Standort des Büros des Benutzers direkt Unternehmens.|
|onPremisesImmutableId|String|Diese Eigenschaft wird verwendet, um eine lokale Active Directory-Benutzerkontos auf ihre Azure Active Directory-Benutzerobjekt zuzuordnen. Diese Eigenschaft muss angegeben werden, wenn ein neues Benutzerkonto im Diagramm erstellen, wenn Sie eine verbunddomäne für die Benutzereigenschaft **UserPrincipalName** (UPN) verwenden. **Wichtig:** Die **$** **_** Zeichen verwendet werden, wenn Sie diese Eigenschaft festlegen. $Filter unterstützt.                            |
|passwordPolicies|String|Kennwortrichtlinien für den Benutzer angibt. Dieser Wert ist eine Enumeration mit einem möglichen Wert wird "DisableStrongPassword", wodurch schwächere Kennwörter als die Standardrichtlinie angegeben werden. "DisablePasswordExpiration" kann auch angegeben. Die beiden können zusammen angegeben werden. Beispiel: "DisablePasswordExpiration, DisableStrongPassword".|
|passwordProfile|[PasswordProfile](../resources/passwordprofile.md)|Gibt das Kennwort Profil des Benutzers. Das Profil enthält das Kennwort des Benutzers. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Das Kennwort im Profil muss als von der **PasswordPolicies** -Eigenschaft angegebenen Mindestanforderungen erfüllen. Standardmäßig ist ein sicheres Kennwort erforderlich.|
|pastProjects|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre letzten Projekte aufgelistet werden.|
|Postleitzahl|String|Die Postleitzahl für die Adresse des Benutzers. Die Postleitzahl ist spezifisch für Land/Region des Benutzers. In den USA enthält dieses Attribut die Postleitzahl.|
|preferredLanguage|String|Die bevorzugte Sprache des Benutzers. Führen Sie die ISO 639-1-Code sollte; beispielsweise "En-US".|
|preferredName|String|Den bevorzugten Namen für den Benutzer.|
|Aufgaben|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre Aufgaben aufgelistet werden.|
|Schulen|Zeichenfolgenauflistung|Eine Liste für den Benutzer zum Aufzählen der Schulen, die sie besucht haben.|
|Fähigkeiten|Zeichenfolgenauflistung|Eine Liste für den Benutzer ihre Kenntnisse aufgelistet werden.|
|Zustand|String|Bundesland oder Kanton für die Adresse des Benutzers. $Filter unterstützt.|
|streetAddress|String|Die Straße Ort des Unternehmens des Benutzers.|
|Nachname|String|Der Nachname des Benutzers (Familie oder Nachnamen). $Filter unterstützt.|
|usagelocation-Wert angegeben|String|Ein zweistelligen Ländercode (ISO 3166 standard). Erforderlich für Benutzer, die aufgrund von gesetzliche Vorgabe So überprüfen Sie die Verfügbarkeit von Diensten in Ländern Lizenzen zugewiesen werden.  Beispiele: "US", "JP" und "GB". Nicht NULL-Werte zulässt. $Filter unterstützt.|
|userPrincipalName|String|Der Benutzerprinzipalname (UPN) des Benutzers. Der Benutzerprinzipalname ist ein Internet-Schreibweise Anmeldenamen für den Benutzer anhand der Internetstandard RFC 822. Standardmäßig sollte dies der Name des Benutzers e-Mail zuordnen. Das Standardformat ist alias@domain, wobei Domäne muss vorhanden sein, in dem Mandanten Auflistung der überprüften Domänen. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Die überprüften Domänen für den Mandanten können über die **VerifiedDomains** -Eigenschaft der [Organisation](../resources/organization.md)zugegriffen werden. Unterstützt $filter und $orderby.
|userType|String|Ein String-Wert, der zum Klassifizieren Benutzertypen in Ihrem Verzeichnis, beispielsweise "Members" und "Gast" verwendet werden kann. $Filter unterstützt.          |

## <a name="response"></a>Antwort
Wenn erfolgreich, diese Methode gibt eine `200 OK` Antwortcode und aktualisierte [Benutzer](../resources/user.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_user"
}-->
```http
PATCH https://graph.microsoft.com/beta/me
Content-type: application/json
Content-length: 491

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "bea13e0c-3828-4daa-a392-28af7ff61a0f"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.user"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 491

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update user",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
