---
title: "Optimieren der Leistung und Reaktionsfähigkeit"
description: Kunden erwarten leistungsstarke und schnell-Systeme.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: AC976D67-DDFF-4238-8887-7030B14F960B
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1ebc9a47ce8c4f2cc7200d5639f7c323e5dc90bb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="optimizing-performance-and-responsiveness"></a>Optimieren der Leistung und Reaktionsfähigkeit


Kunden erwarten leistungsstarke und schnell Systeme. Dies umfasst einen breiten Bereich von Startzeit bis hin zu Fluid Benutzerinteraktionen mit Applications Szenarien. Analysieren von Leistungsproblemen ist viel Kompetenz und domänenspezifische Kenntnisse erforderlich. Microsoft bietet Tools, damit Sie diese komplexe Aufgabe zu lösen.

Dieses Handbuch enthält eine Einführung an den Prozess zur Ermittlung, analysieren und bewirkt, dass den Stamm Lösen von Leistungsproblemen in wichtige Bereiche. Themen:

-   Mithilfe des **Windows Performance Toolkit (WPT)**

-   Erfassen von Event Trace Log (ETL) Spuren

-   Boot und Anwendungsstart Benutzeroberfläche Verzögerungen

-   CPU und die Datenträgertypen Ressource Verwendungsanalyse

-   Critical Path, und warten Sie Analyse

## <a name="goals"></a>Ziele


In diesem Handbuch erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

-   Erfassen von relevanten Daten zum Analysieren von Leistungsproblemen auf jedem system

-   Grundlegendes zu den Analyseprozess System Ressourcenverbrauch wie CPU und die Datenträgertypen anschauen

-   Identifizieren Sie, was der Reaktionsfähigkeit des Systems in einigen Windows Schlüsselszenarien beeinflussen können.

## <a name="tools"></a>Tools


Das Windows Assessment Toolkit in ADK bietet eine Reihe von leistungsbezogene Tests Bewertung aufgerufen. Die Bewertungsergebnisse dienen zum potenzielle Probleme diagnostizieren, sodass der Hardware und Software, die Sie entwickeln beide schnell sind und sich minimal auf die Akkulaufzeit und Leistung beim Systemstart Zeit zum Herunterfahren haben. Die gleichen Bewertungsfragen stehen OEM/ISV/IHV Partner, Anhänger und andere Mitglieder der Community, herstellen einen gemeinsamen Rahmen um messen, vergleichen und Aspekte der Qualität überprüfen.

Die **Windows Performance Toolkit** besteht aus zwei unabhängigen Tools: **Windows Performance Aufzeichnung (WPR)** und **Windows Performance Analyzer (WPA)**. **WPR** ist eine leistungsstarke Aufzeichnung-Tool, das Event Tracing for Windows (ETW) Aufzeichnungen erstellt. Sie können **WPR** aus der Benutzeroberfläche (UI) oder über die Befehlszeile (CL) ausführen. **WPR** bietet integrierten Profile an, denen Sie verwenden können, um die Ereignisse auszuwählen, die Sie aufzeichnen möchten. **WPA** ist eine leistungsstarke Analysetool, das eine flexible Benutzeroberfläche mit umfangreichen Funktionen Diagrammerstellungsfunktion kombiniert und Datentabellen, die Volltext-Suchfunktionen haben und pivotiert werden können.

## <a name="fast-startup-behavior"></a>Fast Startverhalten


Einführung in Windows 8, ist Fast Start das Standardverhalten beim Starten. Schreiben von Daten auf dem Datenträger so, dass spiegelt wie Works Ruhezustand einschließen wurde des Herunterfahrens aktualisiert. Während des Startvorgangs gewechselt, das System über die Phasen, die in der folgenden Tabelle beschrieben werden.

| Phase                       | Beschreibung                                                                                                                                                  |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **BIOS-Initialisierung**     | Die Zeit des Betriebssystems BIOS, einschließlich der Pre-Boot Execution Environment (PXE) nicht initialisiert werden.                                              |
| **Hiberfile lesen**          | Die Zeit des Betriebssystems der Hiberfile vom Datenträger zu lesen. Die Hiberfile enthält alle des Kontexts System während des Herunterfahrens geschrieben.            |
| **Resume-Geräte**          | Die Zeit des Betriebssystems Geräte fortsetzen und wieder in den Status Aktiv Power zu platzieren.                                                           |
| **WinLogon fortsetzen**         | Die Zeit des Betriebssystems an Winlogon-Prozess fortzusetzen.                                                                                          |
| **Explorer-Initialisierung** | Die Zeit des Betriebssystems Windows-Shell (explorer.exe) nicht initialisiert werden. Diese Phase beendet, wenn die Desktop- oder Startseite für den Benutzer sichtbar ist. |
| **On/Off Dauer buchen**    | Das Zeitfenster dauert alle zum Starten des Tasks nach der Desktop angezeigt wird, jedoch erst CPU und die Datenträgertypen-Ressource im Leerlauf.                                 |

 

Weitere Informationen zu Fast Startverhalten finden Sie unter dem Thema [Ein/aus den Umstieg von Leistung](http://go.microsoft.com/fwlink/p/?linkid=619168) auf MSDN.

## <a name="cpu-scheduling-and-threads"></a>Planen von CPU und Threads


Da die Anzahl der Prozessoren in einem System eingeschränkt ist, können nicht alle Threads gleichzeitig ausgeführt werden. Windows implementiert Prozessor Time-sharing, der einen Thread für einen Zeitraum vor der Prozessor auf einen anderen Thread wechselt ausgeführt wird. Der Vorgang der Wechsel zwischen Threads einen Kontextwechsel aufgerufen und erfolgt über eine Windows-Komponente den Verteiler aufgerufen. Jeder Thread ist in einem bestimmten Ausführungszustand zu einem bestimmten Zeitpunkt vorhanden. Windows verwendet drei Zustände, die auf die Leistung relevant sind: **ausgeführt**, **bereit**und **wartet**.

Ausgeführte Threads befinden sich in den Zustand **ausgeführt** . Threads, die ausführen können, jedoch werden derzeit nicht ausgeführt werden, befinden sich im Zustand **bereit** . Threads, die nicht ausgeführt werden können (weil sie für ein bestimmtes Ereignis warten) befinden sich in dem Zustand **wartet** . Die folgende Abbildung zeigt die möglichen Thread Übergänge.

![Diagramm veranschaulicht die möglichen Thread Übergänge.](images/optimizingperformancelab1.png)

1.  Ein Thread im Zustand **ausgeführt** initiiert einen Übergang in den Zustand **wartet** durch Aufrufen einer Wait-Funktion wie **WaitForSingleObject** oder **Energiesparmodus (&gt; 0)**.

2.  Eine Operation Thread oder Kernel bereitet einen Thread den Status **wartet** (beispielsweise **SetEvent** oder den Timer Ablauf-).

3.  Wenn ein ausgeführten Thread wartet oder das Ende des seinen Anteil der Ausführung erreicht wird ein Thread im Zustand **bereit** für die Verarbeitung vom Verteiler geplant.

4.  Ein Thread im Zustand **ausgeführt** wird gewechselt und in der **aktuelle** Status vom Verteiler eingefügt, wenn es mit einer höheren Priorität Thread belegt ist oder seinen Anteil am Ende.

Der Status wird ein wichtiger Faktor bei der Leistung nur, wenn ein Benutzer auf ein Thread für die Durchführung ein Vorgangs wartet.

Weitere Informationen zum Planen von CPU finden Sie unter dem Thema [CPU Analysis](http://go.microsoft.com/fwlink/p/?linkid=619178) auf MSDN.

## <a name="exercises"></a>Übungen


Dieses Handbuch besteht aus den folgenden Übungen.

-   [Übung 1 – schnellen mit dem Assessment Toolkit Start bewerten](optimizing-performance-and-responsiveness-exercise-1.md)

-   [Übung 2 – schnellen Start von Windows Performance Toolkit bewerten](optimizing-performance-and-responsiveness-exercise-2.md)

-   [Übung 3: Grundlegendes zu Critical Path, und warten Sie Analyse](optimizing-performance-and-responsiveness-exercise-3.md)

 

 






