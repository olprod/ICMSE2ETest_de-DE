---
title: "Übung 1: das Gerät Audio-Wartezeit Leistung für Communications Szenarien bewerten"
description: "In dieser Übung werden wir die folgende Matrix audio Wartezeit Tests ausführen, die Latenz Statistik für verschiedene Wartezeit Modi unterstützt im Windows generieren."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2264F1B3-27BC-4140-9A90-0532604298BC
ms.openlocfilehash: d76311bb2fa0873883764bb6e23e357709c14f9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-1---assess-the-devices-audio-latency-performance-for-communications-scenarios"></a>Übung 1: das Gerät Audio Wartezeit Leistung für Communications Szenarien bewerten


In dieser Übung werden wir die folgende Matrix audio Wartezeit Tests ausführen, die Latenz Statistik für verschiedene Wartezeit Modi in Windows unterstützt generieren. Die Modi, die der Test kann, in ausgeführt werden umfassen:

-   Standardmodus – generiert Standard Out-of-Box-audio Wartezeit.

-   Roh-Modus – entfernt Audio Verarbeitung von Objekten (möglich).

-   Niedriger Zeitraum – neue geringer Latenzmodus für nahezu in Echtzeit Szenarien wie etwa Skype.

Der Test rendert Test Sounds, die durch das Mikrofon erfasst werden.

**Hinweis**  Diese schrittweise Anleitung ist auch als eine Übungseinheit auf Channel 9, video anzeigen die Videos für Entwickler von Microsoft Products and Services erstellen Personen features verfügbar: <https://channel9.msdn.com/Events/WinHEC/2015/OWDHOL301>

 

## <a name="step-1-prepare-the-system-to-run-the-tests"></a>Schritt 1: Vorbereiten des Systems zum Ausführen der tests


1.  Installieren des Controllers Hardware Lab Kit (HLK).

2.  Mit der rechten Maustaste auf **das Startmenü** , und klicken Sie auf **der Befehlszeile (Admin)**.

3.  Navigieren Sie zu der ** \\ \\ &lt;-Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessorarchitektur&gt;\\TE** Ordner.

4.  Kopieren Sie die folgenden Tests und Tools aus der Controller Hardware Lab Kit (HLK) auf dem Testcomputer in: C:\\Leistung\\Medien
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\Nttest\\Multimediatest\\Wmmftest\\glitchfreetaeftests.dll
    -   \\\\&lt;Name des Domänencontrollers&gt;\\TaefBinaries\\&lt;Prozessor-Architektur&gt;\\\*
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\Leistung\\WindowsXRay\\Tools\\EtwPattern.dll
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\testen\\MediaEngineTest.exe
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\audiotestdienst\\Bin\\audiospew.exe
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\audiotestdienst\\Bin\\audiostreaming.dll
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\Nttest\\Multimediatest\\Wmmftest\\rws.exe
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\Nttest\\Multimediatest\\Wmmftest\\Audio-Fidelity-stress.xml
    -   \\\\&lt;Name des Domänencontrollers&gt;\\Tests\\&lt;Prozessor-Architektur&gt;\\audiotestdienst\\Bin\\LatencyTest.dll

5.  Legen Sie die Lautstärke der Lautsprecher auf 100 %.

## <a name="step-2-run-the-test-in-default-mode"></a>Schritt 2: Führen Sie den Test im Standardmodus


1.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::Vanilla
    ```

2.  Anzeigen der **durchschnittlichen**, **Max**und **Min** Verzögerungswerte, die an das Eingabeaufforderungsfenster gesendet werden.

## <a name="step-3-run-the-test-in-raw-mode"></a>Schritt 3: Führen Sie den Test im Roh-Modus


1.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::Raw
    ```

2.  Anzeigen der **durchschnittlichen**, **Max**und **Min** Verzögerungswerte, die an das Eingabeaufforderungsfenster gesendet werden.

## <a name="step-4-run-the-test-in-low-latency-mode"></a>Schritt 4: Führen Sie den Test im Modus mit geringer Latenz


1.  Führen Sie den folgenden Befehl ein:

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::LowPeriod
    ```

2.  Anzeigen der **durchschnittlichen**, **Max**und **Min** Verzögerungswerte, die an das Eingabeaufforderungsfenster gesendet werden.

 

 






