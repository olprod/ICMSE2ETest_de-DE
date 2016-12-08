# <a name="groups-plans-and-tasks"></a>Gruppen, Pläne und Aufgaben
Der neuen Office 365-Aufgaben-API ermöglicht Ihnen das Erstellen von Aufgaben, und weisen Sie diese Benutzer in einer Gruppe im Office 365.

## <a name="basics"></a>Grundlagen
Bevor Sie beginnen, mit der API Aufgaben und probieren Sie lohnt Grundlegendes zur Beziehung zwischen der wichtigsten Objekte im Aufgaben-API und miteinander als auch für Office 365-Gruppen.

## <a name="groups"></a>Gruppen
Office 365-Gruppen sind die Besitzer der Pläne in der Tasks-API.
Jede Gruppe kann heute nicht mehr als einen Plan besitzen.
Um die Pläne Besitz einer Gruppe zu erzielen, sollten Sie die folgenden HTTP-Anforderung.

```http
GET /groups/<id>/plans
```
Wenn Sie einen neuen Plan zu erstellen, müssen Sie einer Gruppe Besitzer indem Sie einfach Festlegen der `owner` -Eigenschaft für ein Objekt Plan auf die Id des ein Group-Objekt, wenn die Gruppe nicht bereits einen Plan besitzt. 

**Hinweis: Sie müssen sicherstellen, dass der Benutzer, der den Plan erstellen ist ein Mitglied der Gruppe ist. Wenn Sie eine neue Gruppe mit der API erstellen, werden Sie nicht automatisch an die Gruppe als Mitglied hinzugefügt. Dies hat, erfolgt eine separate API-Aufruf.** 

## <a name="plans"></a>Pläne
Pläne sind die Container von Aufgaben. Legen Sie zum Erstellen einer Aufgabe in einer Gruppe, die `planId` Eigenschaft des Task-Objekts auf die Id des Plans erhob Besitz der Gruppe.
Stellen Sie zum Abrufen der Aufgaben in einem Plan für die folgenden HTTP-Anforderung.

```http
GET /plans/<id>/tasks
```
Jeden Plan hat auch ein Plan Details Objekt die zusammen mit dem Plan Objekt erstellt wird. Um den Plan Details Objekt zuzugreifen, stellen Sie die folgenden HTTP-Anforderung.

```http
GET /plans/<id>/details
```

## <a name="tasks"></a>Aufgaben
Jede Aufgabe kann, die einem Benutzer zugewiesen werden, durch Festlegen der `assignedTo` -Eigenschaft für das Task-Objekt auf die Id des User-Objekts. Es wurde auch ein Task Details-Objekt, die zusammen mit der Task-Objekt erstellt wird. Um die Details Task-Objekt zuzugreifen, stellen Sie die folgenden HTTP-Anforderung.

```http
GET /tasks/<id>/details
```

## <a name="api-reference"></a>-API-Referenz
Die Links auf der linken Seite zeigen die Objekte in der API Aufgaben zur Verfügung. Jeder Seite-Verknüpfung enthält eine Beschreibung der Eigenschaften, Beziehungen und Methoden für das Objekt verfügbar.
Verwenden Sie die Links auf der linken Seite, um mehr zu erfahren.