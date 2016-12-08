# <a name="get-person"></a>Abrufen der person

Rufen Sie die Eigenschaften und die Beziehungen eines Person-Objekts ab.
## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *People.Read*; *User.ReadBasic.All*
 
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/people/<id>
GET /users/<id>/people/<id>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
|Name|Wert|Beschreibung|
|:---------------|:--------|:-------|
|$filter|Zeichenfolge|Beschränkt die Antwort auf die Personen, deren Datensätze mit die angegebenen Kriterien enthält.|
|$orderby|Zeichenfolge|Standardmäßig werden die Personen in der Antwort nach ihrer Relevanz für Ihre Abfrage sortiert. Sie können die Reihenfolge der Personen in der Antwort mit dem Parameter *$orderby* ändern.|
|$search|string|Suchen nach Personen nach Name oder Alias. Fuzzyübereinstimmungen unterstützt|
|$select|Zeichenfolge|Durch Trennzeichen getrennte Liste der Eigenschaften in der Antwort aufzunehmen. Wählen Sie für eine optimale Leistung nur Teilmenge der Eigenschaften benötigt werden.|
|$skip|Ganzzahl|Überspringen Sie die ersten-n-Ergebnisse für Paging hilfreich. Dies wird nicht unterstützt, wenn Sie *$search*verwenden.|
|$top|Ganzzahl|Anzahl der Ergebnisse zurückgegeben werden soll.|

## <a name="request-headers"></a>Anforderungsheader
| Name      |Beschreibung|
|:----------|:----------|
| Autorisierung  | Bearer<code>|

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.
## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode eine `200 OK` Antwortobjekt Code und [Person](../resources/person.md) im Antworttext.
## <a name="examples"></a>Beispiele
#### <a name="browse"></a>Durchsuchen
Die folgende Anforderung Ruft die Personen relevantesten für den Benutzer, basierend auf Kommunikation, Zusammenarbeit und Business Beziehungen ab. In der Standardeinstellung Antwort 10 Datensätze zurückgibt, aber dies kann ändern mit dem Parameter *$top* . Diese Anforderung erfordert den *People.Read* Bereich.

<!-- {
  "blockType": "request",
  "name": "get_person"
}-->
```http
GET https://graph.microsoft.com/beta/me/people/
```

Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.person"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 196

