# <a name="track-changes-for-an-item-and-its-children"></a>Nachverfolgen von Änderungen für ein Element und die untergeordneten

Ruft den aktuellen Status eines Elements und dessen untergeordnete Objekte und Nachverfolgen von Änderungen über einen Zeitraum.

Ihre app beginnt mit dem Aufruf `delta` ohne Angabe von Parametern. Dem Starten des Diensts Aufzählen der DriveItem Hierarchie, von Seiten Elemente und entweder Zurückgeben einer `@odata.nextLink` oder ein `@odata.deltaLink`, wie unten beschrieben. Ihre app sollten weiterhin Anrufe mit der `@odata.nextLink` , bis Sie nicht mehr finden Sie unter ein `@odata.nextLink` zurückgegeben, oder eine Antwort mit ein leerer Satz Änderungen angezeigt wird.

Nachdem Sie alle Änderungen empfangen abgeschlossen haben, können Sie sie in Ihrer lokalen Zustand anwenden. Um die Änderungen in der Zukunft zu überprüfen, rufen Sie `delta` erneut mit der `@odata.deltaLink` aus der vorherigen Antwort.

Gelöschte Elemente zurückgegeben werden, mit der [ `deleted` Facetten](../resources/deleted.md).
Elemente mit dieser Eigenschaftensatz sollten aus Ihrer lokalen Status entfernt werden. Hinweis: Sie sollten nur einen Ordner löschen, lokal, wenn es leer ist, nach dem alle Änderungen zu synchronisieren.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.Readwrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root/delta
GET /me/drive/items/{item-id}/delta
GET /me/drive/root:/{item-path}:/delta
```

## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Wert  | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwort Code und [DriveItem](../resources/driveitem.md) -Auflistung im Antworttext.

Zusätzlich zu der DriveItems-Auflistung wird die Antwort zudem eine der folgenden Eigenschaften aufweisen:

| Name                 | Wert  | Beschreibung                                                                                                                                      |
|:---------------------|:-------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| **@odata.nextLink**  | URL    | Eine URL die nächste verfügbare Seite mit Änderungen, abrufen, wenn in der aktuellen Gruppe weitere Änderungen vorhanden sind.                                        |
| **@odata.deltaLink** | URL    | Eine URL zurückgegeben wird, anstatt **@odata.nextLink** erst, nachdem alle aktuelle Änderungen zurückgegeben wurden. Verwendet, um die nächsten Gruppe von Änderungen in der Zukunft gelesen.  |


## <a name="example-initial-request"></a>Beispiel (erste Anforderung)
Es folgt ein Beispiel zum Einrichten des lokalen Zustand diese API-Aufruf von.

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie ein Beispiel für die erste Anforderung.

<!-- {
  "blockType": "request",
  "name": "get_item_delta"
}-->
```http
GET /drive/root/delta
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "0123456789abc",
            "name": "folder2",
            "folder": { }
        },
        {
            "id": "123010204abac",
            "name": "file.txt",
            "file": { }
        },
        {
            "id": "2353010204ddgg",
            "name": "file5.txt",
            "deleted": { }
        }
    ],
    "@odata.nextLink": "https://api.onedrive.com/drive/root/view.delta?token=1230919asd190410jlka"
}
```

Diese Antwort enthält die erste Seite der Änderungen, und die **@odata.nextLink** -Eigenschaft gibt an, dass mehr Elemente in der aktuellen Gruppe von Elementen verfügbar sind.
Ihre app sollten weiterhin den Wert URL anfordern **@odata.nextLink** , bis alle Seiten mit Elementen abgerufen wurden.

## <a name="example-last-page-in-a-set"></a>Beispiel (letzte Seite in einem Satz)
Es folgt ein Beispiel dafür, wie Sie diese API zum Aktualisieren des lokalen Zustand aufrufen.

##### <a name="request"></a>Anforderung
Es folgt eine Beispiel für eine Anforderung nach der anfänglichen Anforderung.

<!-- {
  "blockType": "request",
  "name": "get_item_delta"
}-->
```http
GET /drive/root/delta?(token='123123901209310923!23alksjd')
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "0123456789abc",
            "name": "folder2",
            "folder": { },
            "deleted": { }
        },
        {
            "id": "123010204abac",
            "name": "file.txt",
            "file": { }
        }
    ],
    "@odata.deltaLink": "https://graph.microsoft.com/beta/me/drive/root/delta?(token='1230919asd190410jlka')"
}
```

Diese Antwort weist darauf hin, dass das Element mit dem Namen `folder2` wurde gelöscht und das Element `file.txt` hinzugefügt oder zwischen der ursprünglichen Anforderung und dieser Anforderung zum Aktualisieren des lokalen Zustand geändert wurde.

Die letzte Seite des Elemente enthalten die **@odata.deltaLink** -Eigenschaft, die die URL, die später verwendet werden können bereitstellt, um Änderungen seit der aktuellen Gruppe von Elementen abzurufen.

## <a name="remarks"></a>Hinweise

* Delta-Feed zeigt den aktuellen Status für jedes Element, das nicht jeder Änderung. Wenn ein Element zweimal umbenannt wurden, werden sie nur einmal, mit den neuesten Namen angezeigt.
* Dasselbe Element kann nur einmal in einer Delta Feeds, die aus verschiedenen Gründen angezeigt.
  Verwenden Sie das letzte Vorkommen angezeigt.
* Die `parentReference` für Elemente Eigenschaft einen Wert für den **Pfad**nicht einschließen.
  Dies tritt auf, da Umbenennen eines Ordners nicht in die Nachfolger des Ordners zurückgegeben werden aus der view.delta führt. Bei Verwendung von view.delta sollten Sie Elemente immer nach Id verfolgen.

Möglicherweise treten bei der Dienst (z. B., wenn ein Client versucht, eine alte Token wiederverwenden nach für einen längeren Zeitraum getrennt wird, oder wenn Serverstatus wurde geändert und ein neues Token erforderlich ist) eine Liste der Änderungen für ein bestimmtes Token bereitstellen kann. In diesen Fällen gibt der Dienst zurück ein `HTTP 410 Gone` -Fehlers mit einer der folgenden Fehlercodes enthält Fehlerantwort und eine `Location` Kopfzeile einer neuen NextLink, die von Grund auf eine frische Delta-Enumeration beginnt mit. Vergleichen Sie nach Abschluss der vollständigen-Aufzählung der zurückgegebenen Elemente mit Ihrer lokalen Status, und befolgen Sie diese Anweisungen.

| Fehlertyp                       | Anweisungen                                                                                                                                                                                                                    |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ResyncChangesApplyDifferences`  | Ersetzen Sie alle lokalen Objekte mit dem Server-Version (einschließlich gelöscht), wenn Sie sicher sind, dass der Dienst wurde bis zu, dass Datum mit Ihren lokalen Änderungen beim letzten synchronisieren möchten. Laden Sie alle lokalen Änderungen, denen der Server nicht bekannt ist. |
| `ResyncChangesUploadDifferences` | Hochladen, die jeder lokale Elemente, dass der Dienst nicht zurückzugeben und Hochladen von Dateien, die unterscheiden sich von der Server-Version (Aktualisieren beide Kopien aus, falls Sie nicht genau wissen, welches aktuellere ist).                                       |


In OneDrive for Business und SharePoint `delta` wird nur unterstützt, auf die `root` Ordner und nicht für andere Ordner. Die folgenden DriveItem Eigenschaften wird ebenfalls nicht zurückgegeben:

* **createdBy**
* **cTag**
* **eTag**
* **fileSystemInfo**
* **lastModifiedBy**
* **parentReference**
* **Größe**


<!-- {
  "type": "#page.annotation",
  "description": "Get item delta",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
