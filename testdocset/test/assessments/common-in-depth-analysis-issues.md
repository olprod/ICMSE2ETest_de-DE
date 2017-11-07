---
title: "Häufige Probleme von eingehenderen Analysen"
description: "Häufige Probleme von eingehenderen Analysen"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 00b00834-8c8e-4f46-bf5e-40c15903f026
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: bc5b3644c806d5dac56cdada9c25d2a40e00530e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="common-in-depth-analysis-issues"></a>Häufige Probleme von eingehenderen Analysen


Bewertung Grenzwerte vordefinierte Analyse für die Durchführung einer Aktivität, die sie gemessen wird. Bewertung identifizieren und Probleme melden, wenn die Dauer der Aktivität diese Grenzwerte überschreiten. Einige Bewertung im Windows Assessment Toolkit durchführen erweiterte Problem Analysen können. Sie können diese Probleme in der Windows-Assessment-Konsole und das Windows-Assessment-Services - Client (Windows ASC), anzeigen und Analysieren von sie weitere in Windows Performance Analyzer (WPA).

**Hinweis**  
Probleme, die von der Bewertungsfragen generiert werden stammen aus verschiedenen Quellen. In diesem Thema werden nur einige häufig auftretende Probleme erweiterten Analyse.

 

In der Windows-Assessment-Konsole und Windows ASC, ermittelte durch Bewertung 2 Positionen angezeigt: in der linken Spalte der Seite **Ansicht "Suchergebnisse"** und im Detailbereich auf der rechten Seite. Klicken Sie auf der Seite **Ergebnisse anzeigen** angezeigt Probleme, Warnungen und Fehler in der Tabelle mit den ausführen und in der Ergebnistabelle Bewertung. Sie können diese Probleme gruppieren, indem Sie **Probleme** mit der rechten Maustaste, und klicken Sie dann auswählen Kriterien, nach denen gruppiert. Klicken Sie im Detailbereich werden Probleme nach Schweregrad sortiert. Sie können sie mithilfe von Schlüsselwörtern und Metadaten filtern. Weitere Informationen finden Sie unter [Gruppen, Filter und Suchproblemen](group-filter-and-search-issues.md).

