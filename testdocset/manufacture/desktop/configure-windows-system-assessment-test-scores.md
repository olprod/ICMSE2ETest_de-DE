---
author: Justinha
Description: Konfigurieren von Windows System Assessment Testergebnisse
ms.assetid: b2906f26-8887-44fe-8894-f73caee41824
MSHAttr: PreferredLib:/library/windows/hardware
title: Konfigurieren von Windows System Assessment Testergebnisse
ms.openlocfilehash: 0ec14fee71d0b4325dacc49371c1e85e068bc802
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-windows-system-assessment-test-scores"></a>Konfigurieren von Windows System Assessment Testergebnisse


Das Windows® System Assessment Tests (WinSAT) dienen zum Analysieren der Leistung verschiedener Systemkomponenten einschließlich CPU, Arbeitsspeicher, Festplatten und Grafiken.

Die WinSAT-Ergebnisse werden als Windows Erfahrung Index (WEI) Bewertungen im Element Systemsteuerung **Leistungsinformationen und Tools** zusammengefasst. Diese Faktoren anzeigen Consumer die Leistungsmerkmale ihres Systems.

WinEI Bewertungen werden nicht mehr während OOBE generiert, noch sind prepop Xml-Dateien, die zum Erstellen von WinSAT formeller Dateien während OOBE verwendet. Es wird empfohlen, dass Sie die formale WinSAT-Datei auf dem System vor der Lieferung an die Endbenutzer generieren. Dies ermöglicht WinSAT-Ergebnisse verfügbar sein soll, sobald Endbenutzer ihre Systeme startet und ermöglicht die Optimierungen, die auf diese Ergebnisse sofort verfügbar sein sollen basieren. Da die Analysen nicht während der Out-of-Box ausgeführt werden auftreten, die WinSAT und WEI Bewertungen werden nicht mehr generiert, wenn ein Benutzer OOBE abgeschlossen ist. Stattdessen können die Faktoren zu zwei Zeiten generiert mithilfe anderer Mechanismen neben Vorausfüllen WinSAT auf dem System, das ausgeliefert wird.

-   Endbenutzer können explizit eine Bewertung anfordern, mithilfe der Option **Bewertung erneut ausführen** im Element Systemsteuerungsoption **Leistungsinformationen und Tools** .

-   Wenn das System nach dem ersten Neustart im Leerlauf befindet, werden die verbleibenden WinSAT-Bewertungen der Wartung Planer verwenden, wenn sie nicht vorausgefüllt wurden ausgeführt.

## <a name="span-idtorunwinsatonacompletesystemspanspan-idtorunwinsatonacompletesystemspanspan-idtorunwinsatonacompletesystemspanto-run-winsat-on-a-complete-system"></a><span id="To_run_WinSAT_on_a_complete_system"></span><span id="to_run_winsat_on_a_complete_system"></span><span id="TO_RUN_WINSAT_ON_A_COMPLETE_SYSTEM"></span>So führen Sie WinSAT auf einem vollständigen system


Verwenden Sie die Option **Prepop** mit dem Befehlszeilentool WinSAT Bewertung für Systeme Komponente ausgeführt.

So führen Sie WinSAT pro Computer (für alle Systeme):

