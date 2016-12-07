# <a name="groups-plans-and-tasks"></a>Groups, Plans and Tasks
The new Office 365 Tasks API enables you to create tasks and assign them to users in a group in Office 365.

## <a name="basics"></a>Basics
Before you get started with trying out the Tasks API, it is worth understanding how the main objects in Tasks API relate to each other as well as Office 365 groups.

## <a name="groups"></a>Gruppen
Office 365 groups are the owners of the plans in the Tasks API. Today, each group can own no more than one plan. To get the plans owned by a group, make the HTTP request below.

```http
GET /groups/<id>/plans
```
When creating a new plan, you need to make a group its owner by simply setting the `owner` property on a plan object to the id of a group object if the group does not already own a plan. 

**Note that you need to ensure that the user who is creating the plan is a member of the group. When you create a new group using the API, you are not automatically added to the group as a member. This has to be done using a separate API call.** 

## <a name="plans"></a>Plans
Plans are the containers of tasks. To create a task in a group, set the `planId` property on the task object to the id of the plan objected owned by the group. To retrieve the tasks in a plan, make the HTTP request below.

```http
GET /plans/<id>/tasks
```
Each plan also has a plan details object which is created together with the plan object. To access the plan details object, make the following HTTP request.

```http
GET /plans/<id>/details
```

## <a name="tasks"></a>Aufgaben
Each task can be assigned to a user by setting the `assignedTo` property on the task object to the id of the user object. It also has a task details object which is created together with the task object. To access the task details object, make the following HTTP request.

```http
GET /tasks/<id>/details
```

## <a name="api-reference"></a>JavaScript-API-Referenz
Unter den im folgenden aufgeführten Links werden die in den APIs zur Verfügung stehenden Excel-Objekte auf hoher Ebene Excel-Objekte erläutert. Auf jeder Seite sind eine Beschreibung der Eigenschaften, das Verhältnis und verfügbare Methoden des Objekts enthalten. Erkunden Sie diese Links, um mehr zu erfahren.