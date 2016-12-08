---
author: Justinha
Description: Festlegen des Standard-Power-Plans
ms.assetid: e6c722ae-29f4-4249-adbe-9121fdadcf4c
MSHAttr: PreferredLib:/library/windows/hardware
title: Festlegen des Standard-Power-Plans
ms.openlocfilehash: bdd2a842782dba60ef64bcbc2eb17f4d20c872bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="set-the-default-power-plan"></a>Festlegen des Standard-Power-Plans


Verwenden Sie diese Anweisungen, um einen Standardwert Power Plan festzulegen, bei der Bereitstellung von Windows 8 oder Windows Server® 2012-PCs. Ein Plan Power ist auch bekannt als ein *Energieschema*.

**Hinweis**  
Diese Seite enthält Informationen über PCs manufacturing.

Um eine Power Pläne auf Ihrem eigenen Computer zu ändern, finden Sie unter [Power Pläne: häufig gestellte Fragen](http://go.microsoft.com/fwlink/p/?linkid=278892).

 

**Festlegen des Standard-Power-Plans**

1.  Öffnen Sie auf dem Referenzcomputer eine Eingabeaufforderung mit erhöhten Rechten aus.

2.  Wenn Sie einen Plan Power von einem anderen Computer verwenden möchten, importieren Sie den Power Plan.

    Geben Sie zum Importieren eines Power-Plans mit dem Namen OutdoorPlan beispielsweise Folgendes an der Befehlszeile:

    ``` syntax
    powercfg -IMPORT C:\OutdoorPlan.pow
    ```

3.  Geben Sie Folgendes ein, um die GUID für die Power-Pläne auf dem Computer zu suchen:

    ``` syntax
    powercfg -LIST
    ```

    Der Computer gibt die Liste der verfügbaren Power Pläne zurück. In den folgenden Beispielen finden Sie in diese Pläne als *guidPlan1* und *guidPlan2*.

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    ```

4.  Beachten Sie die GUIDs vor, die neben den Power-Plänen aufgeführt, die Sie ändern möchten.

5.  Legen Sie den Power-Plan, den Sie als Standard wie der aktiven Power Plan festlegen möchten. Beispielsweise können Sie den folgenden Befehl verwenden:

    ``` syntax
    powercfg -SETACTIVE {guidPlan2}
    ```

    wobei *guidPlan2* der Name des Plans Power ist.

    Dieser Befehl kann mithilfe eines benutzerdefinierten Befehls in einer Antwortdatei oder durch Öffnen einer Eingabeaufforderung mit erhöhten Rechten im Überwachungsmodus ausgeführt werden.

**Bestätigen, dass der Standard-Power planen**

1.  Klicken Sie auf **Start**, und wählen Sie dann auf **Systemsteuerung**.

2.  Klicken Sie auf **Hardware und Sound**, und wählen Sie dann auf **Energieoptionen**.

    Systemsteuerungsoption **Energieoptionen** wird geöffnet, und die Power-Pläne angezeigt werden.

3.  Lesen Sie jede Power Plan.

4.  Stellen Sie sicher, dass der richtige Plan wie der aktiven Power Plan festgelegt ist. Der Computer Zeigt ein Sternchen (\*) neben dem aktiven Power Plan.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen eines benutzerdefinierten Befehls zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915058)

[Windows im Überwachungsmodus oder OOBE Boot](boot-windows-to-audit-mode-or-oobe.md)

[Erstellen eines benutzerdefinierten Power-Plans](create-a-custom-power-plan-technicalreference.md)

[Power-Richtlinienkonfiguration und Bereitstellung in Windows](http://go.microsoft.com/fwlink/p/?linkid=129584)

 

 






