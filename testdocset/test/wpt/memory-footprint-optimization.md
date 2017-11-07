---
title: Optimierung des Speichers Bilanz
description: "Die Menge des Arbeitsspeichers verfügbar auf einem System wirkt sich erheblich auf die Benutzeroberfläche aus."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8ECD1B28-D98A-406D-8920-BC205D3A1729
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e7e8ca172a9a24b2e9eb91f5aa287e8f18592c28
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="memory-footprint-optimization"></a>Optimierung des Speichers Bilanz


Die Menge des Arbeitsspeichers verfügbar auf einem System wirkt sich erheblich auf die Benutzeroberfläche aus. Die Auswirkung wirkt sich auf Bereiche, die von der allgemeinen Reaktionsfähigkeit des Systems bis hin zu Akkulaufzeit. Verfügbare Arbeitsspeicher ist ein wichtiger Faktor, berücksichtigen Sie beim Auswerten der umfassende Erfahrung auf einem Gerät Speichermangel, in dem umfassend Windows auf paging und Austauschen von Inhalten aus dem Speicher.

Dieses Handbuch führt Sie schrittweise durch die Leistungsprobleme im Zusammenhang mit dem Speicher analysieren und die Ursache zu identifizieren, ob es sich um einen Treiber oder ein Benutzer Modus Vorgang ist mit dem **Windows Performance Toolkit**. Themen:

-   Treiber und Anwendung Bilanz

-   Arbeitszeiten und wohnen

-   Pool Arbeitsspeicher Zuweisungen

-   Heap und VirtualAlloc Arbeitsspeicher Zuweisungen

## <a name="goals"></a>Ziele


In diesem Handbuch erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

-   Verwenden Sie **Windows Performance Aufzeichnung (WPR)** , um Spuren von Speicherprobleme sammeln.

-   Verwenden Sie die Bewertung Assessment and Deployment Kit (ADK) Speicherbedarf, um eine Basislinie für den Arbeitsspeicher Nutzung zu sammeln.

-   Analysieren der Speicherverwendung ausgelagert/nicht ausgelagerte Pool von Treibern.

-   Arbeitsseiten und Wohnsitz Sets-Prozessen zu analysieren.

-   Verstehen Sie, wann und wie Arbeitsspeicher dynamisch von betriebswirtschaftlichen Faktoren und Prozesse zugeordnet wird.

## <a name="tools"></a>Tools


In der Vergangenheit mussten Kernel-Debugger sowie eine große Anzahl von unverständliche Befehle zum Ermitteln, welche Seiten Daten- und derzeit physischen Arbeitsspeicher belegen verwendet werden. Nun können Sie das **Windows Performance Toolkit (WPT)** zum Erfassen und diese Informationen verständlich und aktionsgebunden über integrierte Windows-Verwaltungsinstrumentation auf anzeigen.

**WPT** besteht aus den **Windows Performance Analyzer (WPA)** und die **Windows Performance Aufzeichnung (WPR)**.

Das Windows Assessment Toolkit in der ADK kann auch eine Arbeitsspeicher Bilanz Bewertung erhalten verwendet werden. Diese Bewertung erstellt eine Momentaufnahme der Speicherverwendung während der eine Reihe von Neustarts des Systems und unmittelbar nach der Desktop sichtbar ist. Es wird nicht Speicherverwendung während der normalen Computer Vorgänge ausgewertet.

Die ADK **Windows Assessment Konsole (WAC)** ist das Tool zum Ausführen von Analysen und Berichte visuelle Leistung verwendet.

## <a name="terminology"></a>Terminologie


| Begriff                            | Definition                                                                                                                                                                                                                             |
|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Freigebbare Seiten**              | Seiten, die einem oder mehreren Prozessen verwenden können. Beispiele: Codepages in ausführbaren Abbildern (DLL, .exe und .cpl) oder Datenseiten-Datei (txt, DOC, usw.).                                                                           |
| **Private Seiten**               | Seiten, die ausschließlich von einem einzelnen verwendet verarbeiten und die am häufigsten dynamisch zugeordnete Daten wie Heap oder VirtualAlloc enthalten.                                                                                                          |
| **Arbeitsseiten Prozess**         | Menge von Seiten auf die verwiesen wird durch einen anderen Prozess kürzlich und private und freigegebene Seiten enthält.                                                                                                                                              |
| **Prozess privater Arbeitssatz** | Gruppe von privaten-freigebbare Seiten vor kurzem von einem Prozess verwiesen.                                                                                                                                                                    |
| **Verfügbar**                   | Größe des Arbeitsspeichers für die Verwendung von Prozessen sofort verfügbar im System. Diese Metrik besteht Seiten in der Liste Standby, denen nicht dauerhaft geschrieben werden, bevor durch andere Prozesse Postfachtyp umgewandelt werden kann. |

 

## <a name="exercises"></a>Übungen


Dieses Handbuch besteht aus den folgenden Übungen.

-   [Übung 1: Identifizieren von Geschäftsprozessen mit großen Working Sets](memory-footprint-optimization-exercise-1.md)

-   [Übung 2: Nachverfolgen Benutzer Modus Prozess Zuweisungen](memory-footprint-optimization-exercise-2.md)

-   [Übung 3: Nachverfolgen Treiber Speicherbedarf und dynamische Zuweisungen während des Startvorgangs](memory-footprint-optimization-exercise-3.md)

 

 






