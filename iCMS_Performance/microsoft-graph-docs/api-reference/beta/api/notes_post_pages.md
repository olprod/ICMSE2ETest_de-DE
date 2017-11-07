# <a name="create-page"></a>Seite "erstellen"

Erstellen einer neuen OneNote-Seite im Standardabschnitt die Standardnotizbuch.

Um eine Seite in eine andere Position in der Standardnotizbuch erstellen, können Sie die `sectionName` Parameter Abfragen.  Beispiel:`../notes/pages?sectionName=My%20section`

Die `POST /notes/pages` Vorgang wird nur zum Erstellen von Seiten in Standard-Notizbuch des aktuellen Benutzers verwendet. Wenn Sie andere Notizbücher vorgesehenen können Sie die [Seiten in einem angegebenen Abschnitt erstellen](../api/section_post_pages.md).           
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:  
Notes.Create, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->

```http
POST /me/notes/pages
POST /users/<id | userPrincipalName>/notes/pages
POST /groups/<id>/notes/pages
```

## <a name="request-headers"></a>Anforderungsheader  
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer haben Zugriff autorisiert. |
| Inhaltstyp | string | `text/html`oder `application/xhtml+xml` für den HTML-Inhalt, einschließlich für die erforderliche Komponente "Presentation" multipart Anforderungen. Multipart fordert die Verwendung der `multipart/form-data; boundary=your-boundary` Inhaltstyp. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung des HTML-Inhalts für die Seite ein.

Der Text kann HTML direkt im Textkörper Anforderung platziert enthalten, oder ein Format für mehrteilige Nachrichten enthalten wie im Beispiel dargestellt. Wenn Sie binäre Daten senden, müssen Sie eine Anforderung für mehrteilige senden.

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `201 Created` Antwortcode und das neue [Page](../resources/page.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.

In der `../notes/pages` Pfad, Sie können die `sectionName` Abfrage Parameter, um eine Seite in einem bestimmten Abschnitt in der Standardnotizbuch erstellen. Beispiel: `../notes/pages?sectionName=My%20section`. Im Abschnitt nicht vorhanden ist (oder umbenannt wurde), wird die API Erstellen eines neuen Abschnitts.

<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/notes/pages
Content-length: 312
Content-type: multipart/form-data; boundary=MyPartBoundary198374

--MyPartBoundary198374
Content-Disposition:form-data; name="Presentation"
Content-Type:text/html

<!DOCTYPE html>
<html>
  <head>
    <title>A page with <i>rendered</i> images and an <b>attached</b> file</title>
    <meta name="created" content="2015-07-22T09:00:00-08:00" />
  </head>
  <body>
    <p>Here's an image from an online source:</p>
    <img src="http://..." alt="an image on the page" width="500" />
    <p>Here's an image uploaded as binary data:</p>
    <img src="name:imageBlock1" alt="an image on the page" width="300" />
    <p>Here's a file attachment:</p>
    <object data-attachment="FileName.pdf" data="name:fileBlock1" type="application/pdf" />
  </body>
</html>

--MyPartBoundary198374
Content-Disposition:form-data; name="imageBlock1"
Content-Type:image/jpeg

... binary image data ...

--MyPartBoundary198374
Content-Disposition:form-data; name="fileBlock1"
Content-Type:application/pdf

... binary file data ...

--MyPartBoundary198374--
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 312

{
  "title": "title-value",
  "createdByAppId": "createdByAppId-value",
  "links": {
    "oneNoteClientUrl": {
      "href": "href-value"
    },
    "oneNoteWebUrl": {
      "href": "href-value"
    }
  },
  "contentUrl": "contentUrl-value",
  "content": "content-value",
  "lastModifiedTime": "datetime-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->