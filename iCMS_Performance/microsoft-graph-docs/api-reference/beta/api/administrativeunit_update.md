# <a name="update-administrativeunit"></a>Administrativeunit aktualisieren

Aktualisieren Sie die Eigenschaften eines [AdministrativeUnit](../resources/administrativeunit.md) -Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /administrativeUnits/<id>
```
## <a name="optional-request-headers"></a>Optional Anforderungsheader
## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer <token>. Erforderlich.|

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind verwalten ihre vorherigen Werte oder neu berechnet auf der Grundlage Änderungen an andere Eigenschaftswerte werden. Für eine optimale Leistung sollten nicht Sie vorhandene Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|description|string|Beschreibung für die administrative Einheit.|
|displayName|string|Der Anzeigename für die administrative Einheit.|
|visibility|string|Sichtbarkeit für die administrative Einheit. Wenn dies nicht der Standardwert ist "public". Kann auf "HiddenMembership", das die Mitgliedschaft von nicht-Mitglieder verbirgt festgelegt werden.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und aktualisierte [AdministrativeUnit](../resources/administrativeunit.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_administrativeunit"
}-->
```http
PATCH https://graph.microsoft.com/beta/administrativeUnits/<id>
Content-type: application/json
Content-length: 114

{
  "displayName": "displayName-value",
  "description": "description-value",
  "visibility": "visibility-value"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.administrativeunit"
} -->
```http
HTTP/1.1 204 No content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update administrativeunit",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->