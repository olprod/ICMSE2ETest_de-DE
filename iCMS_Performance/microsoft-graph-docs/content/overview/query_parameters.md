# <a name="microsoft-graph-optional-query-parameters"></a>Microsoft Graph optional Abfrageparameter
## <a name="optional-odata-query-parameters"></a>Optionale Parameter der OData-Abfrage
Microsoft Graph bietet mehrere optional Abfrageparametern, die Sie zum angeben und steuern die Menge der Daten wird in der Antwort verwenden können. Microsoft Graph unterstützt die folgenden Abfrageoptionen. 

|Name|Wert|Beschreibung|
|:---------------|:--------|:-------|
|$select|Zeichenfolge|Durch Trennzeichen getrennte Liste der Eigenschaften in der Antwort aufzunehmen.|
|$Erweitern|Zeichenfolge|Durch Trennzeichen getrennte Liste von Beziehungen zu erweitern und in der Antwort enthalten.  |
|$orderby|Zeichenfolge|Durch Trennzeichen getrennte Liste der Eigenschaften, die verwendet werden, die Reihenfolge der Elemente in der Antwort-Auflistung sortiert.|
|$filter|Zeichenfolge|Die Antwort basierend auf einem Satz von Kriterien filtern.|
|$top|Ganzzahl|Die Anzahl der Elemente in einem Resultset zurückgegeben.|
|$skip|Ganzzahl|Die Anzahl der Elemente in einem Resultset überspringen.|
|$skipToken|Zeichenfolge|Paging-Token, das zum Abrufen der nächsten Gruppe von Ergebnissen verwendet wird.|
|$count|Keine|Eine Auflistung und die Anzahl der Elemente in der Auflistung.|


**Codierung Abfrageparameter**