Wenn Sie über den Link in der Ergebnisanzeige WPA öffnen, sehen Sie eine Liste der Probleme, die die Bewertung im Fenster WPA **Probleme** identifiziert wurde. Bei der Auswahl eines dieser Probleme werden Details und empfohlene Lösung im Fenster WPA **Details** angezeigt. Weitere Informationen zu WPA finden Sie unter [Windows Performance Analyzer](http://go.microsoft.com/fwlink/?LinkId=214551).

In diesem Thema:

-   [Problem Format](#formatissue)

-   [Verwalteter code](#managedcode)

-   [Prozessorverwendung](#excessprocessor)

-   [Speicher verwenden](#excessstorage)

-   [Verzögert die Verarbeitung](#processingdelays)

-   [Speicher e/a-Verzögerungen](#storageiodekays)

-   [Registrierung geleert](#registryhiveflushes)

-   [Zeit Buchhaltung](#timeaccounting)

-   [Fehlende Symbole](#missingsymbols)

-   [DPCs und ISRs](#dpcisr)

-   [Zusammenfassung der Probleme](#summaryissues)

-   [Assessment-Protokollierung](#logging)

## <a name="a-href-idformatissueaissue-format"></a><a href="" id="formatissue"></a>Problem-Format


Die meisten Probleme, die im Detailbereich in die Windows-Konsole zur Bewertung und die Windows-ASC angezeigt haben eine allgemeine Struktur, die enthalten kann:

-   **Titel**

    Titel enthält wichtige Informationen zu einem Problem, wie Metriken, die das Problem und der Name der Aktivität, die betroffen war quantifiziert. Titelinformationen kann auch die Phase enthalten, der die Bewertung in war, wenn das Problem erkannt wurde.

-   **Empfehlung**

    Wenn möglich, werden im Detailbereich Schritte aus, um eine gefundene Problem zu beheben. Und in einigen Fällen bietet Anleitungen für die Untersuchung des Problems weiterhelfen. Methoden oder bewährte Methoden können Sie das Optimieren der Leistung oder auf andere Weise beheben des Problems, das die Bewertung identifiziert, kann diese Informationen enthalten.

-   **Weitere Informationen**

    In einigen Fällen werden im Detailfenster Zusatzinformationen als einen Link zu einer Website, die Informationen zu den Schritten bereitstellen kann, die Sie ergreifen können, um dieses Problem zu beheben.

-   **Weitere Analysen**

    Erweiterte Analyse Probleme werden im Detailbereich WPA eingehenderen Analysen Link, damit Sie können WPA öffnen und untersuchen Sie die Quelle des Problems weiter.

    Wenn WPA geöffnet wird, möglicherweise zusätzliche Details je nach Art des Problems verfügbar sein, die die Bewertung erkannt werden, z. B.:

    -   Prozess Image-Details enthalten und die Versionsinformationen Informationen zu der Prozess, das identifizierte Problem erzeugt, einschließlich:

        -   Dateiname

        -   Dateipfad

        -   Beschreibung der Datei

        -   Dateiversion

        -   Hersteller

    -   Zusammenfassung der Datenträgeraktivität von der Datei, einschließlich:

        -   Größe und Anzahl der Datenträgerlese- und Schreibvorgänge

        -   Anzahl der Datenträger geleert

    -   Zusammenfassung der CPU-Aktivität, indem Sie/Prozessthreads, einschließlich:

        -   Auswirkung, im Hinblick auf die CPU-Zeit jedes Threads des Prozesses

        -   Rufen Sie Stapel an, die die Leistungseinbußen aufgetreten ist und wie lange anzeigen

    -   Zusammenfassung der Verzögerungen, die durch einen Prozess oder Threads, einschließlich von CPU oder Festplatten-Aktivität verursacht werden:

        -   Threads oder Prozesse, die verzögert wurden, einschließlich der Dauer der die Verzögerung

        -   Auswirkung der einzelnen Thread des Prozesses, einschließlich der Dauer der die Verzögerung

        -   Stapel für jeden Thread, die bewirkt, dass die Verzögerung oder von dieser betroffen ist

            **Hinweis**  
            Die Informationen, die die Anruf Stapeln bereitstellen ist eine statistische Darstellung einer Aktivität. Die Genauigkeit hängt von der Beispiele, die die Bewertung erfasst.

             

## <a name="a-href-idmanagedcodeamanaged-code"></a><a href="" id="managedcode"></a>Verwalteter Code


Verwalteter Code bezieht sich auf Code, unter dem Microsoft .NET Common Language Runtime (CLR) ausgeführt wird. Die CLR verwaltet die Ausführung von Anwendungen, die auf Microsoft .NET Framework basieren. CLR-Prozesse starten beim Start von Windows und können dazu führen, dass zusätzliche Ressourcenverbrauch die Startzeit erweitern können. Dateien, die während der Initialisierung CLR .NET Framework liest können MB Speicher Lesevorgänge, die den Startvorgang verzögert werden können und die Darstellung des Bildschirms **Starten** hinzufügen.

**Problem-Beispiel**

* &lt;X&gt;*.exe ist der Prozess zum Starten des verwaltetem Code.

**Empfehlung**

Probleme in der Kategorie von verwaltetem Code ist ein .NET Framework-basierten Anwendung oder Dienst entscheidender Faktor in der Windows-Boot sollten Sie die Verwendung von verwaltetem Code vermeiden. Wenn Sie die Verwendung von verwaltetem Code nicht vermeiden lässt, sollten verzögern des .NET Framework-basierten Anwendung oder zu vermeiden, angesichts der Ressourcen, die für andere wichtige Anwendungen erforderlich sind oder beim Start von Windows-Dienste starten.

Mithilfe von verwaltetem Code umfasst einige Beeinträchtigung der Systemleistung und der Aufwand pro Aufruf kaum erkennbar werden kann. Im Bereich **Weitere Analyse** des Problems auf den WPA eingehenderen Analysen Link zum Ermitteln der Aufwand und verringern Sie die Verzögerungen gemäß der folgenden Schritte aus:

-   Vermeiden der Verwendung von verwalteten Codes nicht benötigten in der Startpfad.

-   Verwenden Sie den Taskplaner, um Anwendungen später zu starten.

-   Starten Sie Anwendungen nur auf Anforderung oder ausgelöst. Weitere Informationen finden Sie unter [ \[MSDN\] Entwickeln von effizienten Hintergrund Prozess für Windows](http://go.microsoft.com/fwlink/?LinkId=233633).

## <a name="a-href-idexcessprocessoraprocessor-use"></a><a href="" id="excessprocessor"></a>Prozessorverwendung


Hohe CPU-Verwendung durch Anwendungen und Dienste kann zur benutzerfreundlich, wie UI-Anwendungen und Video und Sound Fehler beitragen. Ein Prozessthread, der unter normalen oder hohe Priorität ausgeführt wird, einen Schwellenwert für die Verwendung von CPU-Ressourcen überschreitet, wird die Bewertung Kennzeichen des Prozesses als ein Problem und berechnet die Verzögerung. Wenn ein einzelner Prozess zu viel CPU verwendet, können andere Prozesse verzögert werden, da diese für Systemressourcen konkurrieren müssen. Generierte Probleme sind farblich als roten oder gelben im Hinblick auf deren Einfluss auf die CPU.

**Problem-Beispiel**

Prozess * &lt;X&gt; * verwendet die CPU für 5.3 Sekunden während des Starts Fast on/off Post fortsetzen.

**Empfehlung**

Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link, um zu bestimmen, welche Funktion des Prozesses weitere Untersuchung benötigt. Übermäßig viele Prozessorverwendung kann in mehr als einem Thread zu einem Zeitpunkt auftreten. Für jeden Thread, der beteiligt ist, wird zeigen Sie die Funktion Call-Stapel in WPA an.

**Hinweis**  
Die Informationen, die die Anruf Stapeln bereitstellen ist eine statistische Darstellung einer Aktivität. Die Genauigkeit hängt von den Beispielen, die erfasst die Bewertung ab.

 

## <a name="a-href-idexcessstorageastorage-use"></a><a href="" id="excessstorage"></a>Speicher verwenden


Ausführung eines Prozesses Speicher liest oder schreibt leert zur Laufzeit. Da eine Festplatte eine einzelne freigegebene Ressource, übermäßig viele ist oder unnötiger Verwendung der Speicherung möglicherweise erhebliche zu Leistungsproblemen führen, die identifiziert der Bewertung.

**Beispiele für Problem**

Prozess * &lt;X&gt;*.exe liest 23 Megabyte (MB) aus dem Speicher während des Starts Fast fortsetzen Post ein-/ausschalten.

Prozess * &lt;X&gt;*.exe leert 12-Mal in den Speicher beim schnellen Start Resume Post ein-/ausschalten.

**Empfehlung**

Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link, um eine Übersicht über die oberen e/a-Datei zu prüfen. Verwenden Sie diese Liste Dateien zu finden, die dazu führen, übermäßig viele Lese- oder Schreibvorgänge dass. Datenträger geleert suchen Sie in der Call-Stapel, die auf die Quelle zeigen.

-   Übermäßig viele Lese- oder Schreibvorgänge wird empfohlen, dass Sie die Menge der Daten, dass der Prozess verarbeitet oder lesen und Schreiben in einem späteren Zeitpunkt verzögern reduzieren.

-   Für ein e/a, die reduziert oder zurückgestellt ist nicht möglich, empfehlen wir die Verwendung von e/a-Größe von 64 KB (Kilobyte) 128 KB bis kleine störende Streams zu vermeiden, die andere ausstehende e/a-Aktivität erheblich beeinträchtigen können.

-   Datenträger geleert Auswirkungen e/a-Aktivität durch andere Prozesse auf. Nur, wenn sie erforderlich sind, sollten Sie Datenträger geleert durchführen.

## <a name="a-href-idprocessingdelaysaprocessing-delays"></a><a href="" id="processingdelays"></a>Verzögert die Verarbeitung


Wenn ein Thread CPU oder Festplatten Ressourcen verwendet wird, wird er die Dauer der Aktivität erhöht. Konflikte häufig über dem Prozessor-Manifeste als Thread blockieren und/oder trennen. Im Analyseabschnitt dieses Problem besteht aus alle Threads betroffen durch den Prozess, der zuerst unterbrochen oder Sicherstellung und Scanthreads später, nachdem der Prozess abgeschlossen wurden.

Ein Thread wartet Arbeit abgeschlossen. Nach dem Abschluss der Arbeit bereitet die DPC dieses wartenden Threads.

Die Thread-ID der wartenden Threads und seine kumulierte Wartezeit in der Problemdetails angezeigt werden. Erweitern Sie die Problemdetails anzeigen des Stapels Wait dieses Threads.

Komplexer Aktivitäten ist es-Parametern ein Thread in einem anderen Thread zu warten, das in einem anderen Thread, die für die Arbeit wartet abgeschlossen wartet. Eine DPC mit Thread, der Planer oder einen anderen Mechanismus bereitet die neuesten wartenden Threads. Diese neuesten wartenden Threads noch einmal ausgeführt, und bereitet wartenden Threads. Der Prozess wird mit den einzelnen wartenden Threads wiederholt, bis der früheste wartende Thread Scanthreads ist und erneut ausgeführt.

Die Problemdetails werden diese Abfolge von Steuerung in chronologischer Reihenfolge beschrieben. Beispiel:

Der Prozess csrss.exe (600) wartet 374 Millisekunden 712 Thread

Der Prozess explorer.exe (1836) wartet 374 Millisekunden 2724 Thread

Thread 4748 des Prozesses explorer.exe (1836) ausgesetzt 373 Millisekunden

Timer DPC bereitet Thread 4748

Thread 4748 bereitet wartenden Threads 2724

Thread 2724 bereitet wartenden Threads 712

Während einer Aktivität kann die gleichen Steuerung oft wiederholen. Die Wartezeiten sind kumulativ.

Wählen Sie einen Satz an, der beschreibt ein wartenden Threads, um einen Stapel anzuzeigen, der die Anzeige für wartende-Funktion enthält. Wählen Sie einen Satz an, der einen Thread Vorbereitung einer anderen Thread, um einen Stapel anzeigen, der die Funktion readying zeigt beschreibt.

Der Anzeige für wartende Stapel von im innersten Thread, Thread 4748 im obigen Beispiel bietet in der Regel sollten über die Quelle für die Verzögerung. Vor der Anzeige für wartende-Funktion zusammen mit der Informationen, die den Stapel folgt Stack-Frames vorsehen Aufschluss über das Problem weiter.

Verzögert die Verarbeitung Typen:

-   **CPU-Verwendung**

    Wenn ein Thread ausgeführt wird – unabhängig von dessen Priorität, während die Aktivität, die Sie analysieren – verbraucht CPU-Zeit, verzögern kann, Abschluss und für die gesamte Zeit der Aktivität beiträgt.

    **Problem-Beispiel**

    CPU-Verwendung durch Prozess * &lt;X&gt; * verzögert die Aktivität, schneller Start Resume Explorer Initialisierung 125 Millisekunden.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link Call-Stapel für den Thread zu analysieren, die bewirkt, die Verzögerung dass.

-   **Blockieren**

    Thread blockieren, das auftritt, während der Ausführung eines Prozesses kann eine Verzögerung bei der Durchführung einer Aktivität führen. Ein Thread ist Sicherstellung, wenn es bereit zur Ausführung ist, aber andere Threads verhindern, dass er sofort ausgeführt.

    **Problem-Beispiel**

    Prozess * &lt;X&gt; * Sicherstellung ist. Das Blockieren von verursacht eine Verzögerung auf die Aktivität Fast Start Resume Explorer Initialisierung von 50 Millisekunden.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems die WPA eingehenderen Analysen Link, um anzuzeigen, welche Thread Sicherstellung wurde und welche Thread oder Threads den betreffende Thread die Ausführung verhindert. Bestimmen Sie die Ursache für das Blockieren des Threads, indem Sie die Problemdetails betrachten, und beobachten die Funktion Stapel aufrufen.

-   **Unterbrechung**

    Wenn ein anderer Thread, der eine höhere Priorität hat stattdessen ausgeführt wird, wird ein ausgeführter Thread belegt. Der höhere Priorität Thread verursacht eine Verzögerung bei der Durchführung der andere Thread-Aktivität.

    **Problem-Beispiel**

    Prozess * &lt;X&gt; * unterbrochen ist. Die Unterbrechung verursacht eine Verzögerung auf die Aktivität Fast Start Resume Explorer Initialisierung von 150 Millisekunden.

    **Empfehlung**

    Weitere Informationen zum Planen von Thread finden Sie unter [Thread planen](http://go.microsoft.com/fwlink/?LinkId=242231).

-   **Den Energiesparmodus versetzt wird**

    Threads den Energiesparmodus versetzt wird, wenn sie eine der verfügbaren Windows dem Standbymodus Funktionen, wie **SleepEx**anrufen. Dies führt zu eine Verzögerung bei der Durchführung der Threadaktivität.

    **Problem-Beispiel**

    Prozess * &lt;X&gt; * die Aktivität schneller Start brechen Sie LEISTE Gerät im Ruhezustand 4.0 Sekunden verzögert.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen-Link ein. Sie können bestimmen, dass die Ursache des Threads Standbymodus aus der Funktion Stapel und die Dateiinformationen aufrufen kann.

## <a name="a-href-idstorageiodekaysastorage-io-delays"></a><a href="" id="storageiodekays"></a>Speicher e/a-Verzögerungen


Wenn ein Thread Speicherressourcen verwendet wird, können sie die Dauer der Aktivität erhöhen. Bei mehreren Threads für die Verwendung des Speichers konkurrieren, sucht die resultierende zufällige Festplatten stellen Verzögerungen wichtiger.

Die Typen der Speicher Verzögerungen umfassen:

-   **Speicher Lese- und Schreibvorgänge**

    Die folgende Probleme enthält die Summe aller Verzögerungen, die Ursache liest (oder schreibt) während einer Aktivität.

    **Problem-Beispiel**

    Aktivität Fast Start Resume Explorer Initialisierung verursacht eine zweite 1.2 Verzögerung aufgrund von Lesevorgängen aus dem Speicher 2,3 MB.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link Threads zuerst nach höchsten Verzögerung sortiert und Empfehlung zur Verbesserung der Leistung während dieser Aktivität finden Sie unter.

-   **Leert Speicher**

    Das folgende Problem wird die Summe der alle geleert, die zu Verzögerungen bei der die Aktivität zählen.

    **Problem-Beispiel**

    Aktivität Fast Start Resume Explorer Initialisierung verursacht eine Verzögerung 300 Millisekunden aufgrund von 4 leert in einen Speicher an.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen-Link finden Sie unter den Anruf Stapeln für jeden Thread, dass Ursachen werden auf den Datenträger geleert und den entsprechenden Code zu identifizieren, die auf die Aktivität Verzögerung beigetragen ein.

## <a name="a-href-idregistryhiveflushesaregistry-flushes"></a><a href="" id="registryhiveflushes"></a>Registrierung geleert


Registrierung leert auftreten, wenn Prozesse nach Abschluss eine Änderung der Registrierung explizit die **RegFlushKey** -Funktion verwenden. Bewertung haben festgestellt, dass die Registrierung Leert einen wichtigen Beitrag Benutzer empfundene Leistung Probleme werden können.

Sie müssen nicht bei jeder Änderung der Registrierung die **RegFlushKey** -Funktion verwenden. Diese Funktion wird am besten verwendet, nur, wenn Sie eine Änderung der Registrierung auf dem Datenträger sofort anwenden müssen.

Es gibt 2 Arten von Problemen mit der flush Registrierung:

-   Prozesse, die für das Leeren der Registrierungs ein oder mehrere Male identifiziert werden. Diese Probleme werden mit hoher Priorität kategorisiert.

    **Problem-Beispiel**

    Eine oder mehrere Prozesse leeren eine Registrierungsstruktur während des schneller Start Resume Post ein-/ausschalten.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link untersuchen jeder Thread der Prozesse, die dieses Verhalten verursacht. WPA stellt die relevante Funktion Call-Stapel, wo die Aktivität aufgetreten ist.

-   Prozesse, die leeren der Registrierungs während einer Aktivität und verursacht eine Verzögerung bei der Durchführung der Aktivität.

    **Problem-Beispiel**

    Prozess * &lt;X&gt; * Verzögerungen Aktivität schnellen Start anhalten anrufen Abonnenten Profile, das eine Registrierungsstruktur 405 Millisekunden leeren.

    **Empfehlung**

    Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link die Funktion Call-Stapel für jeden Thread-Prozessen zu analysieren.

## <a name="a-href-idtimeaccountingatime-accounting"></a><a href="" id="timeaccounting"></a>Zeit Buchhaltung


Bewertung Bericht in der Regel mehrere Probleme pro Aktivität. Zeit Buchhaltung gibt anzeigen, die die zusammengefasste Zeit, die mehrere Probleme, sowie ein Teil der Aktivität berücksichtigt werden, die nicht berücksichtigt werden durch die Probleme aus. Wenn eine Aktivität viele kurze Zeit Probleme umfasst, und sie sich nicht unterhalb der Schwellenwert für die Analyse, sind sie nicht als einzelne Probleme gemeldet. In diesem Design unterstützt die meisten impactful Probleme zu markieren, damit Sie Ihre Untersuchung darauf konzentrieren können.

**Schwellenwert für die Aktivität Dauer**

Diese Grenze ist die Zeit, die voraussichtlich die gesamte Aktivität in Anspruch nimmt. Zeit Buchhaltung Probleme melden die gemessene Dauer der die Aktivität als auch die Aktivität Dauer Schwellenwert festlegen, indem die Bewertung.

**Mindestschwellenwert Analyse**

Probleme werden gemeldet, wenn die Auswirkung beschriebenen größer als der Schwellenwert für die Analyse ist.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Geben Sie 1 ein:</strong></p>
<p>Die Dauer der Aktivität überschreitet den Schwellenwert für die Aktivität Dauer. Die Aktivität, hat auch Probleme, die den Schwellenwert für die Analyse überschreiten.</p></td>
<td><p><strong>Problem-Beispiel</strong></p>
<p>Zusammenfassung: Schnelles Herunterfahren Startvorgangs Example.exe dauert 6.5 Sekunden und überschreitet den Schwellenwert 2 Sekunden. Die Bewertung identifiziert andere Probleme, die diese Aktivität auswirkt. Diese anderen Probleme berücksichtigt werden vollständig für diese Aktivität Zeit.</p></td>
</tr>
<tr class="even">
<td><p><strong>Geben Sie 2:</strong></p>
<p>Die Dauer der Aktivität überschreitet den Schwellenwert für die Aktivität Dauer. Die Aktivität auch verfügt über eine gemischte Reihe von Problemen – einige, die größer als der Schwellenwert für die Analyse und andere Personen, die kleiner als der Schwellenwert für die Analyse.</p></td>
<td><p><strong>Problem-Beispiel</strong></p>
<p>Zusammenfassung: Fast zum Starten des Herunterfahrens Example.exe dauert 6.5 Sekunden und überschreitet den Schwellenwert 2.0 Sekunden. Die Bewertung identifiziert andere Probleme, die diese Aktivität auswirkt. Diese anderen Probleme, die für diese Aktivität 5,9 Sekunden berücksichtigt werden. Die verbleibenden 500 Millisekunden bestehen Probleme bei der Schwellenwert für die minimale Analyse von 150 Millisekunden nicht überschreiten.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Geben Sie 3:</strong></p>
<p>Die Dauer der Aktivität überschreitet den Schwellenwert für die Aktivität Dauer. Die Probleme, die diese Aktivität auswirkt kleiner als der Schwellenwert für die Analyse werden und werden daher nicht angezeigt.</p></td>
<td><p><strong>Problem-Beispiel</strong></p>
<p>Zusammenfassung: Fast zum Starten des Herunterfahrens Example.exe dauert 6.5 Sekunden und überschreitet den Schwellenwert 2.0 Sekunden. Die Bewertung identifiziert andere Probleme, die diese Aktivität auswirkt. Diese anderen Probleme, die diese Aktivität auswirkt überschreiten nicht Schwellenwert für die minimale Analyse von 200 Millisekunden, sodass sie weggelassen.</p></td>
</tr>
<tr class="even">
<td><p><strong>Geben Sie 4:</strong></p>
<p>Die Dauer der Aktivität überschreitet den Zeitraum an, wann Assessment Protokollierung aktiv war. Die Verzögerungen wurden jedoch in der Aktivität gefunden, Protokollierung aktiv war. Diese Verzögerungen wurden durch CPU oder Datenträger Konflikte verursacht.</p></td>
<td><p><strong>Problem-Beispiel</strong></p>
<p>Zusammenfassung: Die Dauer der schneller Start Resume Post ein-/ausschalten ist unbekannt, da diese Aktivität nach Bewertung Protokollierung enden abgeschlossen ist. 4 Sekunden dieser Aktivität sind während Assessment Protokollierung aktiv ist, aufgrund der CPU-Auslastung.</p></td>
</tr>
</tbody>
</table>

 

**Empfehlung**

Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link zum Anzeigen dieses Problem in Windows Performance Analyzer ein. Überprüfen Sie die Details der Aktivität Verhalten, das die Ursache des der Verzögerungen zu verstehen, wenn gemeldet. Führen Sie die folgenden Schritte zum Anzeigen dieser Probleme:

1.  Verwenden Sie die Filteroptionen, um alle Probleme im Zusammenhang mit der Aktivität in den Problemtitel zitiert anzuzeigen.

2.  Bei der Anzeige der der vollständigen Liste der Probleme wählen Sie Pluszeichen (+), und wählen Sie die **Aktivität** aus der Liste der Filter-Optionen.

3.  Geben Sie im Filterfeld **Problem Aktivität** den Namen der Aktivität. Wählen Sie aus der Liste der benannten Aktivitäten die bestimmte Aktivität aus. Erhalten Sie eine gefilterte Liste von Problemen im Zusammenhang mit diesem Problem Accounting Zusammenfassung.

Weitere Informationen zum Erkennen von Problemen finden Sie unter [Gruppieren, Filter und Suchproblemen](group-filter-and-search-issues.md).

## <a name="a-href-idmissingsymbolsamissing-symbols"></a><a href="" id="missingsymbols"></a>Fehlende Symbole


Einige Bewertung benötigen Zugriff auf Symbole. In einigen Fällen werden die Informationen in den Ergebnissen Assessment falsch oder unvollständig sind, wenn ein Symbolserver nicht verfügbar ist. In vielen Fällen erfüllen Internet Connectivity und Zugriff auf den Microsoft-Server öffentliche Symbol diese Abhängigkeit. In anderen Fällen können Sie einen privaten Symbolserver einrichten oder die Symbole auf dem lokalen Computer installieren.

Die Typen von Symbolen verwendet zählen:

-   **Kritische Symbole:** Wenn diese Symbole nicht verfügbar sind kann nicht die Bewertung vollständige Analyse der Daten abgeschlossen, die sie gesammelt werden. In diesem Fall enthält der problemtext bestimmte Modulnamen für die Module die während der Bewertung Analyse keine Symbole konfiguriert und verfügbar sind.

-   **Symbole für 3rd Party Komponenten:** Wenn diese Symbole nicht verfügbar sind, die Bewertung erfolgreich abgeschlossen wird, aber ihre Ergebnisse möglicherweise falsch oder unvollständig. Die Problemdetails generiert möglicherweise unvollständige oder falsche Informationen bei der Anzeige in Windows Performance Analyzer enthalten. Beispielsweise beim Betrachten des Abschnitts Problemdetails die Anruf Stapeln angezeigt möglicherweise fehlen Funktionsnamen für eine bestimmte Komponente.

-   **Kernel Symbole:** Die Bewertung Speicherbedarf wird Kernel Symbole für die Analyse verwendet. Wenn diese Symbole konfiguriert nicht findet, erstellt er ein Problem in den Ergebnissen, die die Abwesenheit von Symbolen erwähnt, nach dem Abschluss der Bewertung.

**Empfehlung**

Wichtige fehlende Symbole: Stellen Sie sicher, dass der Computer über Zugriff auf Microsoft öffentliche Symbolserver verfügt. Dieses Problem kann behoben werden, zeigen Sie auf den richtigen Symbole Speicherort oder durch die Symbole auf einem lokalen Laufwerk installieren.

Symbole für nicht-Microsoft-Komponenten fehlt: Diese fehlenden Symbole für eigene Komponenten oder für Benutzer im Besitz von einem anderen Partner könnte. Zusammenarbeit mit Ihren Partnern diese Drittanbieter-Symbole für die Komponente abrufen, die Symbole nicht angezeigt wird, und konfigurieren Sie den Pfad des richtigen Symbole auf dem Computer, bevor Sie die Bewertung erneut ausführen.

**Hinweis**  
Weitere Informationen zum Festlegen des richtigen Symbole Pfads finden Sie unter [Problembehandlung bei Windows Assessment Services](http://go.microsoft.com/fwlink/?LinkId=246155).

 

Freigabe von Komponenten Symbole Partner im Ökosystem wird eine bessere Zusammenarbeit durch eine zuverlässige und effiziente Bug Ursachenanalyse und Analysen Prozess sichergestellt. Es wird empfohlen, dass Partner dieser collaborative Vertrauensstellungen, um sicherzustellen definieren, dass Sie die Ressourcen verfügen, die Sie die Ursache des der bekannten Probleme auf Ihre Systemkomponente finden müssen.

## <a name="a-href-iddpcisradpcs-and-isrs"></a><a href="" id="dpcisr"></a>DPCs und ISRs


Langer zurückgestellt Prozeduraufrufe (DPCs) und unterbrechen Service Routinen (ISRs) kann stellen Verzögerungen, die die Dauer einer Aktivität zu erweitern und diese Wartezeit von Benutzern als ein Leistungsproblem wahrgenommen werden konnte.

DPC (und ISR) Probleme erfordern in der Regel eine tiefere Analyse von Experten, die mit der Arbeit im Zusammenhang mit der DPC (oder ISR) vertraut. Die detaillierte Analyse für dieses Problem variiert je nach den Typ des DPC verursacht die Verzögerung oder eine Ressource verwenden.

**DPCs, die Verzögerung für eine Aktivität**

Ein Thread wartet Arbeit abgeschlossen. Nach dem Abschluss der Arbeit bereitet die DPC dieses wartenden Threads.

Die Thread-ID der wartenden Threads und seine kumulierte Wartezeit in der Problemdetails angezeigt werden. Erweitern Sie die Problemdetails anzeigen des Stapels Wait dieses Threads.

Komplexer Aktivitäten ist es-Parametern ein Thread in einem anderen Thread zu warten, das in einem anderen Thread, die für die Arbeit wartet abgeschlossen wartet. Eine DPC mit Thread, der Planer oder einen anderen Mechanismus bereitet die neuesten wartenden Threads. Diese neuesten wartenden Threads noch einmal ausgeführt, und bereitet wartenden Threads. Der Prozess wird mit den einzelnen wartenden Threads wiederholt, bis der früheste wartende Thread Scanthreads ist und erneut ausgeführt.

Die Problemdetails werden diese Abfolge von Steuerung in chronologischer Reihenfolge beschrieben. Beispiel:

Der Prozess csrss.exe (600) wartet 374 Millisekunden 712 Thread

Der Prozess explorer.exe (1836) wartet 374 Millisekunden 2724 Thread

Thread 4748 des Prozesses explorer.exe (1836) ausgesetzt 373 Millisekunden

Timer DPC bereitet Thread 4748

Thread 4748 bereitet wartenden Threads 2724

Thread 2724 bereitet wartenden Threads 712

Während einer Aktivität kann die gleichen Steuerung oft wiederholen. Die Wartezeiten sind kumulativ.

Wählen Sie einen Satz an, der beschreibt ein wartenden Threads, um einen Stapel anzuzeigen, der die Anzeige für wartende-Funktion enthält. Wählen Sie einen Satz an, der einen Thread Vorbereitung einer anderen Thread, um einen Stapel anzeigen, der die Funktion readying zeigt beschreibt.

Der Anzeige für wartende Stapel von im innersten Thread, Thread 4748 im obigen Beispiel bietet in der Regel sollten über die Quelle für die Verzögerung. Vor der Anzeige für wartende-Funktion zusammen mit der Informationen, die den Stapel folgt Stack-Frames vorsehen Aufschluss über das Problem weiter.

DPC-bezogene Verzögerungen können in diesen drei Typen klassifiziert werden, wie in diesen Beispielen gezeigt.

**Beispiele für Problem**

Netzwerk DPCs: Netzwerk verwenden der Aktivität schneller Start insgesamt wiederaufnehmen, indem Sie 4.0 Sekunden Verzögerungen

Timer DPCs: Aktivität Fast zum Starten des Herunterfahrens Example.exe wird durch 5.3 Sekunden verzögert.

Schneller Start Aktivität anhalten Gerät LEISTE führt zu eine Sekunde 2,6 Verzögerung aufgrund eines wartenden Threads. DPC Example.sys bereitet diese wartenden Threads.

**DPCs oder ISRs an, die auftreten, während eine Aktivität**

Dieser Art von Problem hervorgehoben langen ISRs oder DPCs, die sich auf die Leistung des Szenarios auswirken können. Die Probleme führen Sie diese Aktivität ISR/DPC Verzögerung Dauer nicht gebunden.

Die Problemdetails Listen jeder Thread der ISR/DPC Anwendungsmodellen. Die Liste ist ungefähr Unterbrechung Zeit Absteigend. Erweitern eines Threads in der Liste um einen Stapel anzuzeigen, der die Threadaktivität ist ein Näherungswert, die Vorrang vor den ISR/DPC hat.

**Problem-Beispiel**

DPC überschreitet den Schwellenwert 1.0 Millisekunden 5 Mal während der Lebensdauer von Medien-Modul. Führen Sie die 5 Instanzen von diesem DPC für insgesamt 3.7 Sekunden

**Hinweis**  
Die Informationen in den Anruf Stapeln ist eine statistische Darstellung der betreffenden Aktivität (gemessen wird einmal für jede Millisekunde), und seine Genauigkeit Stichproben durch die Bewertung abhängig ist.

 

## <a name="a-href-idsummaryissuesasummary-issues"></a><a href="" id="summaryissues"></a>Zusammenfassung der Probleme


Zusammenfassung der Probleme enthalten eine Übersicht über die Probleme durch die Bewertung identifiziert, die einer bestimmten Leistungsverhalten veranschaulichen, und die größere Auswirkung dieser auf dem System visualisieren. Hier sind die verschiedenen Typen von Zusammenfassung Probleme, die in Suchergebnissen Assessment feature konnte.

**Zusammenfassung der Aktivität Datenträger Bilanz**

Datenträger-Bilanz wird der kombinierte Beitrag aller Prozesse, das Problem Speicher e/a in Form von Storage Lesevorgänge, schreibt und leert während einer Aktivität. Diese Zusammenfassung enthält die zusätzlichen Einblick in die Bilanz Datenträger außerhalb der Speicher Verwendungsprobleme, die bereits in den Ergebnissen Assessment gemeldet.

Das Problem Details in WPA enthalten Dateiinformationen Bild und Empfehlungen zur Verbesserung der Leistung des Szenarios. Die Analyse enthält außerdem die Liste der Prozesse, die auf den Datenträger Speicherbedarf, in absteigender Reihenfolge der Auswirkungen beitragen.

**Beispiele für Problem**

Zusammenfassung: Schnellen Start insgesamt Lebenslauf Probleme 275MB Lese- und Schreibvorgänge und leert 82 Zeiten in einen Speicher

**Hinweis**  
Wenn Probleme nach **Kategorie** auf der Seite **Ergebnisansicht** gruppiert sind, wird dieses Problem Zusammenfassung über seine Verwandte Probleme unter der Gruppe **Speicher verwenden** angezeigt.

 

**Prozessor mit Zusammenfassung**

Das Prozessor verwenden Zusammenfassung Problem aggregiert ähnliche Probleme, die bereits von der Bewertung zusammen mit weniger impactful Probleme während der Aktivität identifiziert. Diese Zusammenfassung enthält eine breitere Perspektive der alle zugehörigen Prozessor Verwendungsprobleme.

Das Problem Zusammenfassung enthält Details pro Prozess in absteigender Reihenfolge der Auswirkungen. Für jeden Vorgang zeigt das Problem eine Funktionsaufrufliste, die Aktivität aus allen Threads in den Prozess und die CPU und der Dateiname der Image-Informationen kombiniert. Die einzelnen Probleme enthalten, wenn vorhanden, ausführlichere Funktion Call-Stapel für jeden entsprechenden Thread.

**Beispiele für Problem**

Zusammenfassung: Verwenden der Prozesse 26.9 Sekunden des CPU-Zeit beim schnellen Start insgesamt fortsetzen

**Hinweis**  
Wenn Probleme nach **Kategorie** auf der Seite **Ergebnisansicht** gruppiert sind, wird dieses Problem Zusammenfassung über seine Verwandte Probleme unter der Gruppe **Der Prozessorverwendung** angezeigt.

 

**Prozessor und Festplatte Konflikte Zusammenfassung**

Dieses Problem wird auf die Aktivität aufgrund von Konflikten für Prozessor- und zusammengefasst. Konkurriert Aktivität stört Aufgaben, die für die Durchführung des Szenarios wichtig sind. Die Problemdetails aufgelistet, die verschiedenen untergeordneten Aktivitäten beteiligt sind, in absteigender Reihenfolge die Höhe der Konflikte wird.

Andere Informationen wie Funktion Call-Stapel und Dateiinformationen pro Thread steht in jeder der einzelnen Probleme durch die Bewertung gemeldet.

**Beispiele für Problem**

Zusammenfassung: Schneller Start insgesamt anhalten akzeptiert 29,5 Sekunden. CPU-Auslastung liegen 300 Millisekunden in dieser Zeit.

Wenn Probleme nach **Kategorie** auf der Seite **Ergebnisansicht** gruppiert sind, wird dieses Problem Zusammenfassung über seine Verwandte Probleme unter der Gruppe **Prozessor Verzögerungen** angezeigt.

**Empfehlung**

Zusammenfassung der Probleme helfen Ihrer Untersuchung die am häufigsten impactful Fragen zu konzentrieren. Lesen die Zusammenfassung Probleme häufig selbst bietet einen Einblick in die größere Auswirkung dieser Probleme zusammengestellt.

Wenn Sie die Vorteile der Zusammenfassung Probleme erhalten möchten, können Sie die Liste der Probleme in der Windows-Konsole zur Bewertung mithilfe einer dieser beiden Kriterien gruppieren.

-   **Kategorie**. Dies ist die Standardeinstellung und Ansicht für Zusammenfassung Probleme, wobei sie zusammen mit identischen/vergleichbare Probleme eines bestimmten Typs gruppiert werden empfohlen.

-   **Testfall**. In dieser Ansicht werden die Zusammenfassung Problem zusammen mit der Teilmenge von Problemen gruppiert, die für eine bestimmte Aktivität oder Testfall gelten.

**Warnung**  
Die Informationen in den Anruf Stapeln ist eine statistische Darstellung der betreffenden Aktivität (gemessen wird einmal für jede Millisekunde), und seine Genauigkeit Stichproben durch die Bewertung abhängig ist.

 

## <a name="a-href-idloggingaassessment-logging"></a><a href="" id="logging"></a>Assessment-Protokollierung


Bewertung hängen Event Tracing for Windows (ETW) Protokollierung zum Sammeln von Daten für die Analyse. Diese Protokollierung verwendet Systemressourcen. Dieses Problemkategorie Benutzerkonten für die Speicher-Aktivität, die auftritt, während die Bewertung ausgeführt wird.

**Problem-Beispiel**

Assessment meldet 39 MB Speicher während des schneller Start Resume Post ein-/ausschalten.

**Empfehlung**

Wählen Sie im Bereich **Weitere Analyse** des Problems den WPA eingehenderen Analysen Link hier finden Sie Informationen zur Speicherung von Protokolldateien schreibt.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Konsole](windows-assessment-console.md)

[Bewertung](assessments.md)

 

 







