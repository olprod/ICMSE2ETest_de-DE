# <a name="externalreferencecollection-resource-type"></a>Ressourcentyp externalReferenceCollection

Die Ressource ExternalReferenceCollection * stellt die Auflistung von Verweisen auf eine Aufgabe. Es ist Teil des [Aufgabendetails](taskdetails.md) -Objekts. Der Wert in der Eigenschaft-Wert-Paar ist das [ExternalReference](externalreference.md) -Objekt.

* Beachten Sie, dass dies vom Typ geöffnet ist.

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.externalReferenceCollection"
}-->


```json
{
  "String-value":
  {
    "alias": "String-value",
    "lastModifiedBy": "String-value",
    "lastModifiedDateTime": "String(timestamp)",
    "previewPriority": "String-value",
    "type": "String-value"
  }
}
```

Beispiel

```json
{
  "https%3A//contoso%2Esharepoint%2Ecom/teams/agile/documents/AnnualReport%2Epptx":
  {
    "@odata.type": "microsoft.graph.externalReference", // required in PATCH requests to edit the references on a task
    "alias": "Agile Team Annual Report",
    "lastModifiedBy": "1e9955d2-6acd-45bf-86d3-b546fdc795eb",
    "lastModifiedDateTime": "2015-09-21T17:45:12.039Z",
    "previewPriority": "0009005756397228702",
    "type": "PowerPoint"
  }
}

```

## <a name="properties"></a>Eigenschaften
Eigenschaften vom Typ Open können vom Client definiert werden. In diesem Fall muss der Client bereitstellen, **gültige URLs** basierend auf **HTTP/HTTPS** -Protokolle als Eigenschaften und deren Werte muss die [ExternalReference](externalreference.md) -Objekte. Basierend auf OData, Eigenschaftennamen im offenen Typen die folgenden Zeichen nicht enthalten: `.`, `:`, `%` , sodass sie codiert werden müssen. Beispiel wird oben angezeigt. Um einen Verweis zu entfernen, legen Sie den Wert der Eigenschaft`null`

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "externalReferenceCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->