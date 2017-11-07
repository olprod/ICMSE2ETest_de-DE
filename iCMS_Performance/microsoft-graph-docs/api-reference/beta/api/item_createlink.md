# <a name="create-a-sharing-link-for-a-driveitem"></a>Erstellen Sie einen Link Freigabe für eine driveItem

**CreateLink** -Aktion können Sie ein Element über einen Link freigeben.

Die Aktion **CreateLink** erstellt eine neue Verknüpfung für die Freigabe, sofern der angegebenen Linktyp für die aufrufende Anwendung nicht bereits vorhanden ist. Wenn eine Freigabe Verknüpfung des angegebenen Typs für die app bereits vorhanden ist, werden die vorhandene Verknüpfung auf der Freigabe zurückgegeben.

Elementen erben die Berechtigungen von ihrer Vorgänger.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/items/{item-id}/createLink
POST /me/drive/root:/{item-path}:/createLink
POST /groups/<id>/drive/items/<item-id>/createLink
```

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Der Text der Anforderung definiert den Typ der Verknüpfung, die für Ihre Anwendung Ansichtsseite Freigabe. Die Anforderung sollte mit dieser Eigenschaft ein JSON-Objekt sein.

| Name   | Typ   | Beschreibung                                                          |
|:-------|:-------|:---------------------------------------------------------------------|
| **Typ** | string | Der Typ der Freigabe Link zu erstellen. Either `view`, `edit`, or `embed`. |
| **Bereich** | string | Der Bereich der Link zu erstellen. Entweder `anonymous` oder `organization`. Optional |

## <a name="link-types"></a>Link-Typen
**Type** -Parameter sind die folgenden Werte zulässig.

| Wert der Type | Beschreibung                                                                                  |
|:-----------|:---------------------------------------------------------------------------------------------|
| `view`     | Erstellt eine Verknüpfung schreibgeschützt für das Element.                                                        |
| `edit`     | Erstellt eine Verknüpfung Lese-/ Schreibzugriff auf das Element.                                                       |
| `embed`    | Erstellt einen embeddable Link zum Element. Diese Option ist nur verfügbar für OneDrive Personal. |

## <a name="scope-types"></a>Bereichs-Typen
Die folgenden Werte sind für **die Bereichsparameter** zulässig. Dies ist ein optionaler Parameter. Wenn der **Bereich** -Parameter nicht angegeben wird, wird der am wenigsten restriktiven Link erstellt werden.

| Wert der Type     | Beschreibung                                                                                                                   |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------|
| `anonymous`    | Erstellt eine Verknüpfung mit dem Element für alle Benutzer zugänglich ist. Anonyme Links können vom mandantenadministrator deaktiviert werden.                 |
| `organization` | Erstellt eine Verknüpfung mit dem Element in einer Organisation zugegriffen werden kann. Organisation Link Bereich ist nicht verfügbar für OneDrive Personal. |

## <a name="response"></a>Antwort

Bei erfolgreicher gibt diese Methode eine einzelne [Berechtigung](../resources/permission.md) Ressource in den Antworttext, der die angeforderte Berechtigung der Anwendungsfreigabe Link darstellt.

Der Dienst zuerst sehen Sie sich die aktuellen Berechtigungen und überprüfen Sie, sofern bereits vorhanden, die den gleichen **Typ** für die aufrufende Anwendung hat.

Die Antwort wird `201 Created` Wenn einen neuen Funktionen zur Freigabe Verknüpfung für das Element erstellt oder `200 OK` Wenn eine vorhandene Verknüpfung zurückgegeben wird.

## <a name="example"></a>Beispiel
Es folgt ein Beispiel dafür, wie Sie diese API-aufrufen.

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

<!-- {
  "blockType": "request",
  "name": "item_createlink"
}-->
```http
POST /drive/root:/{item-path}:/createLink
Content-type: application/json

{
  "type": "view",
  "scope": "anonymous"
}
```

##### <a name="response"></a>Antwort

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.permission" } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "123ABC",
  "roles": ["write"],
  "link": {
    "type": "view",
    "scope": "anonymous",
    "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
    "application": {
      "id": "1234",
      "displayName": "Sample Application"
    },
  }
}
```

## <a name="creating-company-sharable-links"></a>Erstellen von Unternehmen freigegeben werden links

OneDrive für Unternehmen und SharePoint unterstützen Unternehmen freigegeben werden Links. Diese ähneln anonyme Links, außer sie nur für Mitglieder des übergeordneten Mandanten funktionieren. Verwenden Sie zum Erstellen eines Unternehmens freigegeben werden Links **der Bereichsparameter** mit dem Wert `organization`.

## <a name="http-request"></a>HTTP-Anforderung

<!-- { "blockType": "request", "name": "create-link-scoped", "scopes": "files.readwrite service.sharepoint" } -->
```http
POST /drive/items/{item-id}/action.createLink
Content-Type: application/json

{
  "type": "edit",
  "scope": "organization"
}
```

## <a name="http-response"></a>HTTP-Antwort

Die Antwort werden `201 Created` Wenn einen neuen Funktionen zur Freigabe Verknüpfung für das Element erstellt oder `200 OK` Wenn eine vorhandene Verknüpfung zurückgegeben wird.

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.permission" } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "123ABC",
  "roles": ["write"],
  "link": {
    "type": "view",
    "scope": "organization",
    "webUrl": "https://contoso-my.sharepoint.com/personal/ellen_contoso_com/...",
    "application": {
      "id": "1234",
      "displayName": "Sample Application"
    },
  }
}
```

## <a name="embeddable-links"></a>Embeddable links

Bei Verwendung der `embed` Verknüpfungstyp, der WebUrl zurückgegeben eingebettet werden kann, einer `<iframe>` HTML-Element. Beim Erstellen einer Verknüpfung auf der Embed der `webHtml` -Eigenschaft enthält den HTML-Code für eine `<iframe>` den Inhalt hosten.

**Hinweis:** Einbetten von Links werden nur für OneDrive Personal unterstützt.

## <a name="programming-notes"></a>Programmierung Notizen

Anwendungsfreigabe mit dieser Aktion erstellten Hyperlinks laufen nicht ab. Sie sind in die Freigabeberechtigungen für das Element sichtbar und können durch einen Besitzer des Elements entfernt werden.
Sharing Links zeigen immer auf die aktuelle Version eines Elements, es sei denn, das Element (nur SharePoint) aktiviert ist.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item: createLink",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Create sharing link"
} -->
