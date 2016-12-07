# <a name="microsoft-graph-optional-query-parameters"></a>Optionale Abfrageparameter in Microsoft Graph 
## <a name="optional-odata-query-parameters"></a>Optionale OData-Abfrageparameter
Microsoft Graph stellt mehrere optionale Abfrageparameter bereit, die Sie zum Festlegen und Steuern der in einer Antwort zurückgegebenen Datenmenge verwenden können. Microsoft Graph unterstützt die folgenden Abfrageoptionen. 

|Name|Wert|Beschreibung|
|:---------------|:--------|:-------|
|select|Zeichenfolge|Durch Trennzeichen getrennte Liste der Eigenschaften, die in der Antwort aufgenommen werden.|
|expand|Zeichenfolge|Durch Trennzeichen getrennte Liste der Beziehungen, die in der Antwort erweitert und aufgenommen werden.  |
|orderby|Zeichenfolge|Durch Trennzeichen getrennte Liste von Eigenschaften, die zum Sortieren der Elemente in der Antwortsammlung verwendet werden.|
|Filter|Zeichenfolge|Filtert die Antwort basierend auf einer Reihe von Kriterien.|
|top|Ganzzahl|Die Anzahl der Elemente, die in einem Resultset zurückgegeben werden.|
|skip|Ganzzahl|Die Anzahl der Elemente, die in einem Resultset übersprungen werden.|
|$skipToken|Zeichenfolge|Pagingtoken, das zum Abrufen des nächsten Resultsets verwendet wird.|
|count|Keine|A collection and the number of items in the collection.|


**Encoding query parameters**

