# <a name="worksheetprotection-resource-type"></a>Ressourcentyp WorksheetProtection

Des Schutzes von einem Blatt-Objekt darstellt.


## <a name="methods"></a>Methoden

| Methode           | Rückgabetyp    |Beschreibung|
|:---------------|:--------|:----------|
|[Abrufen von WorksheetProtection](../api/worksheetprotection_get.md) | [WorksheetProtection](worksheetprotection.md) |Lesen Sie Eigenschaften und Beziehungen des WorksheetProtection-Objekts.|
|[Schützen](../api/worksheetprotection_protect.md)|Keine|Ein Arbeitsblatt zu schützen. Es wird ausgelöst, wenn das Arbeitsblatt geschützt ist.|
|[Heben Sie den Schutz](../api/worksheetprotection_unprotect.md)|Keine|Heben Sie den Schutz eines Arbeitsblatts|

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|geschützte|boolean|Gibt an, ob das Arbeitsblatt geschützt ist.  Schreibgeschützt.|

## <a name="relationships"></a>Beziehungen
| Beziehung | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Optionen|[WorksheetProtectionOptions](worksheetprotectionoptions.md)|Schutzoptionen Blatt. Schreibgeschützt.|

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheetProtection"
}-->

```json
{
  "protected": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "WorksheetProtection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->