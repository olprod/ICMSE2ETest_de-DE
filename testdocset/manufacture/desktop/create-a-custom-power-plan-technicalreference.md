---
author: Justinha
Description: Erstellen eines benutzerdefinierten Power-Plans
ms.assetid: d1d0e1b0-f15f-482c-9e9b-1b75a05dfeb3
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen eines benutzerdefinierten Power-Plans
ms.openlocfilehash: 51b1b866add958982b8f0cd5b67f5ae16f3d972a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-power-plan"></a>Erstellen eines benutzerdefinierten Power-Plans


Ein *Power Plan* ist eine Auflistung von Hardware- und Systemeinstellungen, die verwaltet werden, wie die Computer verwenden und Strom sparen. Ein Plan Power ist auch bekannt als ein *Energieschema*. Sie können benutzerdefinierte Power Pläne erstellen, die für bestimmte Computer optimiert sind.

Standardmäßig Windows 8 und Windows Server® 2012 drei Power-Plänen enthalten: **ausgeglichen**, **Energiesparmodus**und **Hohe Leistung**. Sie können diese vorhandenen Pläne für Ihre Systeme anpassen, neue Pläne, bei die basieren auf die vorhandenen Pläne, oder erstellen einen neuen Power Plan von Grund auf neu erstellen.

Optimieren von Windows Power-Pläne können Sie Akkulaufzeit verbessern. Single-Wert mit geringer Leistung Anwendung, Gerät oder ein System-Feature kann jedoch Akkulaufzeit erheblich verkürzen. Informationen zu den Faktoren, die Akkulaufzeit beeinflussen, finden Sie unter [Verwalten von Akkulaufzeit und Power Auslastung (Übersicht)](managing-battery-life-and-power-consumption-overview-technicalreference.md).

## <a name="span-idinthistopicspanspan-idinthistopicspanspan-idinthistopicspanin-this-topic"></a><span id="In_this_topic"></span><span id="in_this_topic"></span><span id="IN_THIS_TOPIC"></span>In diesem Thema


[Erstellen eines Plans für benutzerdefinierte Stromversorgung](#createcustomizedplan)

[Auflisten von den verfügbaren Power-Plänen](#listpowerplans)

[Bereitstellen eines Power-Plans](#deploypowerplan)

## <span id="CreateCustomizedPlan"></span><span id="createcustomizedplan"></span><span id="CREATECUSTOMIZEDPLAN"></span>


**Erstellen eines Plans für angepasste power**

1.  Klicken Sie auf **Start**, und wählen Sie dann auf **Systemsteuerung**.

2.  Klicken Sie auf **Hardware und Sound**, und wählen Sie dann auf **Energieoptionen**.

3.  Systemsteuerungsoption **Energieoptionen** wird geöffnet, und die Power-Pläne angezeigt werden.

4.  Klicken Sie auf **Erstellen Sie einen Plan für die Leistung**.

5.  Führen Sie die auf dem Bildschirm planen Anweisungen zum Erstellen und Anpassen einer Power-Datei, die auf einen vorhandenen Plan basiert. Nennen Sie Ihren Plan Power "OutdoorPlan".

    **Hinweis**  
    Am häufigsten verwendete Power Planen von Einstellungen über die Systemsteuerung können verwaltet werden. Um die Einstellungen optimieren, die nicht in der Systemsteuerung angezeigt werden, finden Sie unter [Optimieren einer benutzerdefinierten Power planen](fine-tune-a-custom-power-plan-technicalreference.md).

## <span id="ListPowerPlans"></span><span id="listpowerplans"></span><span id="LISTPOWERPLANS"></span>


**Auflisten von den verfügbaren Power-Plänen**

-   Auf dem Referenzcomputer an einer Eingabeaufforderung mit erhöhten Rechten Folgendes ein:

    ``` syntax
    powercfg -LIST
    ```

    Der Computer wird die Liste der verfügbaren Power Pläne zurück. Im folgenden Beispiel sind diese Pläne *ausgeglichen*, *Energiesparmodus*und *OutdoorPlan*.

    ``` syntax
    Existing Power Schemes (* Active)
    -----------------------------------
    Power Scheme GUID: {guidPlan1}  (Balanced) *
    Power Scheme GUID: {guidPlan2}  (Power saver)
    Power Scheme GUID: {guidPlan3}  (OutdoorPlan)
    ```

    Beachten Sie die GUIDs, die neben den Power-Plänen aufgeführt sind, die Sie erfassen möchten.

## <span id="DeployPowerPlan"></span><span id="deploypowerplan"></span><span id="DEPLOYPOWERPLAN"></span>


**Bereitstellen eines Power-Plans**

Nachdem Sie für Ihr System arbeiten Power-Pläne erstellt haben, können Sie die Power-Pläne auf den Zielcomputern bereitstellen.

Um den OutdoorPlan Power Plan exportieren, den Sie auf dem Referenzcomputer erstellt haben, öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten, und geben Sie die folgenden

``` syntax
powercfg -EXPORT C:\OutdoorPlan.pow {guidPlan-New}
```

Dadurch wird eine neue Power Plandatei erstellt.

Weitere Informationen finden Sie unter [festgelegt das Standard Power planen](set-the-default-power-plan-technicalreference.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Verwalten von Akkulaufzeit und Power-Auslastung (Übersicht)](managing-battery-life-and-power-consumption-overview-technicalreference.md)

[Test Akkulaufzeit und des Energieverbrauchs](test-battery-life-and-power-consumption-technicalreference.md)

[Festlegen des Standard-Power-Plans](set-the-default-power-plan-technicalreference.md)