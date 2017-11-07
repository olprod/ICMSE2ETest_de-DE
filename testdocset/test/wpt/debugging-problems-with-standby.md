---
title: Debuggen von Power Problemen mit dem Standbymodus
description: "Nachdem Sie Ihre modernen Standby-System unter Verwendung der richtigen Power Management Anleitung entwickelt haben, müssen Sie zum Testen und überprüfen Sie, ob die Bodenfläche Power bieten umfangreiche Akkulaufzeit im Standbymodus optimiert ist."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5A43DECA-DF16-4CE2-BE21-4077D362C8D7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: dec20d9d8766cf88392796b7234c4eac9d17a6b8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="debugging-power-problems-with-standby"></a>Debuggen von Power Problemen mit dem Standbymodus


Nachdem Sie Ihre modernen Standby-System unter Verwendung der richtigen Power Management Anleitung entwickelt haben, müssen Sie testen und überprüfen, dass die Bodenfläche Power optimiert wird, um großartige Akkulaufzeit im Standbymodus zu übermitteln. Sie müssen möglicherweise das System eine Power Täter isolieren zerlegen.

Diese Übungseinheit enthält nützliche Tools wie **SleepStudy** und **WPA**eingehender und führt Sie durch verschiedene Fallstudien, die häufig auftretender Probleme zu veranschaulichen. Themen:

-   Auswirkung der USB-Geräte

-   Firmware Probleme und fehlenden Integritätsregeln

-   Treiberprobleme

-   Identifizieren von Aktivierungsquellen falsche

## <a name="goals"></a>Ziele


In diesem Handbuch erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

-   Interpretieren der Daten aus **SleepStudy** Berichte und **WPA DRIPS** -Plug-Ins

-   Identifizieren Sie häufig auftretende Probleme, die die Bodenfläche Power beeinflussen können.

## <a name="terminology"></a>Terminologie


-   **Unterste Runtime im Leerlauf Plattform Zustand (DRIPS)**: das System gesagt, dass er in **DRIPS** werden, wenn das System den niedrigsten Betrag Leistung möglich, durch das System Power Floor begrenzt belegt. Bei der Bildschirm deaktiviert ist, die moderne Standby-Sitzung beginnt, und das System über mehrere Phasen zum Verschieben in einen Energiesparmodus geht. Wenn das System in den niedrigsten Power Zustand befindet, wird das System in **DRIPS**ist. Das System ist nicht in **DRIPS** Wenn Aufgaben wie das Empfangen von e-Mails, Leistung aktualisieren live Kacheln mit neuen Inhalt an, annehmen von Anrufen VoIP oder eine beliebige andere Hintergrund-Vorgang, der Systemressourcen ist. Die mehr Zeit, die das System im **DRIPS** verbringt, bevor der Bildschirm ist aktiviert zurück, je mehr die Akkulaufzeit.

    ``` syntax
    Total standby session time = DRIPS time + non-DRIPS time
    ```

-   **Für eine Aktivierung**: Softwarekomponenten, die zum ausführen dürfen arbeiten im Hintergrund im modernen Standby-Modus.

## <a name="tools"></a>Tools


Das **Windows Performance Toolkit** besteht aus zwei unabhängigen Tools: **Windows Performance Aufzeichnung (WPR)** und **Windows Performance Analyzer (WPA)**. **WPR** ist eine leistungsstarke Aufzeichnung-Tool, mit dem Event Tracing for Windows (ETW) Aufzeichnungen erstellt. Sie können **WPR** von der Benutzeroberfläche (UI) oder über die Befehlszeile (CL) ausführen. **WPR** bietet integrierten Profile an, denen Sie verwenden können, um die Ereignisse auswählen, die Sie aufzeichnen möchten. **WPA** ist eine leistungsstarke Analysetool, das eine flexible Benutzeroberfläche mit umfangreichen Funktionen Diagrammerstellungsfunktion kombiniert und Datentabellen, die Volltext-Suchfunktionen haben und pivotiert werden können.

**SleepStudy** ist ein Windows-Diagnosetool, das moderne Standby (verbunden oder getrennt) unterstützt. Es überwacht modernen Standby PC Verhalten und modernen Standby Akkulaufzeit bearbeitungsfähige Diagnose enthält. Es ist nur auf modernen Standby-fähige PCs verfügbar. **SleepStudy** generiert eine Zusammenfassung der häufigsten Probleme, die schlechter modernen Standby Akkulaufzeit verursachen.

Um einen Bericht **SleepStudy** zu erhalten, geben Sie folgenden Befehl in einem Eingabeaufforderungsfenster Administrator:

``` syntax
powercfg.exe /SleepStudy
```

Eine HTML-Datei mit dem Namen Sleepstudy-report.html in das aktuelle Verzeichnis erstellt das Dienstprogramm integrierten **powercfg.exe** .

**Hinweis**  
Alle Übungen in diesem Handbuch vorab generiert **SleepStudy** Berichte, damit Sie keine **SleepStudy** Berichte, die Sie für dieses Handbuch generieren müssen.

 

## <a name="exercises"></a>Übungen


Dieses Handbuch besteht aus den folgenden Übungen.

-   [Übung 1: Ermitteln Sie Probleme mit falsche reaktiviert](debugging-problems-with-standby-exercise-1.md)

-   [Übung 2: Identifizieren von Problemen mit fehlenden Treiber](debugging-problems-with-standby-exercise-2.md)

-   [Übung 3 - Identifizieren von Problemen mit fehlenden Nebenbedingungen](debugging-problems-with-standby-exercise-3.md)

-   [Übung 4: Identifizieren von Problemen mit USB-Geräten](debugging-problems-with-standby-exercise-4.md)

 

 






