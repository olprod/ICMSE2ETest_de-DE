# <a name="identifiers-in-tasks"></a>Bezeichner in Aufgaben

Bezeichner für Objekte in Aufgaben sind Zeichenfolgenwerte Dienst generiert. . Die Werte sind 28 Zeichen lang sein und Groß-/Kleinschreibung beachtet. Wenn als übergeben, wird der Dienst eine einfache Format Validierung des Bezeichners, vorgehen, wenn Format Überprüfung fehlschlägt, die Anrufer Bad Request (400) Fehler, der angibt, des Problems beantwortet werden. Diese Fehlermeldung gibt einen Fehler in der aufrufenden Anwendung, wie an:

- Die aufrufende Anwendung verarbeitet den Bezeichner als String Groß-/Kleinschreibung nicht beachtet. Bezeichner in Aufgaben Groß-/Kleinschreibung beachtet.
- Die aufrufende Anwendung gekürzt den Bezeichner. Bezeichner in Aufgaben sind 28 Zeichen lang sein darf.
- Die aufrufende Anwendung versucht, einen Bezeichner für ein Objekt im Aufgaben zu generieren. Generiert Client-IDs werden nicht akzeptiert. Alle Bezeichner werden vom Dienst nach der Erstellung der Objekte generiert.

Diese Überprüfung ist **nicht über eine Sicherheitsfunktion**. Hierbei handelt es sich nur Applications zu allgemeinen Bezeichner informieren Verwandte Probleme bei der Entwicklung der Anwendung, die andernfalls schwer zu identifizieren sind.