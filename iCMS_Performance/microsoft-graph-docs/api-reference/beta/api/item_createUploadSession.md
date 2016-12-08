# <a name="upload-large-files-with-an-upload-session"></a>Hochladen von großen Dateien mit einer Sitzung hochladen

Erstellen Sie eine Sitzung hochladen, um Ihre app zum Hochladen von Dateien, bis die maximale Dateigröße zu ermöglichen.
Eine Sitzung hochladen kann Ihre app hochzuladenden Bereiche der Datei im sequental API-Anforderungen, wodurch die Übertragung fortgesetzt werden kann, wenn eine Verbindung getrennt wird, während der Upload ausgeführt wird.

Zum Hochladen einer Datei mit einer Sitzung hochladen umfasst zwei Schritte:

1. [Erstellen Sie eine Sitzung hochladen](#create-an-upload-session)
2. [Hochladen von Bytes in der Sitzung hochladen](#upload-bytes-to-the-upload-session)

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="create-an-upload-session"></a>Erstellen Sie eine Sitzung hochladen

Um eine große Dateien hochladen beginnen, muss Ihre app zunächst eine neue Sitzung Upload anfordern.
Dadurch wird einen temporärer Speicherort, in dem die Bytes der Datei gespeichert wird, bis die vollständige Datei hochgeladen wurde, erstellt.
Nachdem das letzte Byte der Datei hochgeladen wurde die Sitzung Upload abgeschlossen ist, und die endgültige Datei wird im Zielordner angezeigt.

### <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/root:/{path-to-item}:/createUploadSession
POST /me/drive/items/{parent-item-id}:/{filename}:/createUploadSession
```

### <a name="request-body"></a>Anforderungstext
Keine Anforderungstext ist erforderlich. Sie können jedoch einen Anforderungstext, um zusätzliche Daten über die hochgeladene Datei bereitzustellen angeben.

Um das Verhalten zu kontrollieren, falls der Dateiname bereits ausgeführt wird, können Sie beispielsweise die Konflikt Verhalten-Eigenschaft im Textkörper der Anforderung angeben.

```json
{
    "item": {
        "@microsoft.graph.conflictBehavior": "rename"
    }
}
```

### <a name="optional-request-headers"></a>Optionale Anforderungsheader

| Name       | Wert | Beschreibung                                                                                                                                                            |
|:-----------|:------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *If-Match-* | ETag  | Wenn diese Anforderungsheader enthalten und bereitgestellt eTag (oder cTag) nicht das aktuelle Etag auf das Element entspricht eine `412 Precondition Failed` Feher Antwort zurückgegeben wird. |


### <a name="response"></a>Antwort
Die Antwort auf diese Anforderung bietet die Details der neu erstellten [UploadSession](../resources/uploadsession.md), die die für das Hochladen von den Teilen der Datei verwendete URL enthält. 

### <a name="example"></a>Beispiel

<!-- {
  "blockType": "request",
  "name": "driveItem_createUploadSession"
}-->
```http
POST /me/drive/root:/{item-path}:/createUploadSession
```

### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.uploadSession"
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "uploadUrl": "https://tenant-my.sharepoint.com/alkjl1kjklna",
  "expirationDateTime": "2020-08-24T10:58:00Z",
  "nextExpectedRanges": ["0-"]
}
```

## <a name="upload-bytes-to-the-upload-session"></a>Hochladen von Bytes in der Sitzung hochladen

Um die Datei oder einen Teil der Datei hochzuladen, sendet Ihre app eine PUT-Anforderung an den **UploadUrl** -Wert in der **CreateUploadSession** Antwort empfangen.
Sie können die gesamte Datei hochladen, oder Teilen Sie die Datei in Fragmente, solange die maximale Bytes pro Anforderung ist kleiner als 60 MiB.
Die Fragmente der Datei müssen in Reihenfolge sequentally hochgeladen werden.
Hochladen von außerhalb der Reihenfolge Fragmente führt einen Fehler.

**Hinweis:** Wenn Ihre app eine Datei in mehrere Fragmente aufgeteilt ist, werden die Größe der einzelnen Fragment **MUSS** ein Vielfaches von 320 KiB. Mit einer Fragmentgröße, die nicht gleichmäßig durch 320 Division wird führt zu Fehlern Ausführen eines Commits für einige Dateien.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die 26 ersten Byte einer 128-Byte-Datei hochgeladen haben.
Der **Content-Length** -Header gibt die Größe der aktuellen Anforderung.
Der **Inhalt Range** -Header gibt an, Bereich von Bytes in der gesamten Datei, die diese Anforderung darstellt.
Die gesamte Länge der Datei muss bekannt sein, bevor Sie das erste Fragment der Datei hochladen können.

<!-- { "blockType": "request", "name": "upload-fragment-piece", "scopes": "files.readwrite" } -->
```
PUT https://tenant-my.sharepoint.com/alkjl1kjklna
Content-Length: 26
Content-Range: bytes 0-25/128

<bytes 0-25 of the file>
```

**Wichtig:** Ihre app muss sicherstellen die gesamten Dateigröße im Header **Content-Range** angegebene für alle Anfragen identisch ist.
Die Anforderung schlägt fehl, wenn ein Fragment eine anderen Dateigröße deklariert.

### <a name="response"></a>Antwort
<!-- { "blockType": "response", "@odata.type": "microsoft.graph.uploadSession", "truncated": true } -->
```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "expirationDateTime": "2015-01-29T09:21:55.523Z",
  "nextExpectedRanges": ["26-"]
}
```

Ihre app kann den **NextExpectedRanges** Wert verwenden, um zu bestimmen, wo Sie das nächste Fragment beginnen.
Mangelndes angegeben, mehrere Bereiche, die Teile der Datei, die der Server noch nicht erhalten hat. Dies ist nützlich, wenn Sie benötigen, um eine Übertragung fortzusetzen, die unterbrochen wurde und Ihr Client nicht sicher sind, den Status für den Dienst ist.

Sie sollten immer die Fragmentgröße gemäß den best Practices unten festlegen. Nehmen Sie nicht an, dass diese **NextExpectedRanges** Reanges der richtigen Größe für ein Upload-Fragment zurückgegeben wird. Die **NextExpectedRanges** -Eigenschaft gibt Bereiche der Datei, die nicht empfangen wurden und nicht um ein Muster für wie die Datei hochgeladen werden sollen.

**Hinweise:**

* Die `nextExpectedRanges` Eigenschaft wird nicht immer auflisten, alle fehlenden Bereiche.
* Auf erfolgreiche Fragment Schreibvorgänge wird es in den nächsten Bereich (z. b. Ausgangsvorlage zurückzugeben. "523-").
* Bei Fehlern bei der Client wurde bereits ein Fragment der Server empfangen gesendet, der Server antwortet mit `HTTP 416 Requested Range Not Satisfiable`. 
  Sie können die [Anforderung Upload-Status](#resuming-an-in-progress-upload) , um eine ausführlichere Liste der fehlenden Bereichen abrufen.


## <a name="completing-a-file"></a>Abschließen einer Datei

Wenn das letzte Fragment einer Datei empfangen wird der Server führt eine Antwort mit einem `HTTP 201 Created` oder `HTTP 200 OK`.
Der Antworttext enthält auch die Standardeigenschaft für die **DriveItem** , das die abgeschlossene Datei festgelegt.

<!-- { "blockType": "request", "name": "upload-fragment-final", "scopes": "files.readwrite" } -->
```
PUT https://tenant-my.sharepoint.com/alkjl1kjklna
Content-Length: 21
Content-Range: bytes 101-127/128

<final bytes of the file>
```

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "912310013A123",
  "name": "largefile.vhd",
  "size": 128,
  "file": { }
}
```
**Hinweis:** Die Antwort Element wird aus Gründen der Übersichtlichkeit Dokumentation Zahl gekürzt.

## <a name="cancel-an-upload-session"></a>Abbrechen einer Sitzung hochladen

Zum Abbrechen eine Sitzung Upload senden eine DELETE-Anforderung an den Upload-URL.
Dadurch wird die temporäre Datei mit den Daten, die zuvor hochgeladen bereinigt.
Dies sollte verwendet werden in Szenarien, in dem der Upload, beispielsweise abgebrochen wird, wenn der Benutzer die Übertragung abbricht.

Temporäre Dateien und die zugehörigen Upload-Sitzungen werden automatisch bereinigt nach Ablauf der **ExpirationDateTime** .

### <a name="example"></a>Beispiel

Die DELETE-Anforderung wird Immedately Ablaufen der Sitzung hochladen und entfernen Sie alle zuvor hochgeladenen Bytes.

<!-- { "blockType": "request", "name": "upload-fragment-cancel", "scopes": "files.readwrite" } -->
```http
DELETE https://tenant-my.sharepoint.com/alkjl1kjklna
```

### <a name="response"></a>Antwort

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 204 No Content
```

## <a name="resuming-an-in-progress-upload"></a>Wiederaufnehmen einer laufenden hochladen

Wenn eine Anforderung Upload getrennt ist oder ein Fehler auftritt, bevor die Anforderung abgeschlossen ist, werden alle Bytes in dieser Anforderung ignoriert.
Dies kann vorkommen, wenn die Verbindung zwischen Ihrer app und der Dienst beendet wird.
In diesem Fall kann Ihre app die Übertragung aus dem zuvor abgeschlossenen Fragment wieder aufnehmen.

Um herauszufinden, welche Bytebereiche zuvor eingegangen sind, kann Ihre app den Status einer Sitzung Upload anfordern.

### <a name="example"></a>Beispiel
Abfragen des Status des Uploads durch Senden einer GET-Anforderung an die `uploadUrl`.

<!-- { "blockType": "request", "name": "upload-fragment-resume", "scopes": "files.readwrite" } -->
```
GET https://tenant-my.sharepoint.com/alkjl1kjklna
```

Der Server antwortet mit einer Liste der fehlenden Bytebereiche, die hochgeladen werden müssen und die Ablaufzeit für die Sitzung hochladen.

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.uploadSession", "truncated": true } -->
```http
HTTP/1.1 200 OK

{
  "expirationDateTime": "2015-01-29T09:21:55.523Z",
  "nextExpectedRanges": ["12345-"]
}
```

### <a name="upload-remaining-data"></a>Hochladen der verbleibende Daten
Nun, da Ihre app, wo Sie das Hochladen von beginnen bekannt ist, Fortsetzen des Uploads nach der Anleitung in [Bytes an der Sitzung Upload hochladen](#upload-bytes-to-the-upload-session).


## <a name="best-practices"></a>Bewährte Methoden

* Fortsetzen oder Retry uploads dieser Fehler aufgrund von Unterbrechungen der Verbindung oder 5xx Fehlern, einschließlich:
  * `500 Internal Server Error`
  * `502 Bad Gateway`
  * `503 Service Unavailable`
  * `504 Gateway Timeout`
* Verwenden Sie eine exponentielle Back deaktiviert Strategie Wenn beim Fortsetzen oder Wiederholen Upload Anforderungen 5xx Serverfehler zurückgegeben werden.
* Bei anderen Fehlern sollten Sie keine exponentielle Back deaktiviert Strategie aber Grenzwert verwenden, die Anzahl der Wiederholungsversuche vorgenommen.
* Behandeln `404 Not Found` Fehler bei der Wiederaufnahme Uploads von den gesamten Upload von vorne beginnen.
* Wiederaufnahme Datei überträgt für Dateien, die größer als 10 MiB (10 \* 1024 \* 1024 Bytes).
* Eine Fragmentgröße von 10 MiB für stabil Hochgeschwindigkeits-Verbindungen ist optimal. 
  Für langsamer oder weniger zuverlässig Verbindungen können von einer kleineren Fragment bessere Ergebnisse angezeigt werden. 
  Die empfohlene Fragmentgröße ist zwischen 5 bis 10 MiB.
* Verwenden Sie eine Fragmentgröße, das ist ein Vielfaches von 320 KiB (320 \* 1024 Bytes). 
  Eine Fragmentgröße verwenden, die ein Vielfaches von 320 ist, ein Fehler kann KiB bewirken große dateiübertragungen, nachdem das letzte Fragment hochgeladen wurde, die Fehler aufweisen.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Upload item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