- Wenn Sie out-Abfrageparameter im [Microsoft Graph Explorer](https://graphexplorer2.azurewebsites.net/)-verwenden, können Sie kopieren und fügen Sie die Beispiele unten ohne alle URL-Codierung der Abfragezeichenfolge. Das folgende Beispiel funktioniert kein Problem _im Diagramm Explorer_ ohne Leerzeichen und Angebot Zeichen Codierung:
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 
- Stellen Sie im Allgemeinen beim Abfrage Parameter _in Ihrer app_angeben, sicher, dass Sie entsprechend Codieren von Zeichen, die [für eine besondere Bedeutung in einem URI reserviert](https://tools.ietf.org/html/rfc3986#section-2.2)sind.
Codieren Sie beispielsweise die Leerzeichen und Angebot Zeichen im letzten Beispiel wie unten dargestellt:
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address%20eq%20%27jon@contoso.com%27
```

### <a name="select"></a>$select
Verwenden Sie eine Teilmenge der Eigenschaften zurückgegeben werden sollen Sie zum Angeben der Abfrageoption **$select** . Beispielsweise wenn Sie Ihre Nachrichten abrufen, möglicherweise möchten Sie, dass nur die **von** auswählen und **Subject** -Eigenschaften des Nachrichten zurückgegeben werden.

```http
GET https://graph.microsoft.com/v1.0/me/messages?$select=from,subject
```

<!--For example, when retrieving the children of an item on a drive, you want to select that only the **name** and **size** properties of items are returned.

```http
GET https://graph.microsoft.com/v1.0/me/drive/root/children?$select=name,size
```

By submitting the request with the `$select=name,size` query string, the objects
in the response will only have those property values included. 


```json
{
  "value": [
    {
      "id": "13140a9sd9aba",
      "name": "Documents",
      "size": 1024
    },
    {
      "id": "123901909124a",
      "name": "Pictures",
      "size": 1012010210
    }
  ]
}
```--> 

### <a name="expand"></a>$Erweitern

Navigationsvorgänge auf ein Objekt oder eine Auflistung von das verwiesene Element werden in Microsoft Graph-API-Anforderungen nicht automatisch erweitert. Dies ist entwurfsbedingt, da es reduziert den Netzwerkdatenverkehr und den Zeitaufwand für das eine Antwort vom Dienst generiert. Möglicherweise möchten Sie jedoch in einigen Fällen die Ergebnisse in eine Antwort aufzunehmen.

Die **$Erweitern** Abfragezeichenfolgen-Parameter können Sie weisen die API erweitern ein untergeordnetes Objekt oder Auflistung und die Ergebnisse enthalten.

Um die Informationen zum Stamm von Laufwerk und untergeordnete Elemente der obersten Ebene Elemente in einem Laufwerk abzurufen, verwenden Sie beispielsweise den Parameter **$Erweitern** . In diesem Beispiel wird eine Anweisung **$select** auch nur die Eigenschaften _-Id_ und _Name_ der untergeordneten Elemente Elemente zurückgegeben werden.

```http
GET https://graph.microsoft.com/v1.0/me/drive/root?$expand=children($select=id,name)
```

>  **Hinweis**: die maximale Anzahl von erweiterten Objekte für eine Anforderung, beträgt 20. 

> Darüber hinaus bei einer Abfrage für die Ressource [Benutzer](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/user) können **$Erweitern** Sie die Eigenschaften nur ein untergeordnetes Objekt oder Auflistung zu einem Zeitpunkt abgerufen. 

Im folgenden Beispiel wird die **Benutzerobjekte, jeweils mit bis zu 20 **DirectReport** -Objekte in der **DirectReports** erweitert** :
```http
GET https://graph.microsoft.com/v1.0/users?$expand=directReports
```
Einige andere Ressourcen möglicherweise einen Grenzwert sowie und muss daher immer auf mögliche Fehler zu überprüfen.


<!---The following shows a sample result that is returned in the response body.-->


### <a name="orderby"></a>$orderby

Um die Sortierreihenfolge der Elemente aus der API zurückgegeben anzugeben, verwenden Sie die Abfrageoption **$orderby** . 

Beispielsweise lautet, um die Benutzer in der Organisation nach dem Anzeigenamen sortiert zurückzugeben, die Syntax wie folgt:

```http
GET https://graph.microsoft.com/v1.0/users?$orderBy=displayName
``` 

Sie können auch nach komplexen Typ Entitäten sortiert werden. Im folgenden Beispiel ruft Nachrichten ab und sortiert sie nach dem Feld **Adresse** der **aus** -Eigenschaft, die von den komplexen Typ **EmailAddress**ist:

```http
GET https://graph.microsoft.com/v1.0/me/messages?$orderBy=from/emailAddress/address
``` 

Fügen Sie zum Sortieren der Ergebnisse in aufsteigender oder absteigender Reihenfolge entweder `asc` oder `desc` , der Name des Felds, getrennt durch ein Leerzeichen `?orderby=name%20desc`.

 >  **Hinweis**: $filter Ausdrücke **$orderby** kombiniert werden.

### <a name="filter"></a>$filter
Um die Antwortdaten basierend auf einem Satz von Kriterien zu filtern, verwenden Sie die Abfrageoption **$filter** .
Beispielsweise ist, um Benutzer in der Organisation Filter nach Anzeigename zurückgeben möchten, die mit "Garth" beginnt, die Syntax wie folgt.

```http
GET https://graph.microsoft.com/v1.0/users?$filter=startswith(displayName,'Garth')
```

Sie können auch nach komplexen Typ Entitäten filtern. Das folgende Beispiel gibt Nachrichten, die das Feld **Adresse** der **von** -Eigenschaft gleich hat "jon@contoso.com". die Eigenschaft **aus** der komplexe Typ **EmailAddress**ist.

```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 

### <a name="top"></a>$top
Verwenden Sie, um die maximale Anzahl von Elementen in einem Resultset zurückzugebenden angeben, die Abfrageoption **$top** . Die Abfrageoption **$top** identifiziert eine Teilmenge in der Auflistung. Diese Teilmenge wird gebildet, indem Sie nur die ersten N Elemente des Satzes, wobei N eine positive ganze Zahl, die von dieser Abfrageoption angegebene ist auswählen. Beispielsweise lautet die ersten fünf Nachrichten im Postfach des Benutzers zurück, die Syntax wie folgt:

```http
GET https://graph.microsoft.com/v1.0/me/messages?$top=5
```

### <a name="skip"></a>$skip
Um die Anzahl von Elementen, die vor dem Abrufen von Elementen in einer Auflistung übersprungen festzulegen, verwenden Sie die Abfrageoption **$skip** . Beispielsweise ist, um Ereignisse nach Erstellungsdatum sortiert und beginnend mit dem 21. Ereignis zurückzugeben, die Syntax wie folgt.

```http
GET  https://graph.microsoft.com/v1.0/me/events?$orderby=createdDateTime&$skip=20
```

### <a name="skiptoken"></a>$skipToken
Verwenden Sie um Seite aus, und geben Sie die nächste zurückzugebender Ergebnisse an, die Abfrageoption **$skipToken** ein.  Der Wert der Abfrageoption **$skipToken** ist ein Token, die als Ausgangspunkt in einer Auflistung identifiziert. Beispielsweise könnte der Wert der Abfrageoption **$skipToken** des ersten Elements in einer Auflistung oder das 8. Element in einer Auflistung mit 20 Elementen oder einer anderen Stelle innerhalb der Auflistung identifizieren.

Da der Wert der Abfrageoption **$skipToken** einen Index in einer Auflistung identifiziert, identifiziert es in der Abfrage verwendet eine Teilmenge der Elemente. Teilmenge identifiziert beginnt das erste Element im Index (identifiziert durch den Wert der Abfrageoption **$skipToken** ) über das letzte Element in der Sammlung.

Einige Reaktion sehen Sie ein `@odata.nextLink` Wert. Einige enthalten eines **$skipToken** -Werts.  Der Wert **$skipToken** ist wie eine Markierung, die dem Dienst anweist, wo Fortsetzen der Ergebnisse für die nächsten ist.  Im folgenden ist ein Beispiel für eine `@odata.nextLink` Wert aus einer Antwort.

```
"@odata.nextLink": "https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27"
```

Beispielsweise ist die nächste Gruppe von Benutzern in Ihrer Organisation, die Begrenzung auf 3 zu einem Zeitpunkt in den Ergebnissen zurückgegeben, um die Syntax wie folgt.

```http
GET  https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27
```

### <a name="count"></a>$count
Verwenden Sie **$count** als einen Abfragezeichenfolgen-Parameter, wie im folgenden Beispiel dargestellt:
```http
GET  https://graph.microsoft.com/v1.0/me/contacts?$count=true
```
die würde sowohl die **Kontakte** -Auflistung und die Anzahl der Elemente in der Auflistung **Kontakte** im Zurückgeben der `@odata.id` Eigenschaft.

Hinweis: Dies ist nicht für [DirectoryObject](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/directoryobject) Auflistungen unterstützt.