- If you are trying out query parameters in the [Microsoft Graph Explorer](https://graphexplorer2.azurewebsites.net/), you can just copy and paste the examples below without applying any URL-encoding to the query string. The following example works fine _in the Graph Explorer_ without encoding the space and quote characters:
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 
- In general, when specifying query parameters _in your app_, make sure you appropriately encode characters that are [reserved for special meanings in an URI](https://tools.ietf.org/html/rfc3986#section-2.2). For example, encode the space and quote characters in the last example, as shown below:
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address%20eq%20%27jon@contoso.com%27
```

### <a name="select"></a>select
Verwenden Sie zum Festlegen einer zurückzugebenden Teilmenge von Eigenschaften die **$select**-Abfrageoption. Wenn Sie z. B. Ihre Nachrichten abrufen, möchten Sie ggf. festlegen, dass nur die Eigenschaften **Von** und **Betreff** der Nachrichten zurückgegeben werden.

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

### <a name="expand"></a>expand

In Microsoft Graph-API-Anforderungen werden untergeordnete Sammlungen von Elementen, auf die verwiesen wird, nicht automatisch erweitert. Dies ist so beabsichtigt, da so der Netzwerkdatenverkehr und die Zeit zum Generieren einer Antwort aus dem Dienst reduziert werden. Möglicherweise möchten Sie jedoch in einigen Fällen diese Ergebnisse in einer Antwort einbeziehen.

Sie können den **$expand**-Abfragezeichenfolgen-Parameter verwenden, um die API zum Erweitern einer untergeordneten Sammlung und zum Einbeziehen dieser Ergebnisse anzuweisen.

Verwenden Sie beispielsweise zum Abrufen von Stammlaufwerkinformationen und der Elemente auf oberster Ebene in einem Laufwerk den **$expand**-Parameter. In diesem Beispiel wird auch eine **$select**-Anweisung verwendet, um nur die Eigenschaften_ID_ und _Name_ der untergeordneten Elemente zurückzugeben.

```http
GET https://graph.microsoft.com/v1.0/me/drive/root?$expand=children($select=id,name)
```

>  **Hinweis**: Die maximale Anzahl der zurückgegebenen Objekte für eine Anforderung beträgt 20. 

> Also, if you query on the [user](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/user) resource, you can use **$expand** to get the properties of only one child object or collection at a time. 

The following example gets **user** objects, each with up to 20 **directReport** objects in the **directReports** collection expanded:
```http
GET https://graph.microsoft.com/v1.0/users?$expand=directReports
```
Some other resources may have a limit as well, so always check for possible errors.


<!---The following shows a sample result that is returned in the response body.-->


### <a name="orderby"></a>orderby

To specify the sort order of the items returned from the API, use the **$orderby** query option. 

Wenn die zurückgegebenen Benutzer in der Organisation nach dem Anzeigenamen sortiert werden sollen, lautet die Syntax hierfür wie folgt:

```http
GET https://graph.microsoft.com/v1.0/users?$orderBy=displayName
``` 

You can also sort by complex type entities. The following example gets messages and sorts them by the **address** field of the **from** property, which is of the complex type **emailAddress**:

```http
GET https://graph.microsoft.com/v1.0/me/messages?$orderBy=from/emailAddress/address
``` 

Verwenden Sie zum Festlegen der Sortierreihenfolge der aus der API zurückgegebenen Elemente die $orderby-Abfrageoption. Wenn Sie die Ergebnisse in aufsteigender oder absteigender Reihenfolge sortieren möchten, fügen Sie entweder asc`asc` oder desc`desc` an den Namen des Felds getrennt durch ein Leerzeichen an, Beispiel:

 >  **Hinweis**: **$orderby** kann nicht zusammen mit $filter-Ausdrücken verwendet werden.

### <a name="filter"></a>Filter
Wenn Sie die zurückgegebenen Daten anhand bestimmter Kriterien filtern möchten, verwenden Sie die **$filter**-Abfrageoption. Wenn die zurückgegebenen Benutzer in der Organisation anhand des Anzeigenamens gefiltert werden sollen, der mit „Garth“ beginnt, lautet die Syntax hierfür wie folgt:

```http
GET https://graph.microsoft.com/v1.0/users?$filter=startswith(displayName,'Garth')
```

You can also filter by complex type entities. The following example returns messages that has the **address** field of the **from** property equal to "jon@contoso.com". The **from** property is of the complex type **emailAddress**.

```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 

### <a name="top"></a>top
Verwenden Sie zum Festlegen der maximalen Anzahl der in einem Resultset zurückzugebenden Elemente die **$top**-Abfrageoption. Die **$top**-Abfrageoption ermittelt eine Teilmenge in der Sammlung. Diese Teilmenge setzt sich aus den festgelegten ersten N Elementen zusammen, wobei N eine positive ganze Zahl ist, die durch diese Abfrageoption angegeben ist. Wenn beispielsweise die ersten fünf Nachrichten im Postfach des Benutzers zurückgegeben werden sollen, lautet die Syntax wie folgt:

```http
GET https://graph.microsoft.com/v1.0/me/messages?$top=5
```

### <a name="skip"></a>skip
Verwenden Sie zum Festlegen der Anzahl der Elemente, die vor dem Abrufen von Elementen in einer Sammlung übersprungen werden sollen, die **$skip**-Abfrageoption. Wenn die zurückgegebenen Ereignisse nach Erstellungsdatum sortiert werden, wobei mit dem 21. Ereignis begonnen wird, lautet die Syntax wie folgt.

```http
GET  https://graph.microsoft.com/v1.0/me/events?$orderby=createdDateTime&$skip=20
```

### <a name="skiptoken"></a>$skipToken
Verwenden Sie zum Paginieren und Festlegen des nächsten zurückzugebenden Resultsets die **$skipToken**-Abfrageoption.  Der Wert einer **$skipToken**-Abfrageoption ist ein Token, das einen Startpunkt in einer Sammlung festlegt. Der Wert einer **$skipToken**-Abfrageoption könnte z. B. das erste Element in einer Sammlung oder das achte Elements in einer Sammlung mit 20 Elementen oder eine andere Position in der Sammlung angeben.

Da der Wert einer **$skipToken**-Abfrageoption einen Index in einer Sammlung ermittelt, wird bei deren Verwendung in Ihrer Abfrage eine Teilmenge der Elemente ermittelt. Die ermittelte Teilmenge beginnt beim ersten Element im Index (ermittelt durch den Wert der **$skipToken**-Abfrageoption) und endet beim letzten Element im Set.

In einigen Fällen wird ein @odata.nextLink`@odata.nextLink`-Wert angezeigt. Manchmal ist ein **$skipToken**-Wert enthalten.  Der **$skipToken**-Wert stellt eine Markierung für den Dienst dar, die angibt, an welcher Stelle das nächste Resultset beginnen soll.  Im Folgenden sehen Sie ein Beispiel eines @odata.nextLink`@odata.nextLink`-Werts aus einer Antwort.

```
"@odata.nextLink": "https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27"
```

Wenn das nächste Set von Benutzern in Ihrer Organisation zurückgegeben werden soll und dabei nie mehr als drei Benutzer auf einmal in den Ergebnissen angezeigt werden sollen, lautet die Syntax wie folgt.

```http
GET  https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27
```

### <a name="count"></a>count
Use **$count** as a query parameter as in the following example:
```http
GET  https://graph.microsoft.com/v1.0/me/contacts?$count=true
```
which would return both the **contacts** collection, and the number of items in the **contacts** collection in the `@odata.id` property.

Note: This is not supported for [directoryObject](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/directoryobject) collections.
