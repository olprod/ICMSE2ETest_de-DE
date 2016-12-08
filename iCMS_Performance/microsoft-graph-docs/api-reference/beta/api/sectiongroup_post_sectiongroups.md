# <a name="create-sectiongroup"></a>SectionGroup erstellen

Erstellen Sie eine neue [Abschnittsgruppe im](../resources/sectiongroup.md) in der angegebenen Abschnittsgruppe aus.
## <a name="prerequisites"></a>Voraussetzungen
Einen der folgenden **Bereiche** ist erforderlich, um diese API ausführen:   
Notes.Create, Notes.ReadWrite.CreatedByApp, Notes.ReadWrite oder Notes.ReadWrite.All
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/sectionGroups/<id>/sectionGroups
POST /users/<id | userPrincipalName>/notes/sectionGroups/<id>/sectionGroups
POST /groups/<id>/notes/sectionGroups/<id>/sectionGroups
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Typ | Beschreibung|
|:---------------|:--------|:----------|
| Autorisierung  | string  | `Bearer <token>`Ein gültiges OAuth-Token bereitgestellt, um die app basierend auf die Anmeldeinformationen des Benutzers und der Benutzer mit dem autorisierter Zugriff. |
| Inhaltstyp | string | `application/json` |

## <a name="request-body"></a>Anforderungstext
Geben Sie einen Namen für den Abschnittsgruppe im Textkörper Anforderung.

Innerhalb der gleichen Hierarchieebene müssen Abschnitt Gruppennamen eindeutig sein. Der Name kann nicht mehr als 50 Zeichen enthalten oder die folgenden Zeichen enthalten: ? *\/: <> | & #'' % ~

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode einen `201 Created` Antwortcode und ein [SectionGroup](../resources/sectiongroup.md) -Objekt aus der Antwort.

## <a name="example"></a>Beispiel
##### <a name="request"></a>Anforderung
Es folgt ein Beispiel der Anforderung.
<!-- {
  "blockType": "request",
  "name": "create_sectiongroup_from_sectiongroup"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/sectionGroups/<id>/sectionGroups
Content-type: application/json
Content-length: 30

{
  "name": "Section group name"
}
```
##### <a name="response"></a>Antwort
Es folgt ein Beispiel der Antwort. Hinweis: Das hier gezeigte Response-Objekt wird aus Platzgründen Zahl gekürzt. Alle Eigenschaften werden von einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.sectiongroup"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 305

{
  "sectionsUrl": "sectionsUrl-value",
  "sectionGroupsUrl": "sectionGroupsUrl-value",
  "name": "name-value",
  "createdBy": "createdBy-value",
  "createdByIdentity": {
    "user": {
      "id": "id-value",
      "displayName": "displayName-value"
    }
  },
  "lastModifiedBy": "lastModifiedBy-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create SectionGroup",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->