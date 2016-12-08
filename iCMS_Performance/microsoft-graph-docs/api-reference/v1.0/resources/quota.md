# <a name="quota-resource-type"></a>Kontingent Ressourcentyp

Die Ressource **Kontingent** finden Sie Informationen über Laufwerk Kontingent.



## <a name="properties"></a>Eigenschaften

| Name der Eigenschaft | Typ   | Beschreibung                                                                 |
|:--------------|:-------|:----------------------------------------------------------------------------|
| insgesamt         | Int64  | Zulässige Speicherplatz in Byte. Schreibgeschützt.                           |
| verwendet          | Int64  | Gesamte Speicherplatz verwendet wird, in Byte. Schreibgeschützt.                                      |
| verbleibenden     | Int64  | Insgesamt Speicherplatz vor dem Erreichen der Kontingentgrenze in Byte. Schreibgeschützt. |
| gelöscht       | Int64  | Gesamtkapazität Identitätsdaten durch Dateien im Papierkorb in Byte. Schreibgeschützt.      |
| Zustand         | string | -Enumerationswert ab, der den Status des Speicherplatzes angibt. Schreibgeschützt. |



## <a name="state-enumeration"></a>State-Aufzählung

| Wert      | Beschreibung                                                                                                                                                                 |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `normal`   | Das Laufwerk kann viel verbleibende Quote links aus.                                                                                                                               |
| `nearing`  | Verbleibende Quote ist weniger als 10 % des Speicherplatzes Gesamtkontingent.                                                                                                                      |
| `critical` | Verbleibende Quote ist kleiner als 1 % des Speicherplatzes Gesamtkontingent.                                                                                                                       |
| `exceeded` | Das verwendete Kontingent hat das Gesamtkontingent überschritten. Neue Dateien und Ordner können nicht hinzugefügt werden auf dem Laufwerk, bis es unter dem Betrag Gesamtkontingent oder mehr Speicherplatz zur Verfügung erworben. |


## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.quota"
}-->

```json
{
  "deleted": 1024,
  "remaining": 1024,
  "state": "normal | nearing | critical | exceeded",
  "total": 1024,
  "used": 1024
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "quota resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
