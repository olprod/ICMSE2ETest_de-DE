# <a name="microsoft-graph-error-responses-and-resource-types"></a>Microsoft Graph Fehlerantworten und Ressourcentypen

<!--In this article:
  
-   [Status code](#msg_status_code)
-   [Error resource type](#msg_error_resource_type)
-   [Code property](#msg_code_property)

<a name="msg_error_response"> </a> -->

##<a name="status-code"></a>Statuscode
Fehler in der Microsoft Graph-API-Dienst werden mithilfe von standard-HTTP-Statuscodes als auch ein JSON-Fehler-Response-Objekt zurückgegeben. Die folgenden HTTP-Statuscodes sollte erwartet werden.

| Statuscode | Statusmeldung                  | Beschreibung                                                                                                                            |
|:------------|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| 400         | Ungültige Anforderung                     | Die Anforderung kann nicht verarbeitet werden, da es ungültig oder falsch ist.                                                                       |
| 401         | Nicht autorisiert                    | Authentifizierungsinformationen erforderlich ist, fehlt oder ist nicht gültig für die Ressource.                                                   |
| 403         | Nicht zulässig                       | Der Zugriff auf die angeforderte Ressource verweigert. Der Benutzer möglicherweise nicht ausreichende Berechtigungen.                                                 |
| 404         | Nicht gefunden                       | Die angeforderte Ressource ist nicht vorhanden.                                                                                                  |
| 405         | Methode unzulässig              | Die HTTP-Methode in der Anforderung ist für die Ressource nicht zulässig.                                                                         |
| 406         | Nicht akzeptabel                  | Dieser Dienst unterstützt keine im Accept-Header angeforderte Format.                                                                |
| 409         | Conflict                        | Der aktuelle Zustand Konflikte mit, was die Anforderung erwartet. Beispielsweise kann der angegebenen übergeordneten Ordner nicht vorhanden.                   |
| 410         | Unerwartet                            | Die angeforderte Ressource ist nicht mehr auf dem Server verfügbar.                                               |
| 411         | Erforderliche Länge                 | Ein Content-Length-Header muss auf die Anforderung.                                                                                    |
| 412         | Voraussetzung fehlgeschlagen             | Eine Voraussetzung, die in der Anforderung (beispielsweise ein If-Match-Header) bereitgestellten entspricht nicht den aktuellen Status der Ressource.                       |
| 413         | Anforderungsentität ist zu groß        | Die Anforderungsgröße überschreitet die maximal zulässige.                                                                                            |
| 415         | Nicht unterstützter Medientyp          | Der Inhaltstyp der Anforderung ist ein Format, das nicht vom Dienst unterstützt wird.                                                      |
| 416         | Bereich nicht ausreichend angefordert | Der angegebene Bytearray Bereich ist ungültig oder nicht verfügbar.                                                                                    |
| 422         | Einheit            | Die Anforderung kann nicht verarbeitet werden, da sie semantisch falsch ist.                                                                       |
| 429         | Zu viele Anfragen               | Clientanwendung hat gedrosselt wurde und dürfen nicht versuchen, die Anfrage wiederholt, bis eine bestimmte Zeitspanne vergangen ist.                |
| 500         | Interner Serverfehler           | Ein interner Serverfehler ist aufgetreten Verarbeitung der Anforderung.                                                                       |
| 501         | Nicht implementiert                 | Das angeforderte Feature ist nicht implementiert.                                                                                               |
| 503         | Dienst nicht verfügbar             | Der Dienst ist vorübergehend nicht verfügbar. Sie können die Anforderung nach einer kurzen Verzögerung wiederholen. Möglicherweise gibt es ein Retry-After-Header.                   |
| 507         | Nicht genügend Speicher            | Das maximale Speicherkontingent wurde erreicht.                                                                                            |
| 509         | Bandbreite wurde überschritten        | Ihre app wurde für die maximale Bandbreite Cap überschreiten gedrosselt wurde. Ihre app kann die Anforderung erneut wiederholen Sie nach dem mehr Zeit vergangen ist. |

Die Fehlerantwort ist ein einzelnes JSON-Objekt, das eine einzelne Eigenschaft namens **Fehler**enthält. Dieses Objekt enthält alle Details des Fehlers. Sie können hier anstelle von oder zusätzlich zu den zurückgegebenen HTTP-Statuscode zurückgegebene Informationen verwenden. Es folgt ein Beispiel einer vollständigen JSON Fehler Einrichtung.

<!-- { "blockType": "example", "@odata.type": "sample.error", "expectError": true, "name": "example-error-response"} -->
```json
{
  "error": {
    "code": "invalidRange",
    "message": "Uploaded fragment overlaps with existing data.",
    "innerError": {
      "requestId": "request-id",
      "date": "date-time"
    }
  }
}
```

<!--<a name="msg_error_resource_type"> </a> -->

# <a name="error-resource-type"></a>Fehler Ressourcentyp

Die Ressource Fehler wird zurückgegeben, wenn bei der Verarbeitung einer Anforderung ein Fehler auftritt.

Fehlerantworten entsprechen der Definition in der Spezifikation für [OData v4](http://docs.oasis-open.org/odata/odata-json-format/v4.0/os/odata-json-format-v4.0-os.html#_Toc372793091) für Fehlerantworten.

## <a name="json-representation"></a>JSON-Darstellung

Die Fehler Ressource besteht aus diesen Ressourcen:

<!-- { "blockType": "resource", "@odata.type": "sample.error" } -->
```json
{
  "error": { "@odata.type": "odata.error" }  
}
```

#### <a name="odataerror-resource-type"></a>Ressourcentyp OData.Error

Innerhalb der Fehler befindet Antwort ein Fehler Ressource, die umfasst die folgenden Eigenschaften:

<!-- { "blockType": "resource", "@odata.type": "odata.error", "optionalProperties": [ "target", "details", "innererror"] } -->
```json
{
  "code": "string",
  "message": "string",
  "innererror": { "@odata.type": "odata.error" }
}
```

| Name der Eigenschaft  | Wert                  | Description\                                                                                               |
|:---------------|:-----------------------|:-----------------------------------------------------------------------------------------------------------|
| **Code**       | string                 | Eine Zeichenfolge des Fehlercodes für den aufgetretenen Fehler                                                            |
| **Nachricht**    | string                 | Ein Entwickler bereit Meldung über den aufgetretenen Fehler. Dies sollte nicht für den Benutzer direkt angezeigt werden. |
| **innererror** | Error-Objekt           | Optional Zusätzliche Error-Objekte, die möglicherweise detaillierter als der obersten Ebene Fehler.                     |
<!-- {
  "type": "#page.annotation",
  "description": "Understand the error format for the API and error codes.",
  "keywords": "error response, error, error codes, innererror, message, code",
  "section": "documentation",
  "tocPath": "Misc/Error Responses"
} -->

<!--<a name="msg_code_property"> </a> -->

##<a name="code-property"></a>Code (Eigenschaft)

Die `code` -Eigenschaft enthält die folgenden möglichen Werte. Behandeln eines diese Fehler sollten Ihre apps vorbereitet werden.

| Code                      | Beschreibung
|:--------------------------|:--------------
| **Zugriff verweigert**          | Der Aufrufer nicht über die Berechtigung zum Ausführen der Aktion. 
| **activityLimitReached**  | Die app oder der Benutzer hat gedrosselt wurden.
| **generalException**      | Ein nicht spezifizierter Fehler ist aufgetreten.
| **invalidRange**          | Der angegebene Bytearray Bereich ist ungültig oder nicht verfügbar.
| **invalidRequest**        | Anforderung ist ungültig oder falsch.
| **itemNotFound**          | Die Ressource konnte nicht gefunden werden.
| **malwareDetected**       | In der angeforderten Ressource wurde Schadsoftware ermittelt.
| **nameAlreadyExists**     | Der Name des angegebenen Elements ist bereits vorhanden.
| **"NotAllowed" an**            | Die Aktion wird vom System nicht zulässig.
| **notSupported**          | Die Anforderung wird vom System nicht unterstützt.
| **resourceModified**      | Die Ressource, die aktualisiert wurde geändert, seit der Anrufer zuletzt es in der Regel ein Konflikt eTag gelesen.
| **resyncRequired**        | Das Token Delta ist nicht mehr gültig, und die app muss den Synchronisierungsstatus zurückgesetzt.
| **serviceNotAvailable**   | Der Dienst ist nicht verfügbar. Versuchen Sie erneut nach einer kurzen Verzögerung der Anforderung. Möglicherweise gibt es ein Retry-After-Header. 
| **quotaLimitReached**     | Der Benutzer hat die Kontingentgrenze erreicht.
| **nicht authentifizierte**       | Der Anrufer wird nicht authentifiziert.

Die `innererror` -Objekts kann enthalten rekursiv mehr `innererror` Objekte mit zusätzlichen, bestimmte Fehlercodes. Bei der Behandlung eines Fehlers sollten apps eine Schleife durch alle verfügbaren Fehlercodes und nehmen Sie die ausführlichste aus, der sie verstehen. Einige der ausführlichere Codes sind am unteren Rand auf dieser Seite aufgeführt.

Zum bestätigen, dass ein Error-Objekt ein Fehler ist Sie erwarten, müssen Sie eine Schleife über die `innererror` Objekte, benötigen die Fehlercodes erwarten. Beispiel:

```csharp
public bool IsError(string expectedErrorCode)
{
    OneDriveInnerError errorCode = this.Error;
    while (null != errorCode)
    {
        if (errorCode.Code == expectedErrorCode)
            return true;
        errorCode = errorCode.InnerError;
    }
    return false;
}
```

Ein vollständiges Beispiel für die Behandlung von Fehlern ordnungsgemäß sehen Sie sich die [Fehlerbehandlung von Code](https://gist.github.com/rgregg/a1866be15e685983b441).

Die `message` -Eigenschaft im Stamm enthält eine Fehlermeldung, die für die direkte Verwendung für Entwickler zum Lesen. Fehlermeldungen wurden nicht lokalisiert und sollte nicht direkt mit dem Benutzer angezeigt werden. Bei der Behandlung von Fehlern, sollte Ihr Code nicht aus der Schlüssel `message` Werte, da sie jederzeit ändern können, und sie häufig dynamischen Informationen speziell für die fehlgeschlagene Anforderung enthalten. Sie sollten nur codieren Sie mit Fehlercodes im zurückgegebenen `code` Eigenschaften.

### <a name="detailed-error-codes"></a>Detaillierte Fehlercodes
Im folgenden sind einige weitere Fehler, die Ihre app in der geschachtelten auftreten `innererror` Objekte. Apps sind nicht erforderlich, diese zu behandeln, aber können, falls gewünscht. Der Dienst neue Fehlercodes hinzuzufügen oder Beenden der alten jederzeit zurückgeben, so wichtig ist, dass alle apps die grundlegende Fehlercodes in den vorstehenden section](#code-property) verarbeiten können.

| Code                               | Beschreibung
|:-----------------------------------|:----------------------------------------------------------
| **accessRestricted**               | Zugriff auf das Element Besitzer beschränkt.
| **cannotSnapshotTree**             | Fehler beim Abrufen einer Momentaufnahme konsistente Delta. Versuchen Sie es erneut.
| **childItemCountExceeded**         | Maximale Grenzwert für die Anzahl der untergeordneten Elemente wurde erreicht.
| **entityTagDoesNotMatch**          | ETag entspricht nicht der aktuelle Wert des Elements.
| **fragmentLengthMismatch**         | Deklarierte Gesamtgröße für dieses Fragment unterscheidet sich von der der Sitzung hochladen.
| **fragmentOutOfOrder**             | Hochgeladenen Fragment ist nicht der Reihe nach.
| **fragmentOverlap**                | Hochgeladenen Fragment überschneidet sich mit vorhandenen Daten.
| **invalidAcceptType**              | Ungültiger Typ akzeptieren.
| **invalidParameterFormat**         | Ungültiger Parameterformat.
| **invalidPath**                    | Name enthält unzulässige Zeichen.
| **invalidQueryOption**             | Ungültige Abfrageoption.
| **invalidStartIndex**              | Ungültiger Index.
| **lockMismatch**                   | Sperre Token entspricht nicht vorhandene sperren.
| **lockNotFoundOrAlreadyExpired**   | Derzeit ist keine noch nicht abgelaufenen Sperre auf das Element vorhanden.
| **lockOwnerMismatch**              | Sperre Besitzer-ID ist keine Übereinstimmung bereitgestellten-ID.
| **malformedEntityTag**             | ETag-Header ist ungültig. ETags müssen Zeichenfolgen in Anführungszeichen eingeschlossen werden.
| **maxDocumentCountExceeded**       | Max maximale Anzahl von Dokumenten wird erreicht.
| **maxFileSizeExceeded**            | Maximale Dateigröße überschritten.
| **maxFolderCountExceeded**         | Max maximale Anzahl der Ordner wird erreicht.
| **maxFragmentLengthExceeded**      | Maximale Dateigröße überschritten.
| **maxItemCountExceeded**           | Max maximale Anzahl von Elementen wird erreicht.
| **maxQueryLengthExceeded**         | Länge der Max-Abfrage überschritten.
| **maxStreamSizeExceeded**          | Maximale Streamgröße überschritten.
| **parameterIsTooLong**             | Der Parameter überschreitet die maximale Länge.
| **parameterIsTooSmall**            | Parameter ist kleiner und minimale Wert.
| **pathIsTooLong**                  | Pfad überschreitet die maximale Länge.
| **pathTooDeep**                    | Ordner Hierarchie Tiefe Grenzwert erreicht.
| **propertyNotUpdateable**          | Diese Eigenschaft kann nicht aktualisiert werden.
| **resyncApplyDifferences**         | Resync erforderlich sind. Ersetzen Sie alle lokalen Objekte mit dem Server-Version (einschließlich gelöscht), wenn Sie sicher sind, dass der Dienst wurde bis zu, dass Datum mit Ihren lokalen Änderungen beim letzten synchronisieren möchten. Laden Sie alle lokalen Änderungen, denen der Server nicht bekannt ist.
| **resyncRequired**                 | Resync ist erforderlich.
| **resyncUploadDifferences**        | Resync erforderlich. Hochladen, die jeder lokale Elemente, dass der Dienst nicht zurückzugeben und Hochladen von Dateien, die unterscheiden sich von der Server-Version (Aktualisieren beide Kopien aus, falls Sie nicht genau wissen, welches aktuellere ist).
| **serviceNotAvailable**            | Der Server ist die aktuelle Anforderung kann nicht verarbeitet werden.
| **serviceReadOnly**                | Ressource ist vorübergehend schreibgeschützt.
| **throttledRequest**               | Zu viele Anforderungen.
| **tooManyResultsRequested**        | Zu viele Ergebnisse angefordert.
| **tooManyTermsInQuery**            | Zu viele Ausdrücke in der Abfrage.
| **totalAffectedItemCountExceeded** | Vorgang ist nicht zulässig, da die Anzahl der betroffenen Elemente Schwellenwert überschreitet.
| **truncationNotAllowed**           | Abschneiden von Daten ist nicht zulässig.
| **uploadSessionFailed**            | Hochladen Sie Sitzung ist fehlgeschlagen.
| **uploadSessionIncomplete**        | Hochladen Sie unvollständige Sitzung.
| **uploadSessionNotFound**          | Laden Sie die Sitzung nicht gefunden.
| **virusSuspicious**                | In diesem Dokument wird verdächtigen und weist möglicherweise einen Virus.
| **zeroOrFewerResultsRequested**    | NULL oder weniger Ergebnisse angefordert werden.

<!-- ##Additional Resources##

- [Microsoft Graph API release notes and known issues](microsoft-graph-api-release-notes-known-issues.md )
- [Hands on lab: Deep dive into the Microsoft Graph API](http://dev.office.com/hands-on-labs/4585) -->
