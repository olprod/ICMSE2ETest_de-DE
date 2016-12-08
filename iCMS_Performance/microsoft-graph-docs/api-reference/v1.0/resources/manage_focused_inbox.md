# <a name="manage-focused-inbox"></a>Verwalten von zielgerichteten Posteingang

Fokussierte Posteingang können Sie wichtige Nachrichten in Anzeigen der `Focused` auf der Registerkarte Posteingang und dem Rest der Posteingangsnachrichten in der `Other` Registerkarte. Das Klassifizierungssystem organisiert anfänglich Nachrichten im Posteingang in einer standardmäßigen Weise. Können Sie beheben und das System über einen Zeitraum über die Benutzeroberfläche oder programmgesteuert Schulen. Je mehr Sie verwenden, desto höher kann das System die eingehende Nachricht als wichtig ableiten.

Ebene der programmgesteuerten praxisorientierte Posteingang REST-API für den angegebenen Benutzer Nachrichten funktioniert und unterstützt eine **InferenceClassification** -Eigenschaft für jede Nachricht. Die möglichen Werte sind `Focused` und `Other`, die angeben, ob der Benutzer die Nachricht als, jeweils wichtiger und weniger wichtig berücksichtigt. An den richtigen wie das System eine Nachricht, [Aktualisieren Sie die Eigenschaft InferenceClassification dieser Nachricht](../api/message_update.md)klassifiziert. Im Laufe der Zeit Schulen diese Korrekturen Nachrichtensystem Klassifikation.

Der Schwerpunkt Posteingang REST-API können Sie außerdem Außerkraftsetzungen erstellen. Jede außer Kraft setzen, dargestellt durch eine Instanz des [InferenceClassificationOverride](../resources/inferenceClassificationOverride.md) ist eine Anweisung für das Klassifizierungssystem Nachrichten von einem bestimmten Absender immer einheitlich (d. h., immer als "Spezifische Darstellung" oder als "Andere" immer), unabhängig davon alle zuvor Gelernte Ansatz festlegt. Können Sie auf [Erstellen](../api/inferenceclassification_post_overrides.md), [Liste](../api/inferenceclassification_list_overrides.md), [Aktualisieren](../api/inferenceclassificationoverride_update.md) und [Löschen](../api/inferenceclassificationoverride_delete.md) für den angegebenen Benutzer außer Kraft gesetzt. Außerkraftsetzungen des Benutzers, werden sofern zutreffend, zugegriffen in einer **InferenceClassification** Navigation-Eigenschaft, die eine Sammlung von **InferenceClassificationOverride** ist. Außerkraftsetzungen können ein Benutzer mehr Kontrolle über die Klassifizierung eingehender Nachrichten und Erstellen von größer Vertrauenswürdigkeit des Systems Klassifikation.

Beachten Sie, dass das Klassifizierungssystem lernen und Klassifizierung nur eingehende Nachrichten im Posteingang betrifft. Nachrichten in anderen Ordnern sind standardmäßig "Spezifische Darstellung". Einrichten einer Überschreibung betrifft zukünftige Nachrichten im Posteingang eingeht. die Überschreibung ändern nicht die Eigenschaft **InferenceClassification** in vorhandenen Nachrichten in einem Ordner Posteingang einschließlich.

## <a name="focused-inbox-api"></a>Posteingang fokussierten API

**Das Klassifizierung Nachrichtensystem Schulung**

[Aktualisieren Sie die Eigenschaft InferenceClassification einer Nachricht](../api/message_update.md)


**Mithilfe von Außerkraftsetzungen konsistent pro Absender klassifizieren**

[Erstellen einer Außerkraftsetzung für eine Absender](../api/inferenceclassification_post_overrides.md) | [Listen Sie alle Benutzer Außerkraftsetzungen](../api/inferenceclassification_list_overrides.md) | 
[Aktualisieren Sie eine Außerkraftsetzung für Absender](../api/inferenceclassificationoverride_update.md) | [eine Absender Überschreibung löschen](../api/inferenceclassificationoverride_delete.md) 
