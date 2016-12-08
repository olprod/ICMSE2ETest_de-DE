# <a name="update-extensionproperty"></a>Extensionproperty aktualisieren

Aktualisieren Sie die Eigenschaften des Extensionproperty-Objekts.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, diese API ausführen: 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
PATCH /applications/<id>/extensionProperties/<id>
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:-----------|:------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung die Werte für die entsprechenden Felder, die aktualisiert werden soll. Vorhandene Eigenschaften, die nicht im Textkörper Anforderung enthalten sind werden ihre vorherigen Werte verwalten oder neu berechnet basierend auf Änderungen an andere Eigenschaftswerte sein. Für eine optimale Leistung sollte nicht Sie vorhandene Werte enthalten, die nicht geändert haben.

| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|appDisplayName|String|            |
|Datentyp|String|Gibt den Typ des hinzuzufügenden Directory Extension-Eigenschaft.   Typen werden unterstützt: ganze Zahl, LargeInteger, DateTime (muss angegeben werden im ISO 8601 - DateTime in UTC gespeichert ist), Binary, Boolean und Zeichenfolge.|
|isSyncedFromOnPremises|Boolean|Gibt an, ob die Extension-Eigenschaft aus dem lokalen lokalen Verzeichnis synchronisiert ist.                            **Notes**: nicht auf NULL festgelegt.            |
|name|String|Gibt den Anzeigenamen für das Verzeichnis Extension-Eigenschaft.                            **Notes**: nicht auf NULL festgelegt.            |
|targetObjects|String|Die Directory-Objekte, die die Directory Extension-Eigenschaft hinzugefügt wird.  Unterstützte Directory Entitäten, die erweitert werden können, sind: "User", "Group", "Organisation", "Gerät", "Anwendung" und "ServicePrincipal" **Notes**: nicht auf NULL festgelegt.            |

## <a name="response"></a>Antwort
Wenn erfolgreich ist, diese Methode gibt einen `200 OK` Antwortcode und aktualisierte [ExtensionProperty](../resources/extensionproperty.md) -Objekts in der Antworttext.
## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "update_extensionproperty"
}-->
```http
PATCH https://graph.microsoft.com/beta/applications/<id>/extensionProperties/<id>
Content-type: application/json
Content-length: 188

{
  "appDisplayName": "appDisplayName-value",
  "name": "name-value",
  "dataType": "dataType-value",
  "isSyncedFromOnPremises": true,
  "targetObjects": [
    "targetObjects-value"
  ]
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Antwortobjekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.extensionproperty"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 208

{
  "appDisplayName": "appDisplayName-value",
  "name": "name-value",
  "dataType": "dataType-value",
  "isSyncedFromOnPremises": true,
  "targetObjects": [
    "targetObjects-value"
  ],
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update extensionproperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->