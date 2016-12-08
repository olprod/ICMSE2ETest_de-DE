---
title: "Ergebnisse für die Internet Explorer zum Starten des Performance-Bewertung"
description: "Ergebnisse für die Internet Explorer zum Starten des Performance-Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c61f4af5-a8ac-4671-98ca-97aaf72bd4f0
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ff3e22153ad96be8a2ad1185f2dcb996ef59ab94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-internet-explorer-startup-performance-assessment"></a>Ergebnisse für Internet Explorer zum Starten des Performance-Bewertung


Die Bewertung der Leistung von Internet Explorer zum Starten des helfen Ihnen bei die Aktivitäten bewerten, die während der Erstellung einer neuen Internet Explorer-Fenster ausgeführt werden. Die Bewertung misst die Zeit, die benötigt wird, um ein neues Internet Explorer-Fenster auf dem Desktop mit einem einzelnen Registerkarte und einfacher Inhalte vollständig zu rendern. Diese Messung enthält die Ladezeit der Prozess IExplore.exe und der Frame-Erstellung und Registerkarte Intervallen.

Auch die Leistung von Erweiterungen, die geladen und initialisiert während des Starts werden gemessen. Es gibt verschiedene Arten von Erweiterungen, einschließlich Kontextmenüs, Symbolleisten, Explorer-Leisten und Browser-Hilfsobjekte (BHO). Um die Typen von Erweiterungen, die auf einem Computer in Internet Explorer, klicken Sie im Dialogfeld **Add-ons verwalten** installiert sind, finden Sie unter rechts wählen Sie die Spaltenüberschrift, wählen Sie **Spalten aus** , und **Wählen Sie dann**.

In diesem Thema können Sie die Ergebnisse, die mit der Leistung von Internet Explorer zum Starten des Bewertung zu interpretieren helfen. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die benutzerfreundlichkeit beim Starten von Internet Explorer auswirken.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-iestartupmetrics)

