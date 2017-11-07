# <a name="update-user"></a>Benutzer aktualisieren

Aktualisieren Sie die Eigenschaften des Benutzerobjekts an.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** zum Ausführen diese API ist erforderlich: *User.ReadWrite; User.ReadWrite.All; Directory.ReadWrite.All*

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
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden die vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandenen Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Mich-Seite|String|Eine Freihandform Texteingabefeld für den Benutzer selbst beschreiben.|
|accountEnabled|Boolean| **true** Wenn das Konto aktiviert ist. anderenfalls **false**. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. $Filter unterstützt.    |
|assignedLicenses|[AssignedLicense](../resources/assignedlicense.md) -Auflistung|Die Lizenzen, die der Benutzer zugewiesen sind. Nicht NULL-Werte zulässt.            |
|Geburtsdatum|DateTimeOffset|Das Geburtsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Ort|String|Stadt ein, in denen der Benutzer befindet. $Filter unterstützt.|
|Land|String|Das Land/Region in das sich der Benutzer befindet; "USA" oder "UK". $Filter unterstützt.|
|Abteilung|String|Der Name für die Abteilung an, in der der Benutzer arbeitet. $Filter unterstützt.|
|displayName|String|Der Name im Adressbuch für den Benutzer angezeigt. Dies ist in der Regel die Kombination aus den Vornamen des Benutzers, mittleren ersten und letzten Namen. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt und kann nicht während des Updates deaktiviert werden. Unterstützt $filter und $orderby.|
|Vorname|String|Dem angegebenen Namen (Vorname) des Benutzers. $Filter unterstützt.|
|hireDate|DateTimeOffset|Das Einstellungsdatum des Benutzers. Der Zeitstempeltyp stellt Informationen zum Datum und Uhrzeit mit ISO 8601-Format dar und ist immer in UTC-Zeit. Beispielsweise würde Uhr UTC auf 1 Jan 2014 sieht folgendermaßen aus:`'2014-01-01T00:00:00Z'`|
|Interessen|String-Auflistung|Eine Liste der Benutzer ihre Interessen zu beschreiben.|
|jobTitle|String|Position des Benutzers. $Filter unterstützt.|
|mailNickname|String|Der e-Mail-Alias des Benutzers. Diese Eigenschaft muss angegeben werden, wenn ein Benutzer erstellt wird. $Filter unterstützt.|
|mobilePhone|String|Die Anzahl der primären Mobiltelefon für den Benutzer.|
|MeineWebsite|String|Die URL für den Benutzer persönliche Websites.|
|officeLocation|String|Der Standort des Büros des Benutzers direkt Unternehmens.|
|onPremisesImmutableId|String|Diese Eigenschaft wird verwendet, um eine lokale Active Directory-Benutzerkonto in ihrer Azure AD-Benutzerobjekt zuordnen. Diese Eigenschaft muss angegeben werden, wenn ein neues Benutzerkonto im Diagramm erstellen, wenn Sie eine verbunddomäne für die Benutzereigenschaft **UserPrincipalName** (UPN) verwenden. **Wichtig:** Die **$** **_** Zeichen verwendet werden, wenn Sie diese Eigenschaft festlegen. $Filter unterstützt.                            |
|passwordPolicies|String|Gibt die Kennwortrichtlinien für den Benutzer an. Dieser Wert ist eine Enumeration mit einem möglichen Wert wird "DisableStrongPassword", dem schwächere Kennwörter als die Standardrichtlinie angegeben werden kann. "DisablePasswordExpiration" kann auch angegeben werden. Die beiden können zusammen angegeben werden; Beispiel: "DisablePasswordExpiration, DisableStrongPassword".|
|passwordProfile|[PasswordProfile](../resources/passwordprofile.md)|Gibt das Kennwort Profil für den Benutzer. Das Profil enthält das Kennwort des Benutzers. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Das Kennwort im Profil muss als von der **PasswordPolicies** -Eigenschaft angegebenen Mindestanforderungen erfüllen. Standardmäßig ist ein sicheres Kennwort erforderlich.|
|pastProjects|String-Auflistung|Eine Liste für den Benutzer ihre letzten Projekte aufgelistet werden.|
|postalCode|String|Die Postleitzahl für die Adresse des Benutzers. Die Postleitzahl ist spezifisch für Land/Region des Benutzers. In den USA enthält dieses Attribut die Postleitzahl.|
|preferredLanguage|String|Die bevorzugte Sprache des Benutzers. Führen Sie die ISO 639-1-Code sollte; beispielsweise "En-US".|
|preferredName|String|Den bevorzugten Namen für den Benutzer.|
|Aufgaben|String-Auflistung|Eine Liste für den Benutzer ihre Aufgaben aufgelistet werden.|
|Schulen|String-Auflistung|Eine Liste für den Benutzer zum Aufzählen der Schulen, den, die Sie teilgenommen haben.|
|Fähigkeiten|String-Auflistung|Eine Liste für den Benutzer ihre Kenntnisse aufgelistet werden.|
|Zustand|String|Bundesland oder Kanton für die Adresse des Benutzers. $Filter unterstützt.|
|streetAddress|String|Die Straße Ort des Unternehmens des Benutzers.|
|Nachname|String|Der Nachname des Benutzers (Familie oder Nachnamen). $Filter unterstützt.|
|usagelocation-Wert angegeben|String|Eine zweistelligen Ländercode (ISO 3166 der standard). Erforderlich für Benutzer, die aufgrund von gesetzliche Vorgabe So überprüfen Sie die Verfügbarkeit von Diensten in Ländern Lizenzen zugewiesen werden.  Beispiele: "US", "JP" und "GB". Nicht NULL-Werte zulässt. $Filter unterstützt.|
|userPrincipalName|String|Der Benutzerprinzipalname (UPN) des Benutzers. Der Benutzerprinzipalname ist ein Internet-Schreibweise Anmeldenamen für den Benutzer anhand der Internetstandard RFC 822. Standardmäßig sollte dies der Name des Benutzers e-Mail zuordnen. Ist das Standardformat alias@domain, wobei Domäne in den Mandanten-Auflistung der überprüften Domänen vorhanden sein. Diese Eigenschaft ist erforderlich, wenn ein Benutzer erstellt wird. Die überprüften Domänen für den Mandanten können aus der Eigenschaft **VerifiedDomains** [Organisation](../resources/organization.md)zugegriffen werden. Unterstützt $filter und $orderby.
|userType|String|Ein String-Wert, der zum Klassifizieren Benutzertypen in Ihrem Verzeichnis, beispielsweise "Members" und "Gast" verwendet werden kann. $Filter unterstützt.          |

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [Benutzer](../resources/user.md) -Objekt aus der Antwort.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_user"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me
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
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
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
