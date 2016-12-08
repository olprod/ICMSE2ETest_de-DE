# <a name="get-a-special-folder-by-name"></a>Einen Ordner mit Sonderfunktion nach Namen erhalten möchten

Verwenden Sie die spezielle-Auflistung, um einen Ordner mit Sonderfunktion namentlich zuzugreifen.

Spezialordner bieten einfache Aliase Zugriff auf bekannte Ordner in OneDrive ohne die Notwendigkeit zum Nachschlagen von den Ordner durch Pfad (die Lokalisierung erforderlich ist) oder verweisen auf den Ordner mit einer ID Ein Ordner mit Sonderfunktion umbenannt oder an eine andere Position innerhalb des Laufwerks verschoben wird, wird diese Syntax weiterhin den Ordner suchen.

Spezialordner werden automatisch beim ersten erstellt, die eine Anwendung zum Schreiben in ein einziges versucht, sofern er nicht bereits vorhanden. Wenn ein Benutzer eine löscht, wird es neu erstellt, wenn nicht neu geschrieben.

**Hinweis:**  Wenn Sie nur über Leseberechtigungen und anfordern einen speziellen Ordner, die nicht vorhanden ist, erhalten Sie eine `403 Forbidden` Fehler.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/special/<name>
```
## <a name="optional-query-parameters"></a>Optional Abfrageparameter
Diese Methode unterstützt die [OData-Abfrage-Parameter](http://graph.microsoft.io/docs/overview/query_parameters) , mit denen die Antwort anpassen.

## <a name="request-headers"></a>Anforderungsheader

| Name          | Typ   | Beschreibung               |
|:--------------|:-------|:--------------------------|
| Autorisierung | string | Bearer <token>. Erforderlich. |


## <a name="request-body"></a>Anforderungstext
Geben Sie einen Anforderungstext für diese Methode nicht.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `200 OK` Antwortcode und eines [DriveItem](../resources/driveitem.md) -Objekts in der Antworttext.

## <a name="example"></a>Beispiel

##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung für den Laufwerken des Benutzers.

<!-- {
  "blockType": "request",
  "name": "get_drive_special"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/drive/special/<name>
```

##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "folder": { },
  "id": "s!lkjqwlkj124912049an",
  "name": "Photos",
  "specialFolder": { "name": "photos" },
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/Photos",
}
```

## <a name="example-head-requests-for-special-folders"></a>Beispiel HEAD-Anfragen für Spezialordner

Wenn Sie einen Ordner mit Sonderfunktion, der nicht anfordern mithilfe einer GET-Anforderung vorhanden ist, wird der Ordner mit Sonderfunktion automatisch für Sie erstellt. Sie können testen, um festzustellen, ob der spezielle Ordner vorhanden ist, indem Sie eine HEAD-Anforderung. HEAD-Anforderung wird zurückgegeben, wenn der Ordner nicht vorhanden ist, eine `404` Antwort.

##### <a name="request-folder-does-not-exist"></a>Anfordern (Ordner ist nicht vorhanden)

<!-- { "blockType": "request", "name": "head-does-not-create-special-folder" } -->
```
HEAD /drive/special/{special-folder-name}
```

##### <a name="response"></a>Antwort
<!-- {"blockType": "response"} -->
```
HTTP/1.1 404 Not Found
```

##### <a name="request-folder-does-exist"></a>Anfordern (Ordner existiert)

Die gleiche Anforderung senden, wenn der Ordner bereits vorhanden ist zurückgegebenen andererseits, eine `200 OK` Antwort.

<!-- { "blockType": "request", "name": "head-existing-special-folder", "scopes": "files.read" } -->
```
HEAD /drive/special/{special-folder-name}
```

##### <a name="response"></a>Antwort

<!-- {"blockType": "response", "isEmpty": true } -->
```
HTTP/1.1 200 OK
```

## <a name="remarks"></a>Hinweise

Um die untergeordneten Elemente einen Ordner mit Sonderfunktion anfordern, können Sie anfordern der `children` -Auflistung oder verwenden Sie die Option [Erweitern](http://graph.microsoft.io/docs/overview/query_parameters) , um die Auflistung untergeordneter Elemente zu erweitern.


<!-- {
  "type": "#page.annotation",
  "description": "List drives",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Get special folder"
}-->