{
  "displayName": "displayName-value",
  "givenName": "givenName-value",
  "surname": "surname-value",
  "birthday": "birthday-value",
  "personNotes": "personNotes-value",
  "isFavorite": true
}
```

##### <a name="requesting-a-subsequent-page-of-people"></a>Anfordern einer nachfolgenden Seite von Personen
Wenn die erste Antwort nicht die vollständige Liste der entsprechenden Personen enthält, können Sie eine zweite Anforderung mithilfe von *$top* und *$skip* So fordern Sie zusätzliche Seiten mit Informationen an vornehmen. Wenn die vorherige Anforderung Zusatzinformationen hat, ruft die folgende Anforderung der nächsten Seite mit Personen vom Server ab.

```http
GET https://graph.microsoft.com/beta/me/people/?$top=10&$skip=10
```

##### <a name="sort-the-response"></a>Sortieren der Antwort
Standardmäßig werden die Personen in der Antwort nach ihrer Relevanz für Ihre Abfrage sortiert. Sie können die Reihenfolge der Personen in der Antwort mit dem Parameter *$orderby* ändern. Diese Abfrage wählt die Personen, die für Sie relevant, nach dem Anzeigenamen sortiert, und klicken Sie dann auf die sortierte Liste die ersten 10 Personen zurückgegeben.

```http
GET https://graph.microsoft.com/beta/me/people/?$orderby=DisplayName
```
##### <a name="changing-the-number-of-people-returned-and-the-fields-returned"></a>Ändern der Anzahl der Benutzer zurückgegeben und die zurückgegebenen Felder
Sie können die Anzahl der Personen, die in der Antwort zurückgegeben wird, indem der Parameter *$top* ändern. 

Im folgende Beispiel fordert den relevantesten 1.000 Mitarbeiter. Anforderung schränkt auch die Menge der Daten vom Server gesendet werden, indem Sie nur den Anzeigenamen der Person anfordern.


```http
GET https://graph.microsoft.com/beta/me/people/?$top=1000&$Select=DisplayName
```
##### <a name="selecting-the-fields-to-return"></a>Auswählen der Felder zurückgeben
Sie können die vom Server mithilfe des *$select* -Parameters ein oder mehrere Felder auswählen zurückgegebene Datenmenge einschränken. Die *@odata.id* -Feld wird immer zurückgegeben.

Im folgenden Beispiel wird beschränkt die Antwort auf die *DisplayName* und *EmailAddress* der höchsten relevanten 10 Personen.

```http
GET https://graph.microsoft.com/beta/me/people/?$select=DisplayName,EmailAddresses
```
##### <a name="using-a-filter-to-limit-the-response"></a>Unter Verwendung eines Filters zur Begrenzung der Antwort
Den Parameter *$filter* können Sie die Antwort auf die Personen beschränken, deren Datensatz die angegebenen Kriterien enthält. 

Die folgende Abfrage beschränkt die Antwort an Personen mit der Quelle "Verzeichnis".


```http
GET https://graph.microsoft.com/beta/me/people/?$Filter=Sources/Any (source: source/Type  eq 'Directory')
```

##### <a name="selecting-the-fields-to-return-in-a-filtered-response"></a>Auswählen der Felder, die in eine gefilterte Antwort zurückgegeben

Sie können die Parameter *$select* und *$filter* zum Erstellen einer benutzerdefinierten Liste der Personen, für den Benutzer relevant und erhalten Sie nur die Felder, die die Anwendung benötigt kombinieren. 

Das folgende Beispiel ruft die *DisplayName* und *EmailAddress* von Personen, deren Anzeigename den angegebenen Namen entspricht. In diesem Beispiel werden nur Personen, deren Anzeigename "Nestor Kellum" entspricht, zurückgegeben. 


```http
GET https://graph.microsoft.com/beta/me/people/?$select=DisplayName,EmailAddresses&$Filter=DisplayName eq 'Nestor Kellum'
```

#### <a name="search-people"></a>Suchen nach Personen
Suchabfragen erfordern den *People.Read* Bereich.

##### <a name="using-search-to-select-people"></a>Wählen Sie Personen mithilfe der Suche

Verwenden Sie den Parameter *$search* , um Personen auszuwählen, die einen bestimmten Satz von Kriterien erfüllen. 

Die Suche in der folgenden Abfrage gibt zuständigen Personen, deren Vorname oder Nachname mit dem Buchstaben "j" beginnt.

```http
GET https://graph.microsoft.com/beta/me/people/?$search=j
```
##### <a name="using-search-to-specify-a-relevant-topic"></a>Geben Sie ein entsprechende Thema mithilfe der Suche

Die folgende Anforderung gibt zuständigen Personen, deren Name "Ma" enthält und die besitzen einer Zuordnung mit "Feature planen".

```http
GET https://graph.microsoft.com/beta/me/people/?$search="ma topic: feature planning"
```
##### <a name="performing-a-fuzzy-search"></a>Durchführen einer fuzzy-Suche

Die folgende Anforderung wird eine Suche für eine Person, die mit dem Namen "Hermaini Saal." Da eine relevante Person mit dem Namen "Herminia Hülle" vorhanden ist, wird die Informationen für "Herminia Hülle" zurückgegeben.

```http
GET https://graph.microsoft.com/beta/me/people/?$search="hermaini hall"
```
#### <a name="related-people"></a>Verwandte Personen

Die folgende Anforderung Ruft die Personen relevantesten an eine andere Person in der Organisation des Benutzers ab. Diese Anforderung erfordert den *User.ReadBasic.All* Bereich. In diesem Beispiel werden Nestor Kellums entsprechenden Personen angezeigt.

```http
GET https://graph.microsoft.com/beta/users('nestork@contoso.com')/people/
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get person",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
