---
title: Problembehandlung bei der Bewertung
description: Problembehandlung bei der Bewertung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c0ab73ed-ba51-45f7-b498-916f2492154f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: b4a85e0463bd1a0f8b2985ef9cc231824c0672a0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="troubleshooting-assessments"></a>Problembehandlung bei der Bewertung


Die folgende Informationen helfen Ihnen die Gründe und Ursachen Bewertungen zu einem Fehler beim diagnostizieren.

## <a name="assessment-didnt-produce-any-results"></a>Bewertung führen keine Ergebnissen.


Wenn Sie eine Fehlermeldung erhalten und die Bewertung keine Ergebnisse, verwenden Sie diese Methode zum Anzeigen der Protokolldateien:

-   Wählen Sie in der Windows-Assessment-Konsole auf der Seite **Ergebnisse anzeigen** die **Gesamtanzahl der Fehler**, und erweitern Sie dann den Fehler, der im Detailbereich auf der rechten Seite angezeigt wird.

-   Wählen Sie den Link unter **Weitere Analyse** zum Öffnen des Ordners, in dem die Protokolldateien gespeichert werden. Der Ordner enthält AxeLog.etl Trace-Dateien, die Sie in Windows Performance Analyzer (WPA) öffnen können. Der Ordner enthält auch ErrorWarnings.xml und AXELog.txt-Dateien. Die Textdatei ist eine Zusammenstellung von aller Event Trace Log (ETL)-Dateien, die erstellt werden, nachdem der Auftrag abgeschlossen ist.

## <a name="the-assessment-fails-to-complete"></a>Die Bewertung nicht abgeschlossen


Der Auftrag abgeschlossen ist, jedoch das Assessment wird nicht ausgeführt. Eine der folgenden Fehlercodes möglicherweise durch die Bewertung gemeldet:

-   0x80050006

-   0 x 80004005

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    **Rundll32.exe advapi32.dll,ProcessIdleTasks**

2.  Deaktivieren Sie Wartungsaufgaben reguläre und im Leerlauf und beenden Sie alle Wartungsaufgaben vor dem Ausführen der Bewertung

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

 

 







