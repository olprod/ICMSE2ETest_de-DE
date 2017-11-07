---
author: Justinha
Description: "Reparieren Sie im Startmenü auf einem PC Dual-boot"
ms.assetid: 166c9499-b9b2-48bb-9ff6-d91dc0e497a3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Reparieren Sie klicken Sie im Startmenü auf einem PC Dual-boot"
ms.openlocfilehash: b5425c60f06bb859eee1a01ad4c198cbc34940ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="repair-the-boot-menu-on-a-dual-boot-pc"></a>Reparieren Sie im Startmenü auf einem PC Dual-boot


Beim Einrichten von eines PCs, mehr als ein Betriebssystem zu starten, verlieren Sie möglicherweise gelegentlich die Möglichkeit zum Starten eines der Betriebssysteme. Die Option BCDBoot können Sie schnell Startoptionen für ein Windows-basierten Betriebssystem hinzufügen.

## <a name="span-idrepairingawindowspartitiononadual-bootpcspanspan-idrepairingawindowspartitiononadual-bootpcspanspan-idrepairingawindowspartitiononadual-bootpcspanrepairing-a-windows-partition-on-a-dual-boot-pc"></a><span id="Repairing_a_Windows_partition_on_a_dual-boot_PC"></span><span id="repairing_a_windows_partition_on_a_dual-boot_pc"></span><span id="REPAIRING_A_WINDOWS_PARTITION_ON_A_DUAL-BOOT_PC"></span>Reparieren eine Windows-Partition auf einem PC Dual-boot


1.  Installieren einer separaten Festplatte oder zur Vorbereitung einer separaten Partition für jedes Betriebssystem.

2.  Installieren Sie die Betriebssysteme. Wenn Ihr PC Windows 8.1 besitzt, installieren Sie Windows 10 beispielsweise auf der anderen Festplatte oder Partition.

3.  Starten Sie den PC neu. Die Menüs Boot sollte mit beiden genannten Betriebssysteme angezeigt werden.

    Wenn beide Betriebssysteme nicht aufgelistet werden:

    1.  Öffnen Sie eine Befehlszeile, entweder als Administrator aus innerhalb Windows, oder durch eine Befehlszeile, die mit dem Windows-Installationsdatenträger und Presssing UMSCHALT + F10 starten oder durch Starten von Windows PE ([Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)).

    2.  Hinzufügen von Startoptionen für ein Windows-Betriebssystem.

        ``` syntax
        Bcdboot D:\Windows
        ```

    3.  Starten Sie den PC neu. Nun wird das Startmenü beide Menüoptionen im angezeigt.

## <a name="span-idrepairanotheroperatingsystempartitionspanspan-idrepairanotheroperatingsystempartitionspanspan-idrepairanotheroperatingsystempartitionspanrepair-another-operating-system-partition"></a><span id="Repair_another_operating_system_partition"></span><span id="repair_another_operating_system_partition"></span><span id="REPAIR_ANOTHER_OPERATING_SYSTEM_PARTITION"></span>Reparieren von einem anderen Betriebssystempartition


Sie können manuell hinzufügen BCDEdit von Partitionen erstellen oder Sie können einem Drittanbieter-Tool wie [EasyBCD](http://go.microsoft.com/fwlink/?LinkId=330254) zum Einrichten der Boot-Partitionen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[BCDboot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

 

 






