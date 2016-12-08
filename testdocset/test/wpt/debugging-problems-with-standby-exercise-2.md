---
title: "Übung 2: Identifizieren von Problemen mit fehlenden Treiber"
description: "Eine enge Integration zwischen Treiber, Geräte, Windows und die Firmware ist erforderlich, um sicherzustellen, dass ordnungsgemäße Power Management und eine hohe Fehlerrate bei der DRIPS vor-Ort."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D3CF7AED-D3AF-4736-A7B7-E8E3C5839ED1
ms.openlocfilehash: 42579b44730b6d60fc178dafc1d1b100a364d346
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-2---identify-problems-with-missing-drivers"></a>Übung 2: Identifizieren von Problemen mit fehlenden Treiber


Eine enge Integration zwischen Treibern, Geräte, Windows und die Firmware ist erforderlich, um sicherzustellen, dass ordnungsgemäße Power Management und eine hohe Fehlerrate bei der **DRIPS** vor-Ort.

Wenn ein Gerät einen Treiber fehlt oder verfügt nicht über die richtigen Treiber, kann er die zugehörigen Power Gerätemanagement und resultierende D-Status auswirken.

1.  Laden Sie die Überprüfung vor dem generierten **Sleepstudy-Bericht\_2.Klicken html** Bericht [hier](http://download.microsoft.com/download/3/2/E/32E8B553-47F6-4E2A-9109-C6D678FE0EE8/sleepstudy-report_2.mdl).

    Hier.

2.  Open **Sleepstudy-Bericht\_2.Klicken html** mit Ihrem bevorzugten Browser.

3.  Klicken Sie auf **Sitzung 11**. Das System verbraucht 4.585 w Energie während 11 Minuten, und die **DRIPS %** ist 0.

    ![Screenshot zeigt, des Energieverbrauchs Beispieldaten der Systeme.](images/standbylab4.png)

4.  Sehen Sie sich die **Oberen hier** -Tabelle. Ein **Nicht registriertes Gerät** wird als active 100 % der Zeit an, während der Sitzung aufgelistet.

    ![Screenshot zeigt Beispieltabelle der hier.](images/standbylab5.png)

Das nicht registrierte Gerät ist die Grafikkarte (Vorhanden) gemäß den Gerätenamen ** \_SB. PCI0 AUS. GFX0**.

Wenn ein **Nicht registriertes Gerät** in der Liste hier vorhanden ist, bedeutet dies, dass ACPI Firmware hat es definierten, aber Windows nicht auf der Liste der Power-Management-Geräte verfügen.

Dies bedeutet eine der zwei Dinge:

-   Ein Gerät fehlt einen Treiber.

-   Eine ACPI Firmware Einschränkung wurde für ein Gerät nicht im System vorhanden definiert.

In diesem Beispiel wird haben nicht das System einen ordnungsgemäßen Treiber für die **Grafikkarte**installiert, siehe unten im **Geräte-Manager**.

![Screenshot der Geräte-Manager-Dialogfeld.](images/standbylab6.png)

 

 






