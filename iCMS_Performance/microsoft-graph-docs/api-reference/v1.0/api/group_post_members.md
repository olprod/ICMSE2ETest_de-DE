# <a name="add-member"></a>Mitglied hinzufügen

Verwenden Sie diese API, um ein Mitglied einer Office 365, eine Sicherheitsgruppe oder eine e-Mail-aktivierte Sicherheitsgruppe über die Navigationseigenschaft **Mitglieder** hinzufügen. Sie können Benutzer oder andere Gruppen hinzufügen. Wichtig: Sie können nur von Benutzern zu Gruppen von Office 365 hinzufügen.

## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen: *Group.ReadWrite.All* oder *Directory.ReadWrite.All* oder *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/members/$ref
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | Bearer <token>. Erforderlich. |

## <a name="request-body"></a>Anforderungstext
Geben Sie im Textkörper Anforderung eine JSON-Darstellung eines Objekts [DirectoryObject](../resources/directoryobject.md), [Benutzer](../resources/user.md) oder eine [Gruppe](../resources/group.md) hinzugefügt werden soll.


## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `204, No Content` Antwortcode. Es gibt keine Suchzeichenfolge im Antworttext zurück.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_directoryobject_from_group"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/members/$ref
Content-type: application/json
Content-length: 30

{
  "@odata.id": "https://graph.microsoft.com/v1.0/directoryObjects/<id>"
}
```
Geben Sie im Textkörper Anforderung eine JSON-Darstellung der die `id` des Objekts [DirectoryObject](../resources/directoryobject.md), [Benutzer](../resources/user.md) oder [Gruppe](../resources/group.md) hinzufügen möchten.
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directoryObject"
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create member",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->