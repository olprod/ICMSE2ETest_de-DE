---
title: "Übung 3 - Identifizieren von Problemen mit fehlenden Nebenbedingungen"
description: "Der SoC Power-Status ist die Summe der Status aller Geräte."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7D11B22F-38A4-4764-B2B0-1AA05D779E0C
ms.openlocfilehash: 9a608615a147939c0759b02ddedc69c23414c8d2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-3---identify-problems-with-missing-constraints"></a>Übung 3 - Identifizieren von Problemen mit fehlenden Nebenbedingungen


Der SoC Power-Status ist die Summe der Status aller Geräte.

Windows speichert eine Liste der Geräte und deren Status, die kritischen Energiesparmodus erreichen sind – heißen Einschränkungen. Windows wartet darauf, dass alle Nebenbedingungen erfüllt sein, bevor ansprechender Resiliency und **DRIPS**eingeben. Die Einschränkungen werden vom OEM und des Herstellers SoC durch die Firmware ACPI angegeben.

ACPI Firmware muss geändert werden, wenn OEM den SoC Hersteller Verweis Entwurf ändert und Einschränkungen müssen diese Änderungen genau widerspiegeln.

Fehlende Einschränkungen oder müssen zu viele Integritätsregeln kann eine Vielzahl von Problemen führen, die während des Standbymodus abzuleiten erhöhen.

1.  Laden Sie die Überprüfung vor dem generierten **Sleepstudy-Bericht\_2.Klicken html** Bericht [hier](http://download.microsoft.com/download/3/2/E/32E8B553-47F6-4E2A-9109-C6D678FE0EE8/sleepstudy-report_2.mdl).

2.  Open **Sleepstudy-Bericht\_2.Klicken html** mit Ihrem bevorzugten Browser.

3.  Klicken Sie auf **Sitzung 12**.

    -   Das System verbraucht 1.307 w Energie während 11 Minuten

    -   Die **DRIPS %** beträgt 92 %.

    -   Die Hardware **DRIPS %** ist 19 %.

    ![Screenshot zeigt, des Energieverbrauchs Beispieldaten der Systeme.](images/standbylab7.png)

4.  Betrachten Sie den **Oberen Bereich hier** -Tabelle

    -   Drahtlosen Gerät wird nur 7 % der Zeit an, während der Sitzung als aktiv aufgelistet.

    -   Dieses Problem kann nicht der 19 % ww **DRIPS** Rate berücksichtigt werden.

    ![Screenshot zeigt Beispieltabelle der hier.](images/standbylab8.png)

Große Unterschiede zwischen Software- **DRIPS %** (beispielsweise 92 %) und **DRIPS %** (beispielsweise 19 %) ist in der Regel symptomatisch für eine fehlende Einschränkung in der Firmware ACPI.

Einfach ausgedrückt, nimmt Windows das System ist bereit **DRIPS**eingeben, aber einige Hardwarekomponente noch aktiv ist und verhindert, dass das Paket SoC eingeben S0 Energiesparmodus im Leerlauf.

Der nächste logische Schritt ist zu isolieren und welche Hardware identifizieren Komponente noch D0 und Verarbeiten von Power mithilfe einer Power instrumentierte Plattform oder Ihre Silicon partner-Tools zum Debuggen.

**Hinweis**  
Das fehlenden Einschränkung Problem verfügbar gemacht, durch die Software und Hardware **DRIPS** Abweichung unterscheidet sich von drahtlosen Gerät 7 % Aktivitätsdauer Problem in der Tabelle hier gezeigt. Dieses Problem sollte separat untersucht werden.

 

 

 