1.  Installieren Sie Windows 8 und Boot im Überwachungsmodus. Weitere Informationen zu den Überwachungsmodus aktiviert finden Sie unter [Übersicht über die Modus überwachen](http://go.microsoft.com/fwlink/?LinkId=214469).

2.  Fügen Sie zusätzliche Komponenten wie Out-of-Box-Treiber.

3.  Führen Sie **WinSAT Prepop**.

    Dadurch wird generiert, die WinSAT prepop .xml führt zu Dateien in das Verzeichnis Datenspeicher befindet sich unter:`%WINDIR%\performance\winsat\datastore\`

4.  \[Optional\] Wenn Sie beabsichtigen, Erfassen dieser Installation für die Bereitstellung auf mehreren Computern ausführen **Sysprep / verallgemeinern/überwachen/Shutdown** und erfassen Sie dann die Installation. Bereitstellen Sie des Abbilds auf einem PC an, die Sie versenden möchten, und starten.

5.  Vergewissern Sie sich, Windows startet im Überwachungsmodus, und führen Sie **WinSAT Moobe**aus.

    Dies generiert eine formelle WinSAT-Datei aus der entsprechenden prepop Dateien und stellt sicher, dass die formale WinSAT-Datei verfügbar ist, wenn der Endbenutzer beim ersten Systemstart. Windows-skaliert, die einige Features basierend auf der formelle WinSAT-Datei, die und wenn diese Datei nicht auf dem System vorhanden ist, und klicken Sie dann das System Leistungsprobleme, einschließlich nicht benötigter Speicher Gerät Defragmentierung auftreten kann fehlende, optimiert Arbeitsspeicher Management und vorab Optimierungen.

    **Hinweis**  
    Um den Zeitraum zu verkürzen, den ein PC werksseitige verbringt, empfehlen wir **WinSAT Prepop** verwenden, wenn Sie Ihre master Windows-Abbilder erstellen. In der Fabrik müssten Sie nur **WinSAT Moobe**ausführen. Wenn Sie **WinSAT Prepop** und **WinSAT Moobe** werksseitige ausführen möchten, können Sie **WinSAT formelle** jedoch stattdessen verwenden. Diese Option erstellt den gleichen Satz von Dateien als **WinSAT Prepop** und **WinSAT Moobe** ausgeführt und sollte in Szenarien verwendet werden, wenn Sie nicht auf Ihre master Windows-Abbilder **WinSAT Prepop** ausführen können.

     

6.  Führen Sie den **Sysprep/oobe** zum Konfigurieren von Windows, OOBE zu starten.

    **Warnung**  
    Ausführen **Sysprep / verallgemeinern** nach **WinSAT Moobe** mit die Ergebnissen löscht, die **WinSAT Moobe** erstellt. Es wird empfohlen, **WinSAT Moobe** oder **formale WinSAT** werksseitige für jeden PC auszuführen, die an einen Kunden ausgeliefert werden soll.

     

Das System ist jetzt bereit, die an einen Kunden geliefert werden. Die Vorteile der Ausführung aller WinSAT-Bewertungen pro Computerabbild ist, dass der Kunde seinen Computer stets eine vollständige Reihe von WinSAT-Ergebnisse verfügt. Auch besitzt die genauesten WinSAT Ergebnisse. In diesem verwenden also genaue Wenn der Consumer bedarfsgesteuerten Bewertung des Systems, verwendet die System eine Bewertung erhalten würde, die Bewertung von WinSAT aufgefüllt wurde, die größer oder gleich.

Vorinstallation soll keine Übertragung von WinSAT Daten zwischen Systemen mit sehr unterschiedliche Funktionen wie zwischen Laptops und Desktops, aktivieren, da die Daten nicht über korrekt sind sehr unterschiedlichen Systeme. Stattdessen dient es WinSAT Daten zwischen ähnliche Systeme Wiederverwendung erleichtern; die Systeme, die dieselbe Hauptplatine/Chipsatz und ähnliche CPU, Grafikkarten und Datenträger enthalten.

Das folgende Verfahren beschreibt, wie WinSAT auf ausgewählte Konfigurationen in einer Zeile von ähnlichen Computern ausführen. Dies beinhaltet die **WinSAT** prepop mehrmals ausgeführt werden.

## <a name="span-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanspan-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanspan-idtorunwinsatforselectivepcconfigurationsandpccomponentsspanto-run-winsat-for-selective-pc-configurations-and-pc-components"></a><span id="To_run_WinSAT_for_selective_PC_configurations_and_PC_components"></span><span id="to_run_winsat_for_selective_pc_configurations_and_pc_components"></span><span id="TO_RUN_WINSAT_FOR_SELECTIVE_PC_CONFIGURATIONS_AND_PC_COMPONENTS"></span>So führen Sie WinSAT für selektive PC-Konfigurationen und PC-Komponenten


1.  Identifizieren Sie die Konfigurationen, die Sie in den PC, einschließlich video Prozessoren, Arbeitsspeicher und Speichergeräten einschließen möchten.

2.  Installieren Sie Windows 8 und Boot im Überwachungsmodus. Weitere Informationen zum Überwachungsmodus finden Sie unter [Überwachen Modus Overview](http://go.microsoft.com/fwlink/?LinkId=214469).

3.  Fügen Sie zusätzliche Komponenten wie Out-of-Box-Treiber.

4.  Führen Sie **WinSAT Prepop**an.

5.  Führen Sie **Sysprep / verallgemeinern / / Reboot überwachen**. Dadurch werden alle nicht Prepop WinSAT XML-Dateien entfernt.

6.  Kopieren der resultierenden WinSAT prepop .xml-Dateien aus `%WINDIR%\performance\winsat\datastore` auf das Netzwerk frei, dass Sie zum Speichern von WinSAT-Ergebnisse verwenden.

7.  Aktualisieren Sie eine der Komponenten. Erhöhen Sie beispielsweise den Arbeitsspeicher eine Konfiguration auf den Computern.

8.  Führen Sie **WinSAT prepop - Speicher** testen. Verwenden das Tool auf diese Weise wird sichergestellt, dass nur für die angegebene Komponente relevant Tests ausgeführt werden. Eine zusätzliche XML-Datei wird generiert, die die Testergebnisse Speicher anzeigt.

9.  Wiederherstellen Sie die ursprüngliche Konfiguration, und aktualisieren Sie eine andere Komponente, wie die Grafikkarte aus.

    **Hinweis**  
    Da WinSAT-Ergebnisse mit der gleichen Konfigurationen verwendet werden können, oder höher, wenn Sie die Basiskonfiguration wiederherstellen, sind die Testergebnisse für eine größere Computer relevant.

     

10. Führen Sie den Test mit erneut aus der **WinSAT prepop - Grafiken** Befehl. Testet, nur für die angegebene Komponente führen Sie relevant. Für die Ergebnisse an Grafiken wird eine zusätzliche XML-Datei generiert.

11. Speichern Sie die neuen Ergebnisdateien mit den XML-Ergebnisse für die Netzwerkfreigabe an.

12. Um die WinSAT-Ergebnisse für einen neuen Computer mit ähnlichen Komponenten auffüllen möchten, kopieren Sie die XML-Dateien von der Netzwerkfreigabe auf dem Zielcomputer WinSAT Datastore Verzeichnis: `%WINDIR%\performance\winsat\datastore`. Den gesamten Satz von WinSAT prepop Dateien aus dem Netzwerk freigeben, können Sie in das lokale WinSAT-Verzeichnis kopieren. WinSAT findet die korrekte Liste für den aktuellen Computer.

13. Auf dem neuen Computer ausführen `WinSAT moobe`. Dies generiert eine formelle WinSAT-Datei aus der entsprechenden prepop Dateien, und es wird sichergestellt, dass die formelle WinSAT-Datei verfügbar ist, wenn der Endbenutzer beim ersten Systemstart. Windows-skaliert, die einige Features basierend auf der formelle WinSAT-Datei, die und wenn diese Datei nicht auf dem System vorhanden ist, und klicken Sie dann das System, einschließlich nicht benötigter Speicherplatz Gerät Defragmentierung, Leistungsproblemen möglicherweise mangelndes, optimiert Arbeitsspeicher Management und vorab Optimierungen.

Wenn das folgende Verzeichnis für Ergebnisdateien untersucht **WinSAT Moobe** WinSAT ausgeführt: `%WINDIR%\performance\winsat\datastore`. Wenn WinSAT nicht relevanten erkennt wird XML-Dateien, Dateien ignoriert und das System als ungefilterte behandeln. Der DWM-Test wird sofort ausgeführt, und die anderen Tests ausgeführt werden, als Wartungsaufgabe oder wenn der Endbenutzer die Tests aus dem Element der Systemsteuerung **Leistungsinformationen und Tools** ausführen möchte. Wenn WinSAT prepop XML-Dateien relevant mehrere findet, verwendet diese die Dateien, um für die Verwendung verfügbar sein wird, wenn der Endbenutzer den Computer zum ersten Mal startet, eine formelle XML-Datei zu generieren. Dies ermöglicht Skalierung von Features und Windows entsprechende Optimierungen ausführen.

WinSAT bestimmt Relevanz mithilfe von Hardware-IDs. Dazu gehören: CPUID, DIMM Speicherkonfiguration, Festplattenmodell und Größe und Video Karte PNP-ID. Wenn die relevante sekundäre Bewertung nicht vorhanden ist, wird WinSAT die primären und sekundären Bewertungsfragen ausgeführt. beispielsweise CPU- und Arbeitsspeicher.

Vorteil von dieser zweite Option auf selektive Konfigurationen ausgeführt wird, dass WinSAT-Bewertungen weniger Konfigurationen ausgeführt und ähnliche Systeme kopiert werden können. Der Nachteil ist, dass wenn eine Reihe von WinSAT-Dateien nicht mit dem aktuellen System relevant ist, diese Tests ignoriert, und das System wird als behandelt nicht klassifizierte und Optimierungen und Featureskalierung werden nicht ausgeführt, wenn der Endbenutzer den Computer gestartet wird.

## <a name="span-idwinsatprepopcommand-lineoptionsspanspan-idwinsatprepopcommand-lineoptionsspanspan-idwinsatprepopcommand-lineoptionsspanwinsat-prepop-command-line-options"></a><span id="WinSAT_Prepop_Command-line_Options"></span><span id="winsat_prepop_command-line_options"></span><span id="WINSAT_PREPOP_COMMAND-LINE_OPTIONS"></span>WinSAT Prepop Befehlszeilenoptionen


**Die Syntax für das Auffüllen lautet wie folgt:**

`Winsat prepop [-datastore <directory>][-graphics | -cpu | -mem | -disk | -dwm]`

Der folgende Befehl führt alle WinSAT Tests: `Winsat prepop`.

Sie können nur eine Subsystem wie DWM, gelten die folgenden Abhängigkeiten vorab aufgefüllt werden.

-   Die DWM-Bewertung kann unabhängig voneinander ausgeführt werden.

-   Die Bewertung Datenträger kann unabhängig voneinander ausgeführt werden.

-   Die CPU-Bewertung erfordert, dass eine Bewertung relevanten Arbeitsspeicher vorhanden ist.

-   Die Arbeitsspeicher-Bewertung erfordert, dass eine entsprechende CPU Bewertung vorhanden ist.

-   Die Bewertung Grafiken erfordert, dass relevante CPU- und Bewertung vorhanden sind.

**Die Syntax für Moobe lautet wie folgt:**

`Winsat moobe [-datastore <directory>]`

**Das WinSAT Dateibenennungsmuster lautet wie folgt:**

Windows 8 ist eine `%type%` Bezeichner, `Prepop`. Dies bezeichnet die Datenspeicher-Dateien, die ein Ergebnis Auffüllung werden. Das Benennungsmuster lautet folgendermaßen:

`%IdentifierDerivedFromDate% %Component%.Assessment(Prepop).WinSAT.xml`

Wobei `%IdentifierDerivedFromDate%` Jahr-Monat-Tag und die Uhrzeit als, beispielsweise ist `0012-08-01 14.48.28` , in dem der Test 2:48:28 Uhr am 1. August 2012 ausgeführt wurde.

Eine formelle WinSAT Datei **Winsat Prepop** gefolgt von **Winsat Moobe**ausführen erstellt; oder verwendet folgende Benennungsmuster **Winsat formelle** ausgeführt:

`%IdentifierDerivedFromDate% Formal.Assessment(Initial).WinSAT.xml`

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Bereitstellungsoptionen](windows-deployment-options.md)

 

 






