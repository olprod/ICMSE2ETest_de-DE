# <a name="excel-rest-api"></a>Excel-REST-API

## <a name="objects"></a>Objekte 

* [Arbeitsblatt](worksheet.md): das Worksheet-Objekt ist ein Mitglied der Worksheets-Auflistung. Worksheets-Auflistung enthält alle Worksheet-Objekte in einer Arbeitsmappe.
* [Bereich](range.md): Bereich eine Zelle, eine Zeile, eine Spalte, eine Auswahl von Zellen aus einem oder mehreren zusammenhängende Zellblöcken Zellbereich darstellt.  
* [Tabelle](table.md): stellt die Auflistung von organisierten Zellen entwickelt, die Verwaltung der Daten zu erleichtern. 
    * [TableColumn](tablecolumn.md) -Auflistung: eine Auflistung aller Spalten in einer Tabelle. 
    * [TableRow](tablerow.md) -Auflistung: eine Auflistung aller Zeilen in einer Tabelle. 
* [Diagramm](chart.md): Stellt ein Chart-Objekt in einer Arbeitsmappe, die eine visuelle Darstellung der zugrunde liegenden Daten ist.  
* [GetNamedItem](nameditem.md): Stellt einen definierten Namen für einen Bereich von Zellen oder ein Wert. Namen primitiven benannte Objekte (wie in der folgenden Typ dargestellt), range-Objekts usw..
  

In der folgenden Abschnitte enthalten wichtige programming Details im Zusammenhang mit Excel-REST-APIs.