-   [Probleme](#bkmk-iestartupissues)

Weitere Informationen zu Systemanforderungen und Bewertung Einstellungen finden Sie unter [Start Leistung im Internet Explorer](internet-explorer-startup-performance.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse-Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für eine große Desktopcomputer festgelegten oder Markt erwartet können sich so, dass Sie die Flexibilität benötigen, um verschiedene Ziele zu definieren und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Wenn an das Ziel dieser Metrik ein metrischer Wert verglichen wird, wird der Status farblich in der Ansicht Ergebnis wie folgt:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass das Benutzererlebnis zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse um die Verbesserungen anzuzeigen, die mit dem System hergestellt werden kann. Dabei kann es sich um Software Änderungen, konfigurationsänderungen oder Hardware suchen handeln. Möglicherweise müssen Sie Kompromisse hochwertige übermitteln, die Windows-Erfahrung erwägen.

-   Keine Farbe bedeutet, dass keine Ziele für die Metrik definiert sind.

**Hinweis**  
In der Windows Assessment Toolkit für Windows 8 umfassen einige Bewertung Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows 10 können.

 

Sie können legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, um die benutzerdefinierten Ziele anzuwenden. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Zu einem Zeitpunkt kann nur eine Ziele Datei verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Sie können die Ziele Beispieldatei, das bereitgestellt wird unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele zum Erstellen Ihrer eigenen Ziele Datei.

**Hinweis**  
Eine Datei Ziele mit einem Auftrag keine Pakete, aber Sie können auf einer anderen Personen zur Freigabe speichern.

 

## <a name="a-href-idbkmk-iestartupmetricsametrics"></a><a href="" id="bkmk-iestartupmetrics"></a>Metriken


In diesem Abschnitt werden die Metriken allgemeine Bewertung der schlechte Ergebnisse für die einzelnen metrische und mögliche Behebung dieser Probleme bewirkt, dass Internet Explorer beim Starten. Die Metriken werden die Phasen des Internet Explorer zum Starten des ausgerichtet. Es gibt sechs Phasen des Internet Explorer zum Starten des: verarbeiten, Erstellung, Frame, Registerkarte erstellen, Erweiterung Erstellung (CoCreateInstance), Erweiterung Initialisierung (Set Site) und docking-Fenster (bei einigen Erweiterung) anzeigen. Hier werden die entsprechenden Metriken behandelt.

**Hinweis**  
Die auf höchster Ebene **IE Startup Dauer** Metrik ist umfassend und umfasst Aufgaben, die ausgeführt werden, nachdem der Prozess, Rahmen und Registerkarte erstellt wurden.

 

-   [Erstellen von Internet Explorer-Prozess](#bkmkl-createieprocess)

-   [Internet Explorer-Fenster erstellen](#bkmk-ieframecreate)

-   [Erstellen von Internet Explorer-Registerkarte](#bkmk-ietabcreate)

-   [Erstellen von Erweiterungen Addon Count](#bkmk-createextension)

-   [Legen Sie die Website für Extensions](#bkmk-setextension)

-   [Erweiterung Symbolleiste anzeigen andocken, Fenster](#bkmk-extensiontoolbar)

**Hinweis**  
Wenn Sie die Einstellung Diagnostic Minifilter-Modus aktivieren aktiviert haben, werden die Bewertungsergebnisse Minifilter Metriken enthalten. Informationen zu Minifilter Metriken und Ergebnisse finden Sie unter [Minifilter Diagnosen](minifilter-diagnostics.md).

 

### <a name="a-href-idbkmkl-createieprocessacreate-internet-explorer-process"></a><a href="" id="bkmkl-createieprocess"></a>Erstellen von Internet Explorer-Prozess

**Am besten:** Gerätehersteller, Softwarehersteller Anti-malware

Diese Metrik misst die Zeit, die benötigt wird, um Internet Explorer-Prozesses zu erstellen. Dazu gehört das Zeitintervall aus zu Beginn das Betriebssystem laden und Ausführen von iexplorer.exe, wenn Internet Explorer zeigt an, dass er die erstellen Frame Phase der Initialisierung begonnen hat. Oder das Zeitintervall aus beim iexplorer.exe starten (die von der Windows-Kernel gemeldet) bis im Freigabefenster Frame erstellen (die von Internet Explorer gemeldet) gestartet wird.

**Typische Schlüsselfaktoren Faktoren**

-   CPU-Geschwindigkeit

-   Anti-malware

**Analyse und Schritte zur Wiederherstellung**

Wenn die Bewertung konsistent meldet, dass diese Stufe zu lange dauert, wird eingehenderen Analysen in WPA die Ursache suchen empfohlen.

### <a name="a-href-idbkmk-ieframecreateainternet-explorer-frame-create"></a><a href="" id="bkmk-ieframecreate"></a>Internet Explorer-Fenster erstellen

**Am besten:** Den Herstellern Anti-Malware Softwarehersteller, Video-Treiber-Entwickler

Diese Metrik misst die Zeit, die zum Rendern von vollständig in Internet Explorer sowie das Zeitintervall Start vor Internet Explorer die erste Registerkarte erstellt und dem Laden und werden keine Erweiterungen initialisiert, einschließlich ein Fenster auf oberster Ebene (Frame) erstellen und initialisieren Direct3D Rendern in diesem Fenster eines Fensterrahmens. Internet Explorer-Frame ist der übergeordnete Prozess und die Benutzeroberfläche Container für die Registerkarten in einem einzelnen auf oberster Ebene Internet Explorer-Fenster. Registerkarten in einem gesonderten Prozess gehostet werden, aber der übergeordnete Prozess ist verantwortlich für die Ausgabe der Ablaufverfolgungsereignisse, die für die Bewertung Analyse verwendet werden.

**Typische Schlüsselfaktoren Faktoren**

-   CPU-Geschwindigkeit

-   Anti-malware

-   Grafikkartentreiber

**Analyse und Schritte zur Wiederherstellung**

Wenn die Bewertung konsistent meldet, dass die Dauer des Textrahmens in Internet Explorer zu lange dauert, führen Sie den WPA weiteren Analyse Link, um finden Sie unter Erweiterte Details, und suchen Sie die Ursache.

### <a name="a-href-idbkmk-ietabcreateainternet-explorer-tab-create"></a><a href="" id="bkmk-ietabcreate"></a>Erstellen von Internet Explorer-Registerkarte

**Am besten:** Gerätehersteller, Softwarehersteller Modul

Diese Metrik misst die Zeit, die zum Erstellen einer neuen Registerkarte in Internet Explorer, einschließlich das Zeitintervall für das Erstellen und Initialisieren einer Registerkarte in einem Frame sowie erstellen und initialisieren aller seiner Extensions. Die Registerkarte ist der Prozess und die Benutzeroberfläche Container für eine einzelne Registerkarte und seinen Inhalt. Es ist immer mindestens eine Registerkarte zwar mehrere Registerkarten in demselben Prozess gehostet werden können. Erweiterungen werden erstellt und in der Registerkarte Prozess initialisiert.

**Typische Schlüsselfaktoren Faktoren**

-   CPU-Geschwindigkeit

-   Modul

-   Extensions

**Analyse und Schritte zur Wiederherstellung**

Für die Analyse der Erweiterung Leistung sollten Sie sich auf die verschiedenen Erweiterung-bezogene Metriken wie erstellen und Set Site konzentrieren. Wenn diese Stufe wird als braucht zu lange konsistent gemeldet, aber die Leistung der einzelnen Extensions nicht gekennzeichnet werden wird, folgen Sie jedoch den WPA weiteren Analyse Link, um finden Sie unter Erweiterte Details, und suchen Sie nach der Ursache.

### <a name="a-href-idbkmk-createextensionacreate-extensions-addon-count"></a><a href="" id="bkmk-createextension"></a>Erstellen von Erweiterungen Addon Count

**Am besten:** Den Herstellern, Softwarehersteller Anti-malware

Diese Metrik zählt Add-ons in Internet Explorer die Aktion CreateExtension beteiligt. Sie können diese Metrik, um eine Liste der jede Erweiterung und deren entsprechende Dauer finden Sie unter erweitern. Für jede wird die Zeit, die zum Instanziieren einer Erweiterungs von CoCreateInstance() gemessen. Dazu gehören auch die Zeit, die Erweiterung DLL und alle abhängigen DLL statischen geladen werden. Wenn Internet Explorer ein Add-on initialisiert wird, ruft es zuerst die CoCreateInstance()-Funktion mit den hinzufügen-auf die CLSID, das wiederum das Add-on aufruft des Moduls DllGetClassObject() Funktion zum Erstellen eines Objekts im Arbeitsspeicher. Add-Ons führen Sie in der Regel eine Verzögerung für die Leistung bei diesen Funktionsaufruf, entstehen keine. Jedoch ist es wichtig, um den Fokus auf diesen Funktionsaufruf beim Optimieren der Leistung beim Systemstart, da geringe Leistung auf Add-ons verknüpft werden kann.

**Typische Schlüsselfaktoren Faktoren**

-   CPU-Geschwindigkeit

-   DLL Abhängigkeiten

-   Synchronous oder Blockieren von e/a-Vorgänge (Datenträger oder im Netzwerk)

-   Modul

**Analyse und Schritte zur Wiederherstellung**

Eine Erweiterung sollte nicht der Fall ist sehr viel während dieser Phase, daher kann eine beliebige einfacher Zeitraums hier ein Problem sein. Für den Herstellern müssen Sie möglicherweise die Erweiterung deinstallieren. Für die Erweiterung Autoren wird zusätzlich zu einer Überprüfung der folgenden Bereiche des Codes für die Erweiterung des Codes eingehenderen Analysen in WPA empfohlen:

-   **DllMain**: selten die DllMain-Methode, um eine nicht triviale Zeitspanne während dieser Phase verbringen.

-   **DllGetClassObject**: selten der DllGetClassObject-Methode, um eine nicht triviale Zeitspanne während dieser Phase verbringen.

-   **Klasse Konstruktor (C++) (oder äquivalente Berechtigungen)**: eine Erweiterung sollte nicht zu viele während der Erstellung, einschließlich den Konstruktor für die Klasse, die wird (die Klasse, durch die CLSID bezeichnet) erstellt.

-   **Statische DLL Abhängigkeiten**: Hierbei handelt es sich um DLLs, die mindestens eine statische Import bei Bedarf aus der DLL-Erweiterung aufweisen. Sie müssen geladen und aufgelöst, bevor Windows zurückgegeben wird, aus der LoadLibrary()-Aufruf von Internet Explorer, unabhängig davon, ob sie tatsächlich verwendet werden.

    Dies schließt nicht DLLs, die Verzögerung geladen werden, sind mit/DELAYLOAD oder LoadLibrary().

    Wenn eine bestimmte DLL nur gelegentlich verwendet wird, oder beim Starten oder während der Initialisierung nicht verwendet, sollten erwägen Sie, / delayload zu verwenden.

-   **Dynamische DLL Abhängigkeiten**: Wenn die Erweiterung LoadLibrary() API des oder eine DLL, die in der Liste/DELAYLOAD ist aufruft, diese Verwendung überprüft werden sollten, um festzustellen, ob es bis zu einem späteren Zeitpunkt verzögert werden kann. Wenn eine DLL verzögert geladen ist, aber wird immer beim Starten oder während der Initialisierung verwendet, sollten Sie aus der Liste/DELAYLOAD entfernt.

    **Hinweis**  
    Dies sollte nicht für alle Windows-APIs durchgeführt werden, die aufgerufen werden, je nachdem, welche Version von Windows ausgeführt wird; die sollte immer verzögert geladen sein. Beispielsweise, wenn eine Erweiterung DirectWrite zum Rendern von Text verwendet und GDI ersatzweise verwendet, soll klicken Sie dann es statisch zu dwrite.dll verknüpft werden. Auf diese Weise kann vollständig deren Laden in früheren Versionen von Windows verhindern.

     

**Weitere Informationen**

[MSDN: / DELAYLOAD (Laden von Import verzögern)](http://msdn.microsoft.com/library/yx9zd12s.aspx)

### <a name="a-href-idbkmk-setextensionaset-site-for-extensions"></a><a href="" id="bkmk-setextension"></a>Legen Sie die Website für Extensions

**Am besten:** Erweiterung Autoren, den Herstellern

Diese Metrik zählt Internet Explorer Addons SetSite-Aktion beteiligt. Sie können diese Metrik, um eine Liste der jede Erweiterung und deren entsprechende Dauer finden Sie unter erweitern. Die Zeit, die für Internet Explorer in die Erweiterung IObjectWithSite::SetSite()-Methode aufrufen, wird für jede gemessen. Diese Methode stellt die Erweiterung Fähigkeit zur Kommunikation mit Internet Explorer her. Erweiterungen führen Sie in der Regel den Großteil hier starten/Initialisierung. Dies richtet die hinzufügen-auf die erste Kommunikation mit Internet Explorer, und wird durch die IObjectWithSite-Schnittstelle die implementieren müssen, alle Internet Explorer Add-ons verfügbar gemacht werden. Add-Ons, die in der Regel die Initialisierungsroutinen in dieser Funktion wie Symbolleiste Benutzeroberfläche anzeigen oder Laden von anderen Modulen ausgeführt werden.

**Typische Schlüsselfaktoren Faktoren**

Dies wird in der Regel nur durch die Erweiterung Implementierung der IObjectWithSite::SetSite() beeinflusst. Es ist wichtig vermeiden synchrone/Blockierung Datenträger oder über das Netzwerk e/a so weit wie möglich, während diese Methode.

**Analyse und Schritte zur Wiederherstellung**

Für den Herstellern müssen Sie möglicherweise die Erweiterung deinstallieren. Erweiterung Autoren wird neben einer Überprüfung des Codes der Implementierung IObjectWithSite::SetSite() eingehenderen Analysen mit WPA empfohlen. Es kann Teile dieses Codes die können bis zu einem späteren Zeitpunkt zurückgestellt, oder vielleicht asynchron durchgeführt werden, sodass diese mit der Initialisierung des anderen-Plug-Ins parallel ausgeführt werden können.

**Weitere Informationen**

[MSDN: IObjectWithSite-Schnittstelle](http://msdn.microsoft.com/library/aa768220.aspx)

### <a name="a-href-idbkmk-extensiontoolbaraextension-toolbar-show-docking-window"></a><a href="" id="bkmk-extensiontoolbar"></a>Erweiterung Symbolleiste anzeigen andocken, Fenster

**Am besten:** Erweiterung Autoren (Symbolleisten und nur Explorer-Leisten), den Herstellern

Diese Metrik zählt Internet Explorer Addons, die eine separate-Symbolleiste anzuzeigen. Sie können diese Metrik um eine Liste der jede Erweiterung und deren entsprechende Dauer finden Sie unter erweitern. Für jede dieser wird das Intervall der Zeit, in der Implementierung IDockingWindow::ShowDW() wird gemessen. Wenn das Add-on Initialisieren einer Symbolleiste oder Explorerleiste ist, ruft Internet Explorer die Add-on IDockingWindow::ShowDW()-Funktion, um das Add-on im Browserfenster sichtbar zu machen. Einige Add-ons festlegen, dass ihre Code zum Rendern der Benutzeroberfläche diese Funktion ausgeführt, daher kann es auch zum Starten des-Leistung beeinflussen.

**Typische Schlüsselfaktoren Faktoren**

-   CPU-Geschwindigkeit

-   Komplexität der Benutzeroberfläche angezeigt wird oder initialisiert

**Analyse und Schritte zur Wiederherstellung**

Für den Herstellern müssen Sie möglicherweise die Addon deinstallieren. Erweiterung Autoren wird neben einer Überprüfung des Codes der Implementierung IDockingWindow::ShowDW() eingehenderen Analysen mit WPA empfohlen.

Wenn die Erweiterung UI Code zum Rendern, beispielsweise WM läuft\_PAINT möglicherweise verschoben, es bis zu einem späteren Zeitpunkt, je nach die Erweiterung wie geschrieben wurde. Wenn es nicht möglich oder zur Vermeidung von Code zum Rendern der möglich ist (WM\_PAINT) während dieser Phase können Sie versuchen, die mit der folgenden Strategie Rendering oder einer ähnlichen zu verzögern.

1.  Nach dem Erstellen und anzeigen das wichtigste HWND für die Erweiterung Benutzeroberfläche, aber bevor Sie keine untergeordneten Fenster hinzufügen, SendMessage zum Senden einer WM verwenden\_SETREDRAW Nachricht mit wParam gleich FALSE.

    **Warnung**  
    Dadurch werden alle Zeichnen für das Fenster vorübergehend deaktiviert. Dies sollte sorgfältig verwendet werden. Wenn es nicht richtig verwendet wird, können Probleme, die schwierig zu debuggen.

     

2.  Im nächsten Schritt erstellen und die untergeordneten Windows oder Inhalte hinzufügen.

3.  Senden Sie dem Fenster ein anderes WM\_SETREDRAW Nachricht mit wParam gleich TRUE.

4.  Verwenden Sie die InvalidateRect oder RedrawWindow, um das Fenster zu aktualisieren.

5.  Geben Sie IDockingWindow::ShowDW() zurück.

**Zusätzliche Informationen**

[MSDN: IDockingWindow::ShowDW-Methode](http://msdn.microsoft.com/library/windows/desktop/bb762050.aspx)

[MSDN: WM\_SETREDRAW Nachricht](http://msdn.microsoft.com/library/dd145219%28v=vs.85%29.aspx)

## <a name="a-href-idbkmk-iestartupissuesaissues"></a><a href="" id="bkmk-iestartupissues"></a>Probleme


Die Leistung von Internet Explorer zum Starten des Bewertung führt eine Problemanalyse der erweiterten und enthält Links zu Windows® Performance Analyzer (WPA) von Problemen, die identifiziert werden. Wenn WPA ausführliche Informationen über die Datenträgeraktivität öffnet oder CPU-Aktivität ist möglicherweise verfügbar, je nach Art des Problems identifiziert. Weitere Informationen zu eingehenderen Analysen Probleme und Empfehlungen finden Sie unter, [Depth Analysis Probleme](common-in-depth-analysis-issues.md).

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Internet Explorer zum Starten des Leistung](internet-explorer-startup-performance.md)

[Bewertung](assessments.md)

[Ein-/ausschalten Übergang-Leistung](onoff-transition-performance.md)

 

 







