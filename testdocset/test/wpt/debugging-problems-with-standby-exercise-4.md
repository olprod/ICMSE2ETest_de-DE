---
title: "Übung 4: Identifizieren von Problemen mit USB-Geräten"
description: "Der USB-Host-Controller Herunterfahren können haben nur erst, nachdem alle von der verbundenen Geräte Energiesparmodus eingegeben."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: AE0C4C51-7DD6-4A18-AEC4-DD01CB24A7A4
ms.openlocfilehash: 0fbbcd1837f5f38cf5780bd53a4c95022f725872
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-4---identify-problems-with-usb-devices"></a>Übung 4: Identifizieren von Problemen mit USB-Geräten


Der USB-Host-Controller Herunterfahren können haben nur erst, nachdem alle von der verbundenen Geräte Energiesparmodus eingegeben. Dies bedeutet, dass USB-Geräte selektive unterstützen müssen angehalten werden soll auf modernen Standby-Geräten, um sicherzustellen, dass die SoC **DRIPS** eingeben kann, während der Bildschirm deaktiviert ist.

## <a name="part-1-use-a-sleepstudy-report-to-identify-problems"></a>Teil 1: Verwenden eines Berichts SleepStudy zur Identifizierung von Problemen


1.  Laden Sie die Überprüfung vor dem generierten **Sleepstudy-Bericht\_2.Klicken html** Bericht [hier](http://download.microsoft.com/download/3/2/E/32E8B553-47F6-4E2A-9109-C6D678FE0EE8/sleepstudy-report_2.mdl).

2.  Open **Sleepstudy-Bericht\_2.Klicken html** mit Ihrem bevorzugten Browser.

    -   Beachten Sie, dass das System nicht weniger als 120 nutzen kann mW Standby (z. B. finden Sie in dem Standbymodus Sitzung 6).

    ![Screenshot zeigt, des Energieverbrauchs Beispieldaten der Systeme.](images/standbylab9.png)

3.  Klicken Sie auf **Sitzung 10**. Das System verbraucht 2,83 w der Energie während 11 Minuten und der **DRIPS %** ist 0.

    ![Screenshot zeigt, des Energieverbrauchs Beispieldaten der Systeme.](images/standbylab10.png)

4.  Sehen Sie sich die **Oberen hier** -Tabelle.

    1.  Der USB-Hostcontroller (**\_SB. PCI0 AUS. XHC**) bei 99 % der Sitzungsdauer aktiv ist.

    2.  XHC ist die 3.0 USB-Hostcontroller.

![Screenshot zeigt Beispieltabelle der hier.](images/standbylab11.png)

Wenn der USB-Bus-Controller für Minuten gleichzeitig in modernen Standby aktiv ist, in der Regel bedeutet dies, ein USB-Gerät angeschlossen ist mit dem Bus ist nicht selektive Eingabe anhalten, möglicherweise angehalten, da er selektive nicht unterstützt werden soll. Der nächste logische Schritt ist zu bestimmen, welches USB-Gerät ist in D0 verfolgen einer ETL-Trace bleiben.

Weitere Informationen zu selektive aussetzen, finden Sie im Thema [USB-selektive aussetzen](https://msdn.microsoft.com/library/windows/hardware/ff540144) auf MSDN.

## <a name="part-2-use-an-etl-trace-to-identify-problems"></a>Teil 2: Verwenden einer ETL-Trace zur Identifizierung von Problemen


Um die Untersuchung USB weiter, wurde ein ETL-Trace auf demselben System erfasst, bei denen die **SleepStudy** generiert wurde.

Wenn USB-Problemen untersuchen möchten, verwenden Sie das **DState** Diagramm und Tabelle.

1.  Laden Sie den Überprüfung vor dem generierten **USBProblem.etl** Trace [hier](http://download.microsoft.com/download/5/1/C/51CB1607-D3A8-455B-828A-244A56B06791/USBProblem.etl).

2.  **USBProblem.etl** mit **WPA**zu öffnen.

3.  Drag & drop im Diagramm **DRIPS** in der Registerkarte **Analyse** .

4.  Sehen Sie sich die **Gründe nicht Drips**und suchen Sie den USB-Hostcontroller xHCI als ein Gerät verhindert, dass das System in **DRIPS**.

    -   Sie können sehen, dass das Gerät bei 98 % der Trace (siehe in der Spalte **% Grund Zeit** ) aktiv ist.

        ![Screenshot der Verwendung von WPA Beispieldaten.](images/standbylab12.png)

5.  Vergrößern Sie die Region, in dem der USB-Hostcontroller xHCI aktiv ist.

    1.  Wählen Sie das Gerät in der Tabelle.

    2.  Mit der rechten Maustaste auf das blaue oberflächliche Intervall im Diagramm, und wählen Sie Zoom.

    3.  Die **Zeit (%) Grund** sollte jetzt 100 % sein.

    ![Screenshot der Verwendung von WPA Beispieldaten.](images/standbylab13.png)

6.  Hier finden Sie das **Gerät Dstate** Diagramm in der Kategorie **Power** des **Diagramm-Explorer**.

    ![Screenshot der Verwendung von WPA Beispieldaten.](images/standbylab14.png)

7.  Drag & drop das **Gerät Dstate** Diagramm in der Registerkarte **Analyse** .

    -   Das **Gerät DState** Diagramm zeigt die effektiven D-Zustände Geräte über einen Zeitraum an. Die Daten können Sie ermitteln, ob ein bestimmtes Gerät den entsprechenden D-Zustand wechselt, während das System in modernen Standby ist.

        -   **PoFx Typ**: verwendet für Geräte, die von der Windows Power Management Framework verwaltet werden.

        -   **Nicht PoFx Typ**: für USB-Geräte verwendet.

8.  Verschiebt die **DState** Spalte rechts neben der Spalte **Typ** . Die Ansicht sollte wie folgt aussehen:

    ![Screenshot zeigt Beispiel DState Daten.](images/standbylab15.png)

9.  Erweitern Sie die Kategorie **Nicht PoFX** aus.

10. Erweitern Sie die **Dstate** Zeile mit dem Wert 0 x 0 (D0 Zustand oder aktiv).

11. Sortieren nach der Spalte **Name** , und suchen Sie die USB-Geräte.

    ![Screenshot zeigt Beispiel DState Daten basierend auf USB-Geräte.](images/standbylab16.png)

Die Daten in der Tabelle D-Zustand zeigt, dass während das System im Standbymodus befindet, ein zusammengesetztes USB-Gerät weiterhin im Zustand D0 für 100 % der Zeit war. Die Hardware-Id des Geräts, zusammengesetzte ist USB\\VID\_0BB4 & PID\_0BA1\\00000015B42EE80F0000000000000000. Dies ist das Gerät, das den Controller XHCI Herunterfahren verhindert hat.

Wenn das Gerät durch einen Treiber verfasst von Microsoft verwaltet wird, melden Sie das Problem an Microsoft. Wenn dies nicht der Fall ist, klicken Sie dann diese Informationen an den Besitzer der Treiber finden Sie eine Lösung, und stellen Sie sicher, dass das Gerät selektive eingibt anhalten Hardwarehersteller gemeldet werden muss.

 

 