* [Autorisierung und Bereiche](#authorization-and-scopes)
* [Die Grundlagen](#the-basics)
* [Arbeitsblatt-Vorgänge](#worksheet-operations)
* [Diagramm Vorgänge](#chart-operations)
* [Tabellenvorgänge](#table-operations)
* [Bereich Vorgänge](#range-operations)
* [Benannte Elemente](#named-items)
* [Grundlegendes zu-NULL-Werte in Excel-API](#understanding-nulls-in-excel-api)
* [Leere ein- und Ausgabe](#blank-input-and-output)
* [Unbegrenzt-Bereich](#unbounded-range)
* [Großen Bereich](#large-range)
* [Fehlerinformationen](#error-information)


## <a name="authorization-and-scopes"></a>Autorisierung und Bereiche

Der Standard, den oauth2 Autorisierung über Mechanismus verwendet basierend, gilt für Excel-APIs. Alle APIs erfordern die `Authorization: Bearer {access-token}` -HTTP-Header.   
Finden Sie im Abschnitt Autorisierung von den Dokumenten, um mehr zu erfahren.  
  

##### <a name="scopes"></a>Bereiche
Einen der folgenden Bereiche ist erforderlich, um Excel-API ausführen:

* Files.Read 
* Files.ReadWrite


## <a name="the-basics"></a>Die Grundlagen

Excel-REST-APIs ermöglichen Web- und mobilen Anwendungen zum Lesen und ändern die Arbeitsmappe, die auf den unterstützten Speicher-Plattformen (OneDrive, SharePoint usw.) gespeichert. `Workbook`(oder Excel-Datei) ist das obersten Ebene-Objekt, das für alle anderen Excel-Objekte über Beziehungen besteht aus. Eine Arbeitsmappe wird durch das Identifizieren von des Speicherorts der Datei in der URL über Laufwerk API behandelt. Beispiel:

`https://graph.microsoft.com/{version}/me/drive/items/{id}/workbook/`  
`https://graph.microsoft.com/{version}/me/drive/root:/{item-path}:/workbook/`  

Eine Reihe von Excel-Objekten (z. B. Tabelle, Bereich, Diagramm usw.) von standard REST-Schnittstellen zum Ausführen von CRUD zugegriffen werden konnte (erstellen, lesen, aktualisieren und löschen) Vorgang für die Arbeitsmappe. Beispielsweise`https://graph.microsoft.com/{version}/me/drive/items/{id}/workbook/`  
Gibt eine Auflistung von Objekten Arbeitsmappenteils der Arbeitsmappe zurück.    

#### <a name="excel-session-and-persistence"></a>Excel-Sitzung und Permanenz

Excel-APIs können in einem von zwei Modi aufgerufen werden: 

1. Persistent Sitzung: In diesem Modus werden alle Änderungen an der Arbeitsmappe (gespeicherten) beibehalten. Dies ist der normalen Modus des Vorgangs. 
2. Nicht persistent Sitzung: In diesem Modus werden keine Änderungen, die durch die API Quellspeicherort gespeichert. Excel-Back-End-Server behält stattdessen eine temporäre Kopie der Datei, die die bestimmten API Sitzung vorgenommenen Änderungen widerspiegelt. Sobald die Excel-Sitzung abgelaufen ist, sind die Änderungen verloren. Dieser Modus eignet sich für apps, die möglicherweise führen Sie die Analyse oder Ergebnis der Berechnung oder ein Diagrammbild usw. zu erhalten.; gleichzeitig keinen Einfluss auf den Dokumentstatus selbst.   

Sitzung wird dargestellt, in der API mit `workbook-session-id: {session-id}` Kopfzeile. 

_Ist die Sitzung Kopfzeile erforderlich?_ Nein. Kopfzeile der Sitzung ist nicht erforderlich für eine Excel-API zu arbeiten. Verwenden der Sitzung ist jedoch ratsam, eine bessere Leistung zu erzielen. Wenn keine Kopfzeile Sitzung verwendet wird, beibehalten während der API-Aufruf _ist_ vorgenommene Änderung an der Datei.  

#### <a name="api-call-to-get-a-session"></a>API-Aufruf eine Sitzung abgerufen. 

##### <a name="request"></a>Anforderung 

Übergeben eines JSON-Objekts durch Festlegen der `persistchanges` -Wert für `true` oder `false`. 

<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/createSession
content-type: Application/Json 
authorization: Bearer {access-token}

{ "persistChanges": true }
```

Wenn der Wert der `persistChanges` wird festgelegt `false`, eine Id für eine Sitzung nicht testenden wird zurückgegeben.  


##### <a name="response"></a>Antwort

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 201, Created
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#microsoft.graph.sessionInfo",
  "id": "{session-id}",
  "persistChanges": true
}
```

##### <a name="usage"></a>Syntax 

Session-Id aus dem vorherigen Aufruf zurückgegeben wird als eine Kopfzeile auf nachfolgende API Anforderungen in übergeben.  
`workbook-session-id`HTTP-Header. 

<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```
[Nach oben](#excel-rest-api)

## <a name="worksheet-operations"></a>Arbeitsblatt-Vorgänge

#### <a name="list-worksheets-part-of-the-workbook"></a>Listenwebpart für Arbeitsblätter der Arbeitsmappe 
Anforderung 

<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets
accept: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets",
  "value": [
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets(%27%7B00000000-0001-0000-0000-000000000000%7D%27)",
      "id": "{00000000-0001-0000-0000-000000000000}",
      "name": "Sheet1",
      "position": 0,
      "visibility": "Visible"
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets(%27%7B00000000-0001-0000-0100-000000000000%7D%27)",
      "id": "{00000000-0001-0000-0100-000000000000}",
      "name": "Sheet57664",
      "position": 1,
      "visibility": "Visible"
    }
  ]
}
```
#### <a name="add-a-new-worksheet"></a>Hinzufügen eines neuen Arbeitsblatts 
 
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets
content-type: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "name": "Sheet32243" }
```

Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 201, Created
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets(%27%7B75A18F35-34AA-4F44-97CC-FDC3C05D9F40%7D%27)",
  "id": "{75A18F35-34AA-4F44-97CC-FDC3C05D9F40}",
  "name": "Sheet32243",
  "position": 5,
  "visibility": "Visible"
}
```

#### <a name="delete-a-worksheet"></a>Löschen eines Arbeitsblatts

Anforderung
```
DELETE /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('%7B75A18F35-34AA-4F44-97CC-FDC3C05D9F40%7D')
content-type: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```


#### <a name="update-worksheet-properties"></a>Aktualisieren Sie die Arbeitsblatteigenschaften

Anforderung 

```
PATCH /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('%7B00000000-0001-0000-0100-000000000000%7D')
content-type: Application/Json 
accept: application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "name": "SheetA", "position": 3 }
```

Antwort

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN')/workbook/worksheets(%27%7B00000000-0001-0000-0100-000000000000%7D%27)",
  "id": "{00000000-0001-0000-0100-000000000000}",
  "name": "SheetA",
  "position": 3,
  "visibility": "Visible"
}
```
[Nach oben](#excel-rest-api)

## <a name="chart-operations"></a>Diagramm Vorgänge

#### <a name="list-charts-that-are-part-of-the-worksheet"></a>Liste Diagramme, die Teil des Arbeitsblatts sind 

Anforderung
<!-- { "blockType": "ignored" } -->
```http 
GET /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts
accept: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id} 
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL')/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts",
  "value": [
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL')/workbook/worksheets(%27%7B00000000-0001-0000-0000-000000000000%7D%27)/charts(%27%7B00000000-0008-0000-0100-000003000000%7D%27)",
      "height": 235.5,
      "id": "{00000000-0008-0000-0100-000003000000}",
      "left": 276.0,
      "name": "Chart 2",
      "top": 0.0,
      "width": 401.25
   }
  ]
}
```

#### <a name="get-chart-image"></a>Erste Diagrammabbilds.

Anforderung 
<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts('%7B00000000-0008-0000-0100-000003000000%7D')/Image(width=0,height=0,fittingMode='fit')
authorization: Bearer {access-token} 
workbook-session-id: {session-id} 
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#Edm.String",
  "value": "{base-64-string}"
}
```

#### <a name="add-a-chart"></a>Hinzufügen eines Diagramms  

Anforderung

<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts/Add
content-type: Application/Json 
accept: application/Json 
authorization: Bearer {access-token} 

{ "type": "ColumnClustered", "sourcedata": "A1:C4", "seriesby": "Auto" }
```

Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 201, Created
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#chart",
  "@odata.type": "#microsoft.graph.chart",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL')/workbook/worksheets(%27%7B00000000-0001-0000-0000-000000000000%7D%27)/charts(%27%7B2D421098-FA19-41F7-8528-EE7B00E4BB42%7D%27)",
  "height": 216.0,
  "id": "{2D421098-FA19-41F7-8528-EE7B00E4BB42}",
  "left": 0.0,
  "name": "Chart 2",
  "top": 0.0,
  "width": 360.0
}
```

#### <a name="update-a-chart"></a>Aktualisieren eines Diagramms

`<!-- { "blockType": "ignored" } -->
```http 
PATCH /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts('%7B2D421098-FA19-41F7-8528-EE7B00E4BB42%7D')
content-type: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "height": 216.0, "left": 0, "name": "NewName", "top": 0, "width": 360.0 }

```
Antwort 

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL')/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL')/workbook/worksheets(%27%7B00000000-0001-0000-0000-000000000000%7D%27)/charts(%27%7B2D421098-FA19-41F7-8528-EE7B00E4BB42%7D%27)",
  "height": 216.0,
  "id": "{2D421098-FA19-41F7-8528-EE7B00E4BB42}",
  "left": 0.0,
  "name": "NewName",
  "top": 0.0,
  "width": 360.0
}
```

#### <a name="update-chart-source-data"></a>Aktualisieren von Diagrammdaten Quelle 

Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/charts('%7B2D421098-FA19-41F7-8528-EE7B00E4BB42%7D')/setData
content-type: Application/Json 
accept: application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "sourceData": "A1:C4", "seriesBy": "Auto" }
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

## <a name="table-operations"></a>Tabellenvorgänge 

#### <a name="get-list-of-tables"></a>Abrufen der Liste der Tabellen 

Anforderung 
<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJB6K563VVUU2ZC2FJBAHLSZZQXL/workbook/worksheets('%7B00000000-0001-0000-0000-000000000000%7D')/tables
accept: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 
```

#### <a name="update-table"></a>Aktualisieren Sie die Tabelle

Anforderung 
<!-- { "blockType": "ignored" } -->
```http 
PATCH /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('2')
content-type: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "name": "NewTableName", "showHeaders": true, "showTotals": false, "style": "TableStyleMedium4" }
```

Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%272%27)",
  "id": "2",
  "name": "NewTableName",
  "showHeaders": true,
  "showTotals": false,
  "style": "TableStyleMedium4"
}
```

#### <a name="get-list-of-table-rows"></a>Hier finden Sie die Liste der Tabellenzeilen
Anforderung 

<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('4')/Rows
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables('4')/rows",
  "value": [
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(0)",
      "index": 0,
      "values": [
        [
          42019,
          53,
          34
       ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(1)",
      "index": 1,
      "values": [
        [
          42020,
          45,
          39
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(2)",
      "index": 2,
      "values": [
        [
          42021,
          50,
          31
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(3)",
      "index": 3,
      "values": [
        [
          42022,
          43,
          39
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(4)",
      "index": 4,
      "values": [
        [
          42023,
          45,
          41
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows/itemAt(5)",
      "index": 5,
      "values": [
        [
          42024,
          52,
          40
        ]
      ]
    }
  ]
}
```

## <a name="get-list-of-table-columns"></a>Abrufen der Liste der Tabellenspalten

Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('4')/Columns
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort 

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK 
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables('4')/columns",
  "value": [
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/columns(%271%27)",
      "id": "1",
      "index": 0,
      "name": "Date",
      "values": [
        [
          "Date"
        ],
        [
          42019
       ],
        [
          42020
        ],
        [
          42021
        ],
        [
          42022
        ],
        [
          42023
        ],
        [
          42024
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/columns(%272%27)",
      "id": "2",
      "index": 1,
      "name": "High (F)",
      "values": [
        [
          "High (F)"
        ],
        [
          53
        ],
        [
          45
        ],
        [
          50
        ],
        [
          43
        ],
        [
          45
        ],
        [
          52
        ]
      ]
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/columns(%273%27)",
      "id": "3",
      "index": 2,
      "name": "Low (F)",
      "values": [
        [
          "Low (F)"
        ],
        [
          34
        ],
        [
          39
        ],
        [
          31
        ],
        [
          39
        ],
        [
          41
        ],
        [
          40
        ]
      ]
    }
  ]
}
```


#### <a name="add-a-table-row"></a>Hinzufügen einer Tabellenzeile

Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('4')/Rows
content-type: Application/Json 
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "values": [ [ "Jan-15-2016", "49", "37" ] ], "index": null }
```
Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 201, Created
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables('4')/rows/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%274%27)/rows(null)",
  "index": 6,
  "values": [
    [
      "Jan-15-2016",
      49,
      37
    ]
  ]
}
```
#### <a name="add-a-table-column"></a>Fügen Sie eine Spalte hinzu 

Anforderung 
<!-- { "blockType": "ignored" } -->
```http 
POST /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('2')/Columns
content-type: Application/Json 
accept: application/Json 


{ "values": [ [ "Status" ], [ "Open" ], [ "Closed" ] ], "index": 2 }
```

Antwort 

<!-- { "blockType": "ignored" } -->
```http 
HTTP code: 201, Created
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables('2')/columns/$entity",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/tables(%272%27)/columns(%274%27)",
  "id": "4",
  "index": 2,
  "name": "Status",
  "values": [
    [
      "Status"
    ],
    [
      "Open"
    ],
    [
      "Closed"
    ]
  ]
}
```

#### <a name="delete-table-row"></a>Tabellenzeile löschen

Anforderung 
<!-- { "blockType": "ignored" } -->
```http  
DELETE /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('4')/Rows/$/ItemAt(index=6)
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

#### <a name="delete-table-column"></a>Tabellenspalte löschen 
Anforderung
<!-- { "blockType": "ignored" } -->
```http
DELETE /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('4')/Columns('3')
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort 
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

#### <a name="convert-table-to-range"></a>Tabelle in Bereich umwandeln 
Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/tables('1')/convertToRange
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK 
content-type: application/json;odata.metadata 
```

#### <a name="table-sort"></a>Tabelle sortieren
Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('Sheet15799')/tables('table2')/sort/apply
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{
"fields" : [
  { "key": 0,
   "ascending": true
  }
]
}
```


Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

#### <a name="table-filter"></a>Table-filter
Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('Sheet15799')/tables('table2')/columns(id='2')/filter/apply
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{
"criteria" : 
  { "filterOn": "custom",
   "criterion1": ">15",
   "operator": "and",
   "criterion2": "<50"
   
  }
}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```


#### <a name="clear-filter"></a>Filter löschen
Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('Sheet15799')/tables('table2')/columns(id='2')/filter/clear
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

[Nach oben](#excel-rest-api)

## <a name="range-operations"></a>Bereich Vorgänge

#### <a name="get-range"></a>Abrufen von Bereichen 

Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/worksheets('test')/range(address='A1:B2')
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort 

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata 

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#range",
  "@odata.type": "#microsoft.graph.range",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/worksheets(%27%7B00000000-0001-0000-0300-000000000000%7D%27)/range(address=%27A1:B2%27)",
  "address": "test!A1:B2",
  "addressLocal": "test!A1:B2",
  "cellCount": 4,
  "columnCount": 2,
  "columnHidden": false,
  "columnIndex": 0,
  "formulas": [
    [
      "",
      ""
    ],
    [
      "",
      ""
    ]
  ],
  "formulasLocal": [
    [
      "",
      ""
    ],
    [
      "",
      ""
    ]
  ],
  "formulasR1C1": [
    [
      "",
      ""
    ],
    [
      "",
      ""
    ]
  ],
  "hidden": false,
  "numberFormat": [
    [
      "General",
      "General"
    ],
    [
      "General",
      "General"
    ]
  ],
  "rowCount": 2,
  "rowHidden": false,
  "rowIndex": 0,
  "text": [
    [
      "",
      ""
    ],
    [
      "",
      ""
    ]
  ],
  "values": [
    [
      "",
      ""
    ],
    [
      "",
      ""
    ]
  ],
  "valueTypes": [
    [
      "Empty",
      "Empty"
    ],
    [
      "Empty",
      "Empty"
    ]
  ]
}
```

#### <a name="range-update"></a>Bereich update 

<!-- { "blockType": "ignored" } -->
```http
PATCH /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/worksheets('test')/range(address='test!A1:B2')
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{ "values": [ [ "Test", "Value" ], [ "For", "Update" ] ] }
```

<!-- { "blockType": "ignored" } -->
```http
HTTP code: 200, OK
content-type: application/json;odata.metadata

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#range",
  "@odata.type": "#microsoft.graph.range",
  "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/worksheets(%27%7B00000000-0001-0000-0300-000000000000%7D%27)/range(address=%27test!A1:B2%27)",
  "address": "test!A1:B2",
  "addressLocal": "test!A1:B2",
  "cellCount": 4,
  "columnCount": 2,
  "columnHidden": false,
  "columnIndex": 0,
  "formulas": [
    [
      "Test",
      "Value"
    ],
    [
      "For",
      "Update"
    ]
  ],
  "formulasLocal": [
    [
      "Test",
      "Value"
    ],
    [
      "For",
      "Update"
    ]
  ],
  "formulasR1C1": [
    [
      "Test",
      "Value"
    ],
    [
      "For",
      "Update"
    ]
  ],
  "hidden": false,
  "numberFormat": [
    [
      "General",
      "General"
    ],
    [
      "General",
      "General"
    ]
  ],
  "rowCount": 2,
  "rowHidden": false,
  "rowIndex": 0,
  "text": [
    [
      "Test",
      "Value"
    ],
    [
      "For",
      "Update"
    ]
  ],
  "values": [
    [
      "Test",
      "Value"
    ],
    [
      "For",
      "Update"
    ]
  ],
  "valueTypes": [
    [
      "String",
      "String"
    ],
    [
      "String",
      "String"
    ]
  ]
}
```

#### <a name="range-sort"></a>Bereich Sortieren
Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /{version}/me/drive/items/01CYZLFJGUJ7JHBSZDFZFL25KSZGQTVAUN/workbook/worksheets('Sheet15799')/usedRange/sort/apply
authorization: Bearer {access-token} 
workbook-session-id: {session-id}

{
"fields" : [
  { "key": 0,
   "ascending": true
  }
]
}
```

Antwort
<!-- { "blockType": "ignored" } -->
```http
HTTP code: 204, No Content
```

[Nach oben](#excel-rest-api)

## <a name="named-items"></a>Benannte Elemente
Anforderung

<!-- { "blockType": "ignored" } -->
```http
GET /{version}/me/drive/items/01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4/workbook/names
authorization: Bearer {access-token} 
workbook-session-id: {session-id}
```

Antwort 

<!-- { "blockType": "ignored" } -->
```http 
HTTP code: 200, OK
content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/{version}/$metadata#users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/names",
  "value": [
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/names(%27data%27)",
      "name": "data",
      "type": "Range",
      "value": "Range!$A$1:$D$3",
      "visible": true
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/names(%27myrange%27)",
      "name": "myrange",
      "type": "Range",
      "value": "Range!$E$1:$F$7",
      "visible": true
    },
    {
      "@odata.id": "/users('f6d92604-4b76-4b70-9a4c-93dfbcc054d5')/drive/items('01CYZLFJDYBLIGAE7G5FE3I4VO2XP7BLU4')/workbook/names(%27range1%27)",
      "name": "range1",
      "type": "Range",
      "value": "Range!$I$1:$M$11",
      "visible": true
    }
  ]
}
```

## <a name="understanding-nulls-in-excel-api"></a>Grundlegendes zu-NULL-Werte in Excel-API

#### <a name="null-input-in-2-d-array"></a>Null Eingaben in 2D-Diagramme Array

`null`Eingabe in zweidimensionales Array (für Werte, Anzahl Format, Formel) wird im Bereich/Tabelle Zeile/Tabelle Spalten Update APIs ignoriert. Keine Aktualisierung stattfinden soll in das vorgesehene Ziel (Zelle) beim `null` Eingabe in Werte oder Format Zahl oder Formel gesendete Werte Raster.

Beispiel: In der Reihenfolge, nur Update bestimmte Teile des Bereichs, z. B. einige Zelle der Zahlenformat, und legen Sie beibehalten das vorhandene Zahlenformat in anderen Teilen des Bereichs, gewünschte Zahlenformat benötigt und senden `null` für die anderen Zellen.

In der folgenden Set-Anforderung werden nur einige Teile der Bereich Zahlenformat Beibehaltung der vorhandenen Zahlenformat auf den verbleibenden Teil (durch das Übergeben von null) festgelegt.

```json
{
  "values" : [["Eurasia", "29.96", "0.25", "15-Feb" ]],
  "numberFormat" : [[null, null, null, "m/d/yyyy;@"]]
}
```

#### <a name="null-input-for-a-property"></a>NULL-Eingabe für eine Eigenschaft

`null`ist keine gültige einzelne Eingabe für die gesamte-Eigenschaft. Beispielsweise Folgendes gilt nicht als die gesamte Werte können nicht festgelegt werden, zu null oder ignoriert.

```json
{
"values":  null
}

```

Im folgenden ist nicht gültig, entweder als null ist kein gültiger Farbe Wert.

```json
{
"color" :  null
}
```

#### <a name="null-response"></a>NULL-Antwort

Darstellung der Formateigenschaften, der nicht einheitlichen Werte besteht, ergibt die Rückgabe von einen null-Wert in der Antwort.

Beispiel: Ein Bereich kann eine der mehr Zellen bestehen. In Fällen, in dem die einzelnen Zellen im angegebenen Bereich enthaltenen uniform Formatierung keine Werte enthalten, werden die Ebene Darstellung Bereich nicht definiert.

```json
{
  "size: : null,
  "color" : null
}
```
[Nach oben](#excel-rest-api)

## <a name="blank-input-and-output"></a>Leere ein- und Ausgabe

Leere Werte in Update Anfragen werden als Anweisung zum Löschen oder Zurücksetzen der jeweiligen-Eigenschaft behandelt. Leerer Wert wird durch zwei doppelte Anführungszeichen ohne Leerzeichen dazwischen liegenden dargestellt. `""`

Beispiel:

* Für `values`, der Bereichswert gelöscht wird. Dies entspricht dem Löschen des Inhalts in der Anwendung.

* Für `numberFormat`, das Zahlenformat festgelegt ist, um `General`.

* Für `formula` und `formulaLocale`, die Formel Werte werden gelöscht.


Erwarten Sie für Lesevorgänge um leere Werte erhalten, wenn der Inhalt der Zellen Leerzeichen sind. Wenn die Zelle keine Daten oder einen Wert enthält, gibt die API einen leeren Wert zurück. Leerer Wert wird durch zwei doppelte Anführungszeichen ohne Leerzeichen dazwischen liegenden dargestellt. `""`.

```json
{
  "values" : [["", "some", "data", "in", "other", "cells", ""]]
}
```

```json
{
  "formula" : [["", "", "=Rand()"]]
}
```
[Nach oben](#excel-rest-api)

## <a name="unbounded-range"></a>Unbegrenzt Bereich

#### <a name="read"></a>Lesen

Unbegrenzt Bereichsadresse enthält Spalten- oder Zeilenfelds-IDs und ID nicht spezifizierte Zeile oder Spaltenbezeichner (entsprechend), z. B.:

* `C:C`, `A:F`, `A:XFD` (enthält nicht spezifizierte Zeilen)
* `2:2`, `1:4`, `1:1048546` (nicht spezifizierte Spalten enthält)

Wenn die API macht eine Anforderung zum Abrufen eines unbegrenzten Bereichs (z. B. `getRange('C:C')`, die Antwort zurückgegeben enthält `null` für Zelle level-Eigenschaften wie `values`, `text`, `numberFormat`, `formula`usw... Andere Bereichseigenschaften wie `address`, `cellCount`, usw. wider unbegrenzten Bereich.

#### <a name="write"></a>Write

Zelle Ebene Eigenschaften festlegen (z. B. Werte, NumberFormat usw.) für unbegrenzt Bereich ist wie die Eingabe Anforderung ist zu groß zum Verarbeiten von möglicherweise **nicht zulässig** .

Beispiel: Die folgenden ist keiner gültigen updateanforderung, da der angeforderte Bereich unbegrenzt ist.

<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets('Sheet1')/range(address="A:B")

{
  "values" : "Due Date"
}
```

Wenn Sie ein aktualisieren-Vorgang für einen solchen Bereich versucht wird, wird die API einen Fehler zurück.


## <a name="large-range"></a>Großen Bereich

Große Bereich impliziert einen Bereich, dessen Größe für einen einzelnen API-Aufruf zu groß ist. Viele Faktoren wie die Anzahl der Zellen, Werte, NumberFormat, Formeln im Bereich enthalten können, dass sie nicht für API Interaktion wird die Antwort so groß stellen. Die API ist einen bewährten Versuch, zurückgeben oder Schreiben in die angeforderten Daten. Allerdings kann sehr groß ist beteiligten aufgrund der großen Ressourcenverwendung ein Fehlerzustand API führen.

Vermeiden Sie eine solche Bedingung, mit lesen oder Schreiben für großen Bereich in mehrere kleinere Bereich werden empfohlen.


## <a name="single-input-copy"></a>Einzelne Input-Kopie

Zur Unterstützung der Aktualisierung eines Bereichs mit dieselben Werte wie oder -Zahlenformat oder Anwenden derselben Formel Beispieldokumenten wird in der Set-API die folgende Konventionen verwendet. Dieses Verhalten ähnelt in Excel eingeben von Werten oder Formeln, die einem Bereich in den Modus STRG + EINGABETASTE.

Sieht der API für eine *einzelne Zellenwert* und, wenn Ziel Bereichsdimension die Dimension Eingabebereich entspricht, wird es Anwenden des Updates auf den gesamten Bereich im Modell mit dem Wert oder eine Formel, die in der Anforderung bereitgestellten STRG + EINGABETASTE.

#### <a name="examples"></a>Beispiele

Die folgende Anforderung aktualisiert den ausgewählten Bereich mit dem Text "Beispieltext". Beachten Sie, dass Bereich 200 Zellen hat, während die Eingabe bereitgestellte nur 1 Zellwert verfügt.

<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets('Sheet1')/range(address="A1:B00")

{
  "values" : "Sample text"
}
```

## <a name="error-information"></a>Fehlerinformationen 

Fehler werden mit dem HTTP-Fehlercode sowie ein Error-Objekt zurückgegeben. Ein Fehler `code` und `message` bereitstellt, Erklärung der Grund zurückgegeben werden. Ein Beispiel ist unten aufgeführt:

<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": {
    "code": "ItemAlreadyExists",
    "message": "A resource with the same name or identifier already exists.",
    "innerError": {
      "request-id": "214ca7ea-9ea4-442e-9c67-71fdda0a559c",
      "date": "2016-07-28T03:56:09"
    }
  }
}
```
[Nach oben](#excel-rest-api)
