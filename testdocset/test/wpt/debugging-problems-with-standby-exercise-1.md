---
title: "Übung 1: Ermitteln Sie Probleme mit falsche reaktiviert"
description: "Geräte sollten unerwartet reaktiviert die SoC über Interrupts (beispielsweise Interrupt Stürme, schlecht debouncing usw.)."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: FEC9383F-3643-4CF3-82FA-34FD6C535483
ms.openlocfilehash: 3c8ede2f13b55acd878792349b042d98ed9ff820
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-1---identify-problems-with-spurious-wakes"></a>Übung 1: Ermitteln Sie Probleme mit falsche reaktiviert


Geräte sollten unerwartet reaktiviert die SoC über Interrupts (beispielsweise Interrupt Stürme, schlecht debouncing usw.). Reaktiviert die SoC bewirkt, dass das System **DRIPS**beenden, die durchschnittliche Power Bodenfläche erhöht und verringert die Akkulaufzeit. Dies wird als eine falsche Aktivierung bezeichnet.

Die Analyse Prozess im Zusammenhang mit falsche reaktiviert ist recht unkompliziert.

1.  Laden Sie die Überprüfung vor dem generierten **Sleepstudy-Bericht\_1. html** Bericht [hier](http://download.microsoft.com/download/2/6/6/2662D67D-58CC-4823-8812-AD215DD9778F/sleepstudy-report_1.mdl).

2.  Open **Sleepstudy-Bericht\_1. html** mit Ihrem bevorzugten Browser.

3.  Klicken Sie auf **Sitzung 2**. Das System verbraucht 1.818 w der Energie während 19 Stunden und den **DRIPS %** ist 92 %.

    ![Screenshot zeigt ein Beispiel der verbunden mit dem Standbymodus Sitzung 2](images/standbylab1.png)

4.  Sehen Sie sich die **Oberen hier** -Tabelle. Drahtlosen Gerät wird als active 7 % der Zeit an, während der Sitzung aufgelistet.

    ![Screenshot zeigt ein Beispiel der hier Batterie Verbrauch.](images/standbylab2.png)

5.  Klicken Sie auf die Netzwerke Gerät Zeile um Details zu diesem Täter abzurufen.

    ![Screenshot zeigt, detaillierte Informationen zu Gerät, das höchste Leistung in Anspruch nimmt.](images/standbylab3.png)

Falsche reaktiviert werden durch den Bericht eindeutig identifiziert. Es sind 80 von ihnen in diesem Beispiel wird. Eine weitere Erörterung sollte der Fall sein, unabhängigen Hardwarehersteller um zu bestimmen, warum der drahtlosen Adapter unerwartet oben die SoC aktiviert ist. Das zugrunde liegende Problem könnte eine ungültige Geräte Firmware-Implementierung.

 

 






