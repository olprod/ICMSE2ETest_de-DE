---
title: "Ergebnisse für die Bewertung ein-/ausschalten"
description: "Ergebnisse für die Bewertung ein-/ausschalten"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7aa9fcbc-4019-4be0-829a-d50eadc6ca02
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: bd44cde5ff0f947b5425c6998ff34d6af6d9124e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-onoff-assessments"></a>Ergebnisse für die Bewertung ein-/ausschalten


In diesem Thema können Sie die Ergebnisse, die mit der On/Off Bewertungsfragen (Start-Leistung (Fast Start), Start-Leistung (vollständige Boot), dem Standbymodus Leistung und Leistung Ruhezustand) interpretiert werden. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben mehrere häufige Probleme, die sich negativ auf die Endbenutzer Erfahrung beim Herunterfahren und Starten eines Computers auswirken.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#fs-metrics)

-   [Probleme](#fs-issues)

-   [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis)

Weitere Informationen zum Übergang weiter Bewertung finden Sie unter [Weiter Übergang Leistung](onoff-transition-performance.md).

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

 

## <a name="a-href-idfs-metricsametrics"></a><a href="" id="fs-metrics"></a>Metriken


Dieser Abschnitt beschreibt die Taste bewirkt, der On/Off Bewertungsfragen ist, allgemeine Metriken schlechte Ergebnisse für diese Metriken und allgemeine Behebung für Probleme im Zusammenhang mit diesen Metriken dass. In diesem Abschnitt können Sie die Benutzergruppe zu identifizieren, für die die Metrik am häufigsten anwendbar ist.

In diesem Abschnitt:

-   [Herunterfahren Dauer & Dauer anhalten](#oo-shutdown-duration)

-   [Benutzer beim Herunterfahren Sitzungsdauer](#oo-user-session-shutdown-duration)

-   [Herunterfahren Prozesse Dauer](#oo-shutdown-processes)

-   [Winlogon Dauer & Winlogon Benachrichtigungen Dauer anhalten](#oo-winlogon-suspend)

-   [Prozesse Dauer anhalten](#oo-suspend-processes-duration)

-   [Services Dauer anhalten](#oo-suspend-services-duration)

-   [Vorbereiten der SuperFetch Arbeitsspeicher Dauer](#oo-superfetch-prepare-memory-duration)

-   [Dauer der Abfrage-Geräte](#oo-query-devices-duration)

-   [Leeren Speicher Volumes Dauer](#oo-flush-storage-volumes-duration)

-   [Geräte Dauer anhalten](#oo-suspend-devices-duration)

-   [Dauer der Hiberfile schreiben](#oo-hiberfile-write-duration)

-   [Dauer der BIOS-Initialisierung](#oo-bios-initialization-duration)

-   [Insgesamt Boot \[ausschließen BIOS\] Dauer & insgesamt Resume \[ausschließen BIOS\] Dauer](#oo-total-boot)

-   [Main Pfad Boot Dauer & Hauptfenster Pfad Resume Dauer](#oo-main-path)

-   [Start-Manager](#oo-boot-manager)

-   [Dauer der Hiberfile lesen](#oo-hiberfile-read-duration)

-   [Dauer der Resume-Geräte](#oo-resume-devices-duration)

-   [Winlogon Resume Dauer](#oo-winlogon-resume-duration)

-   [Explorer Initialisierung Dauer](#oo-explorer-initialization-duration)

-   [On/Off Dauer buchen](#oo-post-on-off-duration)

**Hinweis**  
Wenn Sie die Einstellung Diagnostic Minifilter-Modus aktivieren aktiviert haben, werden die Bewertungsergebnisse Minifilter Metriken enthalten. Informationen zu Minifilter Metriken und Ergebnisse finden Sie unter [Minifilter Diagnosen](minifilter-diagnostics.md).

 

### <a name="a-href-idoo-shutdown-durationashutdown-duration-suspend-duration"></a><a href="" id="oo-shutdown-duration"></a>Herunterfahren Dauer & Dauer anhalten

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, die der Computer Herunterfahren aufwendet oder Vorgänge anhalten. In der folgenden Tabelle werden die Metrik für jedes Assessment beschrieben:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Bewertung</th>
<th>Metrische Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Zur Bewertung Boot-Leistung (schnellen Start)</p></td>
<td><p>Diese Metrik werden die Zeit bis zum Ende des Schreibens der Hiberfile auf Datenträger und der Übergang zu einem niedrigeren Power-Status (S4) vom Anfang einer Phase beim Herunterfahren erfasst.</p></td>
</tr>
<tr class="even">
<td><p>Boot Performance (vollständige Boot)-Bewertung</p></td>
<td><p>Diese Metrik erfasst die Zeit ab dem Anfang einer Phase beim Herunterfahren mit der Umstellung auf einem funktionsfähigen Status.</p></td>
</tr>
<tr class="odd">
<td><p>Standby-Performance-Bewertung</p></td>
<td><p>Diese Metrik erfasst die Zeit ab dem Anfang einer Phase Suspend mit der Umstellung auf einen Zustand mit niedrigerer (S3).</p></td>
</tr>
<tr class="even">
<td><p>Ruhezustand Performance-Bewertung</p></td>
<td><p>Diese Metrik erfasst die Zeit aus Ruhezustand an das Ende der Hiberfile auf Datenträger und den Übergang zu einer Zustand mit niedrigerer (S4) schreiben.</p></td>
</tr>
</tbody>
</table>

 

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert ist, wird eine Liste der Herunterfahren oder angehalten werden soll, wird der untergeordnete Phasen angezeigt.

**Hinweis**  
Die Dauer der untergeordneten Phasen füge nicht unbedingt die Gesamtdauer in einrichten.

 

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik ist eine allgemeine Metrik für das System Herunterfahren/angehalten werden soll. Es kann durch keine Softwarekomponenten beeinflusst werden, die auf den Pfad zum Herunterfahren/Anhalten ausgeführt werden.

**Analyse und Schritte zur Wiederherstellung**

Erweitern Sie diese Metrik, um die untergeordneten Metriken anzuzeigen, die auf einzelnen untergeordneten Phasen des Herunterfahren/anhalten Bereitstellen weiterer Informationen ein. Untersuchen Sie Probleme bei der potenziellen Verzögerung Mitwirkende suchen und einzelnen untergeordneten Phase Metriken.

### <a name="a-href-idoo-user-session-shutdown-durationauser-session-shutdown-duration"></a><a href="" id="oo-user-session-shutdown-duration"></a>Benutzer beim Herunterfahren Sitzungsdauer

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

Diese Metrik misst die Zeit, die der Computer benötigt die Sitzung des Benutzers beendet. Diese Phase umfasst Benutzersitzungsdaten Prozesse heruntergefahren, der Benutzer abgemeldet und benachrichtigen Abonnenten auf Winlogon-Benachrichtigungen. Wenn die Metrik erweitert ist, wird eine Liste der Herunterfahren oder angehalten werden soll, wird der untergeordnete Phasen angezeigt.

**Hinweis**  
Die Dauer der untergeordneten Phasen füge nicht unbedingt die Gesamtdauer in einrichten.

 

Diese Metrik ist eine allgemeine Metrik für das Herunterfahren des Systems. Sie können von keine Softwarekomponenten betroffen sein, die auf den Pfad zum Herunterfahren ausgeführt werden.

**Analyse und Schritte zur Wiederherstellung**

Erweitern Sie diese Metrik, um die untergeordneten Metriken angezeigt, die auf einzelnen untergeordneten Phasen des Herunterfahrens mehr Informationen bereitzustellen. Untersuchen Sie Probleme bei der potenziellen Verzögerung Mitwirkende suchen und einzelnen untergeordneten Phase Metriken.

### <a name="a-href-idoo-shutdown-processesashutdown-processes-duration"></a><a href="" id="oo-shutdown-processes"></a>Herunterfahren Prozesse Dauer

**Am besten:** Anwendungsentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

Wenn die Bewertung Herunterfahren die Benutzer der Sitzung initiiert hat, wird jeder Benutzeroberflächen-Thread in jeder Anwendung Graphical User Interface (GUI) eine WM gesendet\_QUERYENDSESSION Nachricht. Nachdem Windows eine Antwort auf die WM erhält\_QUERYENDSESSION Nachricht, Windows sendet die WM\_ENDSESSION auf dieselben Threads. Wenn nach 5 Sekunden jeder Anwendung nicht auf diese Benachrichtigungen geantwortet hat, wird Windows die Anwendung beendet. Jeder Anwendung verzögern kann Herunterfahren des Systems, indem Sie auf die Nachrichten nicht umgehend reagieren.

**Hinweis**  
Wenn ein Benutzer das Herunterfahren initiiert, zeigt ein Dialogfeld für Benutzer nach Ablauf des Timeouts. Dieses Dialogfeld zeigt Informationen über die Anwendung, die das Herunterfahren blockiert, und ermöglicht es dem Benutzer zu **erzwingen** oder auf **Abbrechen,** das beim Herunterfahren.

 

Diese Metrik misst die Zeit, die der Computer verbringt allen Prozessen in der die Sitzung beendet.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht einer Reihe von untergeordneten Metriken, die Zeiten zu messen, die jeder einzelne Vorgang zur Beantwortung Benachrichtigungen zum Herunterfahren ausgeführt wurden, angezeigt. Die Spalten enthalten die folgende Informationen:

-   Eine PID durch Iteration in der Spalte Details. In der Standardansicht möglicherweise dieser Spalte den Wert enthalten "Verschiedene", da PID auf Iterationen aggregiert werden können. Erweitern Sie Iterationen, um einzelne PID finden Sie unter.

-   Die Zeit, die in diesem bestimmten Prozess während dieser Phase ausgeführt wurden.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik erfasst die kumulierte Zeit aller aktiven Prozesse, die UI-Threads zur Beantwortung Benachrichtigung zum Herunterfahren. Diese Metrik kann von einem einzelnen Prozess betroffen sein, die zusätzlich zu der kumulierte Zeit aller Prozess Antworten zu lange dauert.

Jeder Vorgang, bei dem einen Benutzeroberflächen-Thread wurde Herunterfahren des Systems verzögern kann, durch die Antwort auf die WM verzögern\_QUERYENDSESSION Nachricht oder WM\_ENDSESSION-Nachricht.

**Hinweis**  
Um diese Metrik auswirken, muss ein Prozess ausgeführt werden. Da dieses Assessment Neustarts, bevor Daten zur Analyse gesammelt, sind die ausgeführte Prozesse fast ausschließlich über Start Anwendungen oder geplante Tasks.

 

**Analyse und Schritte zur Wiederherstellung**

Sie können Prozesse identifizieren, die am häufigsten erheblich diese Metrik mithilfe der Technik [Suchen Sie nach der größten Mitwirkende](#fs-issues) auswirkt.

Entfernen Sie wenn möglich, Applications aus Startpfad. Da die Bewertung Neustart bevor Maßangaben durchgeführt werden nur Anwendungen, die beim Herunterfahren ausgeführt werden die Anwendungen, die beim Start begonnen hat. Als bewährte Methode sollte Autostart-Programme auf ein Minimum beschränkt werden. Wenn eine Anwendung unessential Verzögerungen verursacht, sollten Sie sie aus der Liste Start Programme entfernen.

Suchen Sie die möglichen Gründe, Antworten auf WM\_QUERYENDSESSION Nachricht oder WM\_ENDSESSION verzögert werden kann, und beheben und die zugrunde liegenden Probleme zu beheben. Eine Liste der allgemeine bewährte Methoden finden Sie unter [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis) .

**Weitere Informationen**

[MSDN: WM\_QUERYENDSESSION Nachricht](http://go.microsoft.com/fwlink/?LinkId=247501)

[MSDN: WM\_ENDSESSION-Nachricht](http://go.microsoft.com/fwlink/?LinkId=247502)

### <a name="a-href-idoo-winlogon-suspendawinlogon-suspend-duration-winlogon-notifications-duration"></a><a href="" id="oo-winlogon-suspend"></a>Winlogon Dauer & Winlogon Benachrichtigungen Dauer anhalten

**Am besten:** Winlogon Abonnenten Entwickler, Richtlinie Skript Gruppenbesitzer, Systemadministratoren

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Standby-Leistung

-   Ruhezustand Leistung

Dieser Metrik Maßnahmen aufgewendet wurde die Zeitspanne für die vom Winlogon, einschließlich der Zeit Abonnenten Benachrichtigungen/Rückrufe ausführen.

Für das Szenario Start-Leistung (Fast Start) gilt die Metrik **Winlogon Benachrichtigungen** in Windows Assessment-Konsole für die kumulative Zeitspanne für die Verarbeitung aller Winlogon Abonnenten Benachrichtigungen und Rückrufen. Jedoch um Kontext in die Zeitachse Windows® Performance Analyzer (WPA) bereitzustellen, die **Winlogon Benachrichtigungen** Aktivität beginnt mit dem ersten Abonnenten Benachrichtigung/Rückruf, und endet mit dem letzten. Die Zeitspanne für die Verarbeitung jeder Benachrichtigung wird von einzelnen untergeordneten Aktivitäten dargestellt.

Start-Leistung (Fast Start) ist die einzige Bewertung, die zusätzliche untergeordnete Metriken für diese Metrik bereitstellt. Während der anhalten registriert Winlogon Probleme synchrone Abonnenten Benachrichtigungen an Abonnenten für die folgenden vier Benachrichtigungstypen:

-   Sitzung beenden

-   End-Shell

-   Abmelden

-   Erstellen der Sitzung

Wenn die Metrik erweitert wird, werden diese vier Benachrichtigungstypen als untergeordnete Metriken dargestellt. Jeder dieser Typen verfügt über eine Liste von Abonnenten (beispielsweise Profile und GPClient) als zusätzliche untergeordnete Metriken und jedem Abonnenten bestimmten Instanzen von **Connect an Abonnenten** und **Aufrufen von Abonnenten** für diese Abonnenten aufgeführt.

In jedem Szenario können Winlogon Abonnenten Herunterfahren Standby verzögern durch braucht zu lange zum Verarbeiten diese Benachrichtigungen. Beispielsweise muss ein Profildiensts (Profile) im Benutzerprofil synchronisieren, wenn das Feature **Roaming (Remote) Profile** auf dem Computer aktiviert ist. Als weiteres Beispiel kann ein Gruppenrichtlinien-Client (GPClient) durch eine Richtlinie System oder einer Domäne für bestimmte Aufgaben bei der Abmeldung Benutzer konfiguriert werden. Diese Aufgaben werden in der Regel durch ein System oder Domänenadministrator an konfiguriert.

**Typische Schlüsselfaktoren Faktoren**

Wenn Sie diese Metrik untersuchen, sollten Sie den Abonnenten Winlogon konzentrieren.

**Analyse und Schritte zur Wiederherstellung**

Überprüfen Sie wie oft der einzelnen Abonnenten Vorgänge. Bestimmte Probleme werden in der Regel für Abonnenten generiert, die längere dauern. Öffnen Sie WPA, um das Zeitintervall eines Abonnenten für mehr Einblick darin enthalten. Beispielsweise wenn Gespräch Abonnenten GPClient 10 Sekunden dauert, kann eine Prüfung der Periode in WPA offen legen, dass ein bestimmte benutzerdefiniertes Skript 9 Sekunden lang nicht genügend 10 ausgeführt wird. Dies zeigt an, dass das Skript stark mögliche Ursache der die Verzögerung ist.

**Weitere Informationen**

[MSDN: Winlogon Benachrichtigungsereignisse](http://go.microsoft.com/fwlink/?LinkId=247505)

### <a name="a-href-idoo-suspend-processes-durationasuspend-processes-duration"></a><a href="" id="oo-suspend-processes-duration"></a>Prozesse Dauer anhalten

**Am besten:** Anwendungsentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, der Computer die bevorstehende Power Zustand Änderung benachrichtigen über Prozesse zum.

Während dieser Phase sendet der Client/Server-Laufzeit Server Subsystem (Csrss.exe) WM\_POWERBROADCAST Fenster-Nachrichten zusammen mit den Ereignistyp der PBT\_APMSUSPEND zu jeder Anwendung, die ein Fenster besitzt. Das System möglicherweise auch aus der Monitor Herunterfahren.

Diese Aktivität kann im Diagramm WPA **Aktivitäten** als einem großen Abstand zwischen aufeinander folgenden Prozesse betrachtet werden, die angehalten. Eine Sekunde oder mehr Ausschalten der Monitor erwartet. Dies ist eine erforderliche Phase beim Anhalten/beenden nach unten, und es sollte nicht berücksichtigt werden einen Leistungsengpass dieser Metrik.

Sehen Sie sich das Diagramm **CPU-Auslastung (abgetastete)** während dieser Zeit CPU-Auslastung in dem csrss.exe-Prozess auf dem folgenden Stapel angezeigt:

``` syntax
[Root] (csrss.exe) 
winsrv.dll!RegisterForDeviceBroadcastNotifications 
|- winsrv.dll!ZwUserCallNoParam 
|    win32k.sys!xxxUserPowerStateCalloutWorker 
|    |- win32k.sys!PowerOffMonitor 
|    |    |- win32k.sys!FadeDesktop 
|    |    |- win32k.sys!DrvSetMonitorPowerState 
|    |    |- win32k.sys!UpdateDisplayState 
|    |    |- win32k.sys!DwmSyncClearSwapChain 
|    |    |- win32k.sys!RestoreGammaRamp
```

Lücken in **Prozesse anhalten** aufgrund von CPU-Auslastung auf anderen Stapel oder Verzögerungen ohne CPU-Auslastung auf dem aktuellen Stapel können Bereiche weiter untersuchen vorschlagen.

Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht der Phase dargestellt, mit einem Satz von untergeordneten Metriken, die die Zeiten, die jeder Prozess ausgeführt wurden messen, reagieren, um Benachrichtigungen anzuhalten. Die Spalten enthalten die folgende Informationen:

-   Eine PID durch Iteration in der Spalte **Details** . In der Standardansicht möglicherweise dieser Spalte den Wert enthalten "Verschiedene", da PID auf Iterationen aggregiert werden können. Erweitern Sie Iterationen, um einzelne PID finden Sie unter.

-   Die Zeit, die in diesem bestimmten Prozess während dieser Phase ausgeführt wurden.

**Hinweis**  
Wenn eine Anwendung mehrere Fenster verfügt, kann die gleiche Weise mehr als eine Benachrichtigung.

 

**Typische Schlüsselfaktoren Faktoren**

Jede Anwendung hat die Möglichkeit, Verzögerung Herunterfahren von verzögert die Antwort auf die WM\_POWERBROADCAST Nachricht mit PBT\_APMSUSPEND Ereignistyp. Da diese Metrik die kumulierte Zeit erfasst, die alle Windows GUI-Prozessen durchführen wird, um auf die Benachrichtigung Suspend reagieren, kann diese Metrik von einem einzelnen Prozess betroffen sein, die zusätzlich zu einer kumulierte Zeit aller Prozess Antworten zu lange dauert. Beachten Sie, dass der Prozess ausgeführt werden muss, um diese Metrik auswirken. Da die Start-Leistung (Fast Start) Bewertung Neustarts, bevor Daten zur Analyse gesammelt, stammen diese Prozesse fast ausschließlich zum Starten des Anwendungen oder geplante Tasks.

**Analyse und Schritte zur Wiederherstellung**

Identifizieren der Prozesse, die diese Metrik die meisten erheblich beeinträchtigen. Erweitern Sie im Windows-Assessment-Konsole die Metrik **Prozesse Dauer anhalten** , um die Details für diese Phase zu erhalten. Sortieren Sie in der Liste **Vorgang** in dieser Phase die **Dauer** in absteigender Reihenfolge zu, und suchen Sie nach der größten Autoren.

Entfernen Sie nach Möglichkeit Applications aus Startpfad. Als bewährte Methode sollte Autostart-Programme auf ein Minimum beschränkt werden. Wenn eine Anwendung unessential Verzögerungen verursacht, sollten Sie aus der Liste Start Programme entfernt wird.

Problembehandlung und Beheben von Problemen mit d. erheblich Auswirkung Startpfad erfordert umfassende Analyse der Anwendung verzögert. Eine Liste der allgemeine bewährte Methoden finden Sie unter [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis) .

**Weitere Informationen**

[MSDN: PBT\_APMSUSPEND-Ereignis](http://go.microsoft.com/fwlink/?LinkId=247503)

### <a name="a-href-idoo-suspend-services-durationasuspend-services-duration"></a><a href="" id="oo-suspend-services-duration"></a>Services Dauer anhalten

**Am besten:** Windows-Dienst-Entwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, der Computer die bevorstehende Power Zustand Änderung benachrichtigen über Services zum. Alle Dienste, die zum Empfangen von Power Management Ereignisse registrieren (DIENST\_ANNEHMEN\_FEHLERS) empfangen Benachrichtigungen anhalten. Da seriell diese Benachrichtigungen gesendet werden, trägt Verzögerungen in einem Dienst direkt zur Gesamtdauer Herunterfahren/angehalten werden soll. Eine zweite 30 Timeout wird (für jeden Dienst einzeln) erzwungen, um diese Benachrichtigung zu verarbeiten; nach diesem Timeout wird verschoben das System zur nächsten Phase. Da für diese Benachrichtigung registrieren optional ist, ist keine bestimmte Aktion vom Dienst vom Betriebssystem erforderlich.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine Liste der einzelnen Dienste und deren entsprechende Dauer eine ausführlichere Ansicht der Phase angezeigt.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik erfasst die kumulierte Zeit, die alle Dienste zum Reagieren auf eine Power-Abfrage ausführen. Diese Metrik kann von einem einzelnen Prozess betroffen sein, die zusätzlich zu der kumulierte Zeit aller Prozess Antworten zu lange dauert.

Die meisten Dienste sind zur erhebliche arbeiten als Reaktion auf dem Standbymodus und Ruhezustand Power Benachrichtigungen nicht erforderlich. Im Hinblick auf einen Dienst ähnelt schneller Start Ruhezustand.

**Analyse und Schritte zur Wiederherstellung**

Einen Dienst, der diese Metrik erheblich beeinträchtigt zu identifizieren. Längere Verzögerungen bei der Dienst Antworten zur Folge im allgemeinen Problemen, die für einen bestimmten Dienst spezifisch sind. Wenn eine solche ein Problem generiert wird, können Sie den Link in der Ausgabe zu erweiterten Problem ausführliche Informationen finden folgen. Wenn ein Problem nicht generiert wird, ist die nachfolgende Analyse in WPA erforderlich. Diese zusätzliche Analyse ist nicht Gegenstand dieses Dokuments. Weitere Informationen über allgemeine bewährte Methoden finden Sie unter [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis).

**Weitere Informationen**

[MSDN: OnNow/ACPI-Unterstützung](http://go.microsoft.com/fwlink/?LinkId=247504)

### <a name="a-href-idoo-superfetch-prepare-memory-durationasuperfetch-prepare-memory-duration"></a><a href="" id="oo-superfetch-prepare-memory-duration"></a>Vorbereiten der SuperFetch Arbeitsspeicher Dauer

**Am besten:** Anwendungsentwickler, Windows-Dienst-Entwickler

**Relevante Bewertung**

1.  Start-Leistung (Fast Start)

2.  Standby-Leistung

3.  Ruhezustand Leistung

Diese Metrik misst die Zeit, der Windows Superfetch-Dienst zum Vorbereiten der Zustand des Arbeitsspeichers für die nachfolgende Boot/fortsetzen. SuperFetch vor Abrufe Daten, die häufig zugegriffen werden, klicken Sie auf Start, und speichert sie entweder im Hauptspeicher (Standby Leistung) oder Hiberfile (für Start-Leistung (Fast Start) und Performance Ruhezustand) zur Vermeidung von übermäßig viele greift auf auf fortsetzen. Dieses Feature beschleunigt den Vorgang fortsetzen.

**Typische Schlüsselfaktoren Faktoren**

Während dieser Phase greift auf der Superfetch-Dienst zu Daten, die während des Starts gelesen werden. Die Dauer dieser Phase wird durch die Menge der Daten, die beim Start von Autostart-Programme, Dienste, Anmeldeinformationsanbieter und usw. gelesen werden muss, direkt beeinflusst.

**Analyse und Schritte zur Wiederherstellung**

Diese Phase erfordert Erweiterte Analysen, die in diesem Dokument nicht enthalten ist.

### <a name="a-href-idoo-query-devices-durationaquery-devices-duration"></a><a href="" id="oo-query-devices-duration"></a>Dauer der Abfrage-Geräte

**Am besten:** Treiberentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Während der Phase der Herunterfahren Standby, wird jedem Gerätetreiber Potenzierung IRP, die ein IRP wurde gesendet\_MN\_ABFRAGE\_POWER minor-Code und einen Power-Status (S4 für Boot-Leistung (Fast Start) / Ruhezustand Leistung, S3 für Standby Leistung). Diese Metrik misst die Dauer aller Treiber, die von der Abfrage Power IRP verarbeitet.

Jeden Treiber verzögern kann Herunterfahren des Systems, indem die IRP nicht umgehend behandeln.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht der Phase mit einer Liste von Geräten und deren entsprechende Dauer dargestellt.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik erfasst die kumulierte Zeit, die alle Treiber ergreifen Power Abfragen beantworten. Diese Metrik kann von einem einzelnen Treiber betroffen sein, die zusätzlich die kumulierte Zeit aller Treiber Antworten zu reagieren zu lange dauert.

**Analyse und Schritte zur Wiederherstellung**

Sie können einen Treiber oder Treibern, die diese Metrik erheblich beeinträchtigen, verfolgen die untergeordneten Metriken identifizieren. Längere Verzögerungen bei der Treiber Antwort Dauer in der Regel erstellen, Probleme, die für ein gegebenes spezifisch sind. Wenn solche ein Problem generiert wird, führen Sie den Link in der Ausgabe erweiterte Problemdetails angezeigt. Wenn ein Problem nicht generiert wird, ist die nachfolgende Analyse in WPA erforderlich. Dies ist nicht Gegenstand dieses Dokuments. Eine Liste der allgemeine bewährte Methoden finden Sie unter [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis) .

**Hinweis**  
Wenn ein Treiber eine Richtlinie Power bei einem Gerät besitzt, wird ein Gerät Power IRP als Reaktion auf das Empfangen von einem System Power IRP generiert. Treiber müssen nicht warten, um das System IRP auszuführen, bis das Gerät IRP abgeschlossen ist, da dieser Wait andere Geräte verhindern kann, dass ihre IRPs System empfangen. In dieser Artikelreihe wartet Ursache Serialisierung Verzögerungen und das gesamte Zeit anhalten erhöht.

 

**Weitere Informationen**

[MSDN: IRP\_MN\_ABFRAGE\_POWER](http://go.microsoft.com/fwlink/?LinkId=247506)

### <a name="a-href-idoo-flush-storage-volumes-durationaflush-storage-volumes-duration"></a><a href="" id="oo-flush-storage-volumes-duration"></a>Leeren Speicher Volumes Dauer

**Am besten:** Anwendungsentwickler, Windows-Dienst-Entwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, der Computer zum Schreiben in die Registrierung und andere geänderten Seiten auf sekundären Speicher speichern.

**Typische Schlüsselfaktoren Faktoren**

Die Zeit, die dieser Metrik hängt die Menge der Daten, die gelöscht werden soll.

**Analyse und Schritte zur Wiederherstellung**

Identifizieren der Prozesse, die für diese Daten verantwortlich sind erfordert Erweiterte Analysen, die den Rahmen dieses Dokuments sprengen; alle Prozesse, die große Datenmengen direkt vor dem Herunterfahren schreibt sind jedoch Verlusts.

Beispiele: eine Anwendung, die eine Datei mit mehreren Megabyte geschrieben haben, mithilfe von zwischengespeicherten e/a direkt vor dem Beenden oder ein Dienst, der beim Herunterfahren große Mengen von einer Datei zugeordneten Speicher ändert.

### <a name="a-href-idoo-suspend-devices-durationasuspend-devices-duration"></a><a href="" id="oo-suspend-devices-duration"></a>Geräte Dauer anhalten

**Am besten:** Treiberentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Während der Phase beim Herunterfahren des Start-Leistung (Fast Start) Szenarios wird jedem Gerätetreiber Potenzierung gesendet (IRP\_MJ\_POWER) e/a (IRP, der IRP\_MN\_FESTLEGEN\_POWER minor Code und eine Potenz Statusdienst (für Boot-Leistung (Fast Start) oder Ruhezustand Leistung S4), S3 für Standby-Leistung.

Diese Metrik misst die Zeit, die für alle Treiber die Leistungsfähigkeit Set IRP Verarbeitung erforderlich ist.

Wenn Gerätetreiber Verarbeiten dieser IRP, sie speichern die entsprechende Gerätekontext (sofern erforderlich) und Put das Gerät in den entsprechenden Status für Standbymodus oder Ruhezustand. Jeder Treiber kann Herunterfahren des Systems durch nicht umgehend behandeln die IRP verzögern.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht der Phase angezeigt, das eine Liste der Geräte und deren entsprechende Dauer enthält.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik erfasst die kumulierte Zeit, die alle Treiber zum Reagieren auf eine Abfrage Power ausführen. Diese Metrik kann von einem einzelnen Treiber betroffen sein, die zusätzlich zu den kumulierte Zeit aller Antworten reagieren zu lange dauert.

**Hinweis**  
Wenn ein Treiber eine Richtlinie Power bei einem Gerät besitzt, wird ein Gerät Power IRP als Reaktion auf das Empfangen von einem System Power IRP generiert. Treiber müssen nicht warten, um das System IRP auszuführen, bis das Gerät IRP abgeschlossen ist, da dieser Wait andere Geräte verhindern kann, dass ihre IRPs System empfangen. In dieser Artikelreihe wartet Ursache Serialisierung Verzögerungen und das gesamte Zeit anhalten erhöht.

 

**Analyse und Schritte zur Wiederherstellung**

Sie können einen Treiber oder Treibern, die diese Metrik erheblich beeinträchtigen, anhand der untergeordneten Metriken identifizieren. Lange Verzögerungen bei der Treiber Antwort Dauer in der Regel erstellen, Probleme, die für ein gegebenes spezifisch sind. Wenn solche ein Problem generiert wird, führen Sie den Link in der Ausgabe erweiterte Problemdetails angezeigt. Wenn ein Problem nicht generiert wird, ist nachfolgende Analyse in WPA erforderlich; Diese Art der Analyse ist nicht Gegenstand dieses Dokuments.

**Weitere Informationen**

[MSDN: IRP\_MN\_FESTLEGEN\_POWER](http://go.microsoft.com/fwlink/?LinkId=247508)

### <a name="a-href-idoo-hiberfile-write-durationahiberfile-write-duration"></a><a href="" id="oo-hiberfile-write-duration"></a>Dauer der Hiberfile schreiben

**Am besten:** Anwendungsentwickler, Windows-Dienst-Entwickler, Treiber-Entwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, die das System zum Schreiben der relevanten Inhalt der Hauptspeicher an den sekundären Speicher; insbesondere in hiberfile.sys-Datei, die in der Regel im Stammverzeichnis des Systemlaufwerks gefunden wird.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird die Größe der Hiberfile in Kilobyte dargestellt.

**Typische Schlüsselfaktoren Faktoren**

Die zum Schreiben der Hiberfile erforderliche Zeit ist direkt proportional zum die Menge der Daten, die geschrieben werden soll. Diese Daten besteht aus Arbeitsspeicher, die vom Betriebssystem, Treiber und Dienste, zusätzlich zur alle Daten, die das System während System Resume lesen muss (Siehe während der Phase der Superfetch vorbereiten Arbeitsspeicher) verwendet wird.

Ein Treiber, der viel Arbeitsspeicher verwendet kann dieser Metrik beeinflussen, indem Sie das Schreiben von Daten in die Hiberfile Speicher-Manager. Oder eine Anwendung starten kann dazu führen, dass große Datenmengen im Pfad Resume gelesen werden sollen. In diesen Fällen gewährleistet der Superfetch-Dienst an, dass Daten in die Hiberfile, um zu vermeiden, langsame zufällige Kommunikationsteilnehmer Resume Pfad enthalten ist.

**Hinweis**  
Festplatte physischen Leistungsmerkmale wie Durchsatz für sequenzielle Schreibvorgänge, wirkt sich auch auf diese Metrik.

 

**Analyse und Schritte zur Wiederherstellung**

Identifizieren die spezifischen Komponenten, die für die Dauer der länger Hiberfile Schreibzugriff berücksichtigt erfordert detaillierte Speicheranalyse und ist nicht Gegenstand dieses Dokuments. Jedoch kann aller ausgeführten Treiber und Dienste zu dieser Metrik beitragen großer Arbeitsspeicher Zuweisungen beibehalten. Die Anzahl und Speicherbedarf der Start-Anwendungen und anderer Komponenten, die Daten während des Starts lesen können auch diese Metrik beeinflussen.

### <a name="a-href-idoo-bios-initialization-durationabios-initialization-duration"></a><a href="" id="oo-bios-initialization-duration"></a>Dauer der BIOS-Initialisierung

**Am besten:** BIOS-Hersteller

**Bewertung relevant:**

1.  Start-Leistung (Fast Start)

2.  Start-Leistung (vollständige Boot)

3.  Standby-Leistung

4.  Ruhezustand Leistung

Diese Metrik misst die Zeit, die Plattform Firmware zum Identifizierung und Hardwaregeräten initialisieren und Ausführen einer Selbsttest (POST).

**Hinweis**  
BIOS Initialisierung passiert, bevor das Betriebssystem Steuerelement erhält. Die Bewertung kann nicht sorgfältig die Phase überprüft und können nur Bericht auf die Dauer.

 

**Detaillierte untergeordnete Metriken**

Start-Leistung (Fast Start) ist nur in einem Szenario, zusätzliche untergeordnete Metriken für diese Metrik bereitzustellen. Für Systeme, die BIOS enthalten, die neuesten Advanced Configuration and Power Interface (ACPI) standard (ACPI 5.0) unterstützen, kann diese Metrik erweitert werden, um die POST-Zeit angezeigt, die von der Firmware Leistung Daten-Tabelle (FPDT) benötigt wird. Dies ist eine alternative Maßeinheit für die Dauer BIOS Initialisierung, die von der Kernel Instrumentation gemeldet wird.

**Typische Schlüsselfaktoren Faktoren**

Die Startreihenfolge, die für das System festgelegt ist kann eine erhebliche Datenquelle Verzögerung während der Initialisierung BIOS entsprechen. Dieser Auftrag kann das System zu überprüfen, startbaren optische, Diskette, USB- oder anderen Festplatten, bevor Windows geladen erfordern. PXE-Start (Netzwerk/Remote Boot) kann auch als Teil der Startreihenfolge festgelegt werden. Wenn diese Option aktiviert ist, können sie die Verzögerung erheblich beeinträchtigen. Einige BIOS-Konfigurationen haben auch erweiterte Diagnose oder Überprüfungsmodi, die für die Durchführung länger dauern können.

**Analyse und Schritte zur Wiederherstellung**

Keine zusätzlichen Informationen werden für die Phase BIOS erfasst. Wie aktiviert Faktoren mit Einfluss auf die normale sollte PXE-Start überprüft werden soll. BIOS-Hersteller sollte konsultiert werden, wenn Sie selektieren oder diese Einstellungen ändern möchten. Eine tiefere Untersuchung der BIOS Initialisierungsphase ist nicht Gegenstand dieses Dokuments.

### <a name="a-href-idoo-total-bootatotal-boot-excluding-bios-duration-total-resume-excluding-bios-duration"></a><a href="" id="oo-total-boot"></a>Insgesamt Boot \[ausschließen BIOS\] Dauer & insgesamt Resume \[ausschließen BIOS\] Dauer

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, der der Computer verbringt gestartet. Diese Metrik erfasst die Zeit ab dem Ende BIOS Initialisierung bis zum Ende einer Phase Beitrag weiter, die beendet, wenn das System Leerlauf erreicht wird.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine Liste der untergeordneten Phasen beim Starten/Fortsetzen angezeigt.

**Hinweis**  
Dauer der untergeordneten Phasen entspricht nicht notwendigerweise die Gesamtdauer.

 

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik ist eine allgemeine Metrik für System Boot/fortsetzen, und es wird dadurch beeinflusst, keine Softwarekomponenten, die auf den Pfad Boot/fortsetzen ausgeführt.

**Analyse und Schritte zur Wiederherstellung**

Erweitern Sie diese Metrik, um die untergeordneten Metriken angezeigt, die Weitere Informationen zu einzelnen untergeordneten Phasen bereitzustellen. Untersuchen Sie Probleme bei der potenziellen Verzögerung Mitwirkende suchen und einzelnen untergeordneten Phase Metriken.

### <a name="a-href-idoo-main-pathamain-path-boot-duration-main-path-resume-duration"></a><a href="" id="oo-main-path"></a>Main Pfad Boot Dauer & Hauptfenster Pfad Resume Dauer

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst die Uhrzeit aus, wenn der Computer Start beginnt, bis auf dem Desktop des Benutzers angezeigt wird. Diese Metrik erfasst die Zeit ab dem Ende der BIOS-Initialisierung wird die Windows 8-Benutzeroberfläche angezeigt, bis die Beitrag weiter Phase ist nicht enthalten.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine Liste der untergeordneten Phasen (mit Ausnahme der Phase Post ein/aus) dargestellt.

**Hinweis**  
Dauer der untergeordneten Phasen entspricht nicht notwendigerweise die Gesamtdauer.

 

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik ist eine allgemeine Metrik für Boot/fortsetzen, um einem sichtbaren Desktop. Es kann durch keine Softwarekomponenten beeinflusst werden, die ausgeführt werden, bevor der Desktop angezeigt.

**Analyse und Schritte zur Wiederherstellung**

Erweitern Sie diese Metrik um untergeordnete Metriken anzuzeigen, die auf einzelnen untergeordneten Phasen Bereitstellen weiterer Informationen ein. Untersuchen Sie Probleme bei der potenziellen Verzögerung Mitwirkende suchen und einzelnen untergeordneten Phase Metriken.

### <a name="a-href-idoo-boot-manageraboot-manager"></a><a href="" id="oo-boot-manager"></a>Start-Manager

**Am besten:** Systemadministratoren

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Ruhezustand Leistung

Diese Metrik misst die Zeit zum Suchen und starten Winload.exe Ladeprogramm des Betriebssystems, in der Windows-Boot-Partition.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik kann von BitLocker-Operationen betroffen sein, insbesondere dann, wenn Sie eine PIN für BitLocker So starten Sie erforderlich ist.

**Analyse und Schritte zur Wiederherstellung**

Verwenden einer BitLocker unlock-Methode, die keine manuelle Eingabe der PIN-NUMMER erforderlich ist.

### <a name="a-href-idoo-hiberfile-read-durationahiberfile-read-duration"></a><a href="" id="oo-hiberfile-read-duration"></a>Dauer der Hiberfile lesen

**Am besten:** Anwendungsentwickler, Windows-Dienst-Entwickler, Entwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Ruhezustand Leistung

Diese Metrik misst die Zeit, die das System zum Lesen des Inhalts der Hiberfile in den Hauptspeicher.

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird die Größe der Hiberfile (in KB) dargestellt.

**Typische Schlüsselfaktoren Faktoren**

Die Zeit, die zum Lesen der Hiberfile ist direkt proportional zum die Menge der Daten, die gelesen werden müssen. Diese Daten besteht aus Daten im Speicher, die vom Betriebssystem, Treiber und Dienste, die neben den Daten, die das System für System fortsetzen (identifiziert der Phase Superfetch vorbereiten Arbeitsspeicher Herunterfahren Standby) verwendet wird.

**Hinweis**  
Festplatte physischen Leistungsmerkmale wie sequenzielle Lesen der Durchsatz, wirkt sich auch auf diese Metrik.

 

**Analyse und Schritte zur Wiederherstellung**

Identifizieren die einzelnen Komponenten, die zum länger Hiberfile beitragen lesen Dauer erfordert detaillierte Speicheranalyse und ist nicht Gegenstand dieses Dokuments.

**Hinweis**  
Jede ausgeführte Treiber und jeden Dienst kann Beibehaltung großer Arbeitsspeicher Zuweisungen dieser Metrik beitragen. Die Anzahl und Speicherbedarf von Autostart-Programme und anderer Komponenten, die für das Lesen von Daten während des Starts beeinflussen auch diese Metrik.

 

### <a name="a-href-idoo-resume-devices-durationaresume-devices-duration"></a><a href="" id="oo-resume-devices-duration"></a>Dauer der Resume-Geräte

**Am besten:** Treiberentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Standby-Leistung

-   Ruhezustand Leistung

Beim Herunterfahren/unterbrechen, wird jedem Gerätetreiber Potenzierung gesendet (IRP\_MJ\_POWER) IRP, die eine IRP hat\_MN\_FESTLEGEN\_POWER minor-Code und Working power Zustand. Gerätetreiber senden anschließend Gerät Power IRPs entsprechende Geräte. Diese Metrik misst für alle Treiber die Set Leistungsfähigkeit IRP verarbeitet.

**Hinweis**  
Treiber sollten nicht das System Power IRP während dieser Phase beibehalten. Jeder Treiber verzögern kann Systemstart, indem Sie die Leistung des Systems IRP nicht umgehend behandeln.

 

**Detaillierte untergeordnete Metriken**

Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht der Phase mit einer Liste von Geräten und deren entsprechende Dauer dargestellt.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik erfasst die kumulierte Zeit, die alle Treiber ergreifen, um auf eine IRP reagieren\_MN\_FESTGELEGT\_POWER Power-Anforderung. Diese Metrik kann von einem einzelnen Treiber betroffen sein, die zu viel neben die kumulierte Zeit aller Treiber Antworten Zeit.

**Hinweis**  
Wenn ein Treiber eine Richtlinie Power bei einem Gerät besitzt, wird ein Gerät Power IRP als Reaktion auf das Empfangen von einem System Power IRP generiert. Treiber müssen nicht warten, um das System IRP auszuführen, bis das Gerät IRP abgeschlossen ist, da diese Wait andere Geräte verhindern, kann ihre IRPs System empfangen. In dieser Artikelreihe wartet Ursache Serialisierung Verzögerungen und das gesamte Zeit anhalten erhöht.

 

**Analyse und Schritte zur Wiederherstellung**

Sie können einen Treiber oder Treibern, die diese Metrik erheblich beeinträchtigen, verfolgen die untergeordneten Metriken identifizieren. Lange Verzögerungen bei der Treiber Antworten erzeugen normalerweise Probleme, die für ein gegebenes spezifisch sind. Wenn solche ein Problem generiert wird, führen Sie den Link in der Ausgabe erweiterte Problemdetails angezeigt. Wenn ein Problem nicht generiert wird, ist die nachfolgende Analyse in WPA erforderlich. Dies ist nicht Gegenstand dieses Dokuments. Finden Sie unter [bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis).

**Weitere Informationen**

[MSDN: IRP\_MN\_FESTLEGEN\_POWER](http://go.microsoft.com/fwlink/?LinkId=247508)

### <a name="a-href-idoo-operating-system-selection-menu-durationaoperating-system-selection-menu-duration"></a><a href="" id="oo-operating-system-selection-menu-duration"></a>Betriebssystem Auswahl im Menüdauer

**Am besten:** Systemadministratoren

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

Diese Metrik misst die Zeit, die für das Betriebssystem Auswahlmenü, stellen Sie die Standardauswahl. Standardmäßig ist nach 30 Sekunden (ohne Benutzereingriff) eine Auswahl getroffen.

**Typische Schlüsselfaktoren Faktoren**

Diese Metrik ist durch Systemverhalten nicht betroffen. Diese Metrik wird gemeldet, nur auf Systeme, die mehrere Betriebssysteme installiert sind, und 30 Sekunden wird immer gemeldet, wenn kein Benutzereingriff durchgeführt wird.

**Hinweis**  
Obwohl die Dauer dieser Metrik von Systemverhalten nicht beeinträchtigt wird, hat der Startvorgang zahlreiche asynchrone Vorgänge, die während dieser Zeit ausgeführt werden können. Diese Prozesse können sich auf die Ergebnisse für Aktivitäten auswirken, die auftreten, nachdem die Standardauswahl vorgenommen wird, da einige der arbeiten, die normalerweise während dieser Zeiten durchgeführt wird bereits ausgeführt werden.

 

**Analyse und Schritte zur Wiederherstellung**

Entfernen Sie alle installierten Betriebssysteme außer für das Element, das analysiert wird. Zum Anzeigen der Liste der derzeit installierten Betriebssysteme (einschließlich der Einstellungen, die dieses Menü betreffen) führen Sie **msconfig.exe** an einer Eingabeaufforderung aus, und wählen Sie dann die Registerkarte **Start** .

### <a name="a-href-idoo-winlogon-resume-durationawinlogon-resume-duration"></a><a href="" id="oo-winlogon-resume-duration"></a>Winlogon Resume Dauer

**Am besten:** Winlogon Abonnenten Entwickler, Gruppenrichtlinien Skript Besitzer, Systemadministratoren, Anmeldeinformationen Anbieter Autoren

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Ruhezustand Leistung

Diese Metrik stellt Timespan mehrerer Winlogon Legenden und Vorgänge, wie die Interaktion mit Winlogon Abonnenten. Diese Metrik ist nicht die kumulierte Zeit in Abonnenten Benachrichtigungen ist, und sollte nicht als solche behandelt werden.

**Detaillierte untergeordnete Metriken**

Start-Leistung (Fast Start) ist die einzige Bewertung, die zusätzliche untergeordnete Metriken für diese Metrik bereitstellt. Wenn die Metrik erweitert wird, wird eine ausführlichere Ansicht der Phase angezeigt, das die Zeiten, die von jedem Abonnenten Winlogon dividiert umfasst. Während der Reaktivierung stellt Winlogon synchrone Abonnenten Benachrichtigungen für registrierte Abonnenten für die folgenden zwei Benachrichtigung:

-   Anmeldung

-   Starten der Shell

Wenn es vergrößert wurde, werden diese zwei Benachrichtigungstypen als untergeordnete Metriken angezeigt. Jeder dieser Typen verfügt über eine Liste von Abonnenten (z. B. Profile oder GPClient) als zusätzliche untergeordnete Metriken. Jeder Abonnent sind die spezifischen Instanzen von **Connect an Abonnenten** und **Abonnent rufen Sie** für dieses Abonnenten aufgeführt.

Für alle Szenarien können Winlogon Abonnenten Herunterfahren von braucht zu lange zum Verarbeiten diese Benachrichtigungen verzögern. Beispielsweise muss ein Profildiensts (Profile) im Benutzerprofil synchronisieren, wenn das Feature **Roaming (Remote) Profile** auf diesem Computer aktiviert ist. Oder ein Gruppenrichtlinienclient (GPClient) möglicherweise durch eine Richtlinie System oder einer Domäne für bestimmte Aufgaben bei der Benutzeranmeldung konfiguriert werden. Diese Aufgaben sind in der Regel durch ein System oder Domänenadministrator an konfiguriert und im Allgemeinen nicht von Microsoft stammenden gehören Skripts ausführen.

**Typische Schlüsselfaktoren Faktoren**

Wenn Sie diese Metrik untersuchen, sollten Sie den Abonnenten Winlogon konzentrieren, die die Benachrichtigungen für Anmeldung und Shell starten zu verarbeiten.

**Analyse und Schritte zur Wiederherstellung**

Überprüfen Sie wie oft der einzelnen Abonnenten Vorgänge. Bestimmte Probleme werden in der Regel für länger dauern für Abonnenten generiert. Sie können auch Einblick durch WPA der Zeitintervall eines Abonnenten öffnen. Beispielsweise wenn Gespräch Abonnenten GPClient 10 Sekunden dauert, kann eine Prüfung der dieser Dauer in WPA offen legen, dass ein bestimmte benutzerdefiniertes Skript 9 Sekunden lang nicht genügend 10 ausgeführt wird. Dies kann im **Prozess Lebensdauer** Diagramm angezeigt werden. Es gibt an, dass dieses Skript mögliche Ursache für die Verzögerung ist.

**Weitere Informationen**

[Winlogon Benachrichtigungsereignisse](http://go.microsoft.com/fwlink/?LinkId=247505)

### <a name="a-href-idoo-explorer-initialization-durationaexplorer-initialization-duration"></a><a href="" id="oo-explorer-initialization-duration"></a>Explorer Initialisierung Dauer

**Am besten:** Zum Starten des Anwendungsentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

Diese Metrik erfasst die Zeit ab dem Ende der Phase Winlogon, bis die Windows-Shell (Explorer.exe) ein initialisiertes Startseite meldet. Sie enthält den Beginn des Prozesses userinit.exe, die wiederum Explorer.exe gestartet wird. Darüber hinaus die Initiierung von Autostart-Programme, die unter Registrierungsschlüssel **RunOnce** gespeichert sind.

**Typische Schlüsselfaktoren Faktoren**

Keine **RunOnce** Anwendungstypen sollte in den meisten Fällen in dieser Phase beim Initialisieren des Explorer-Prozesses ausgegeben werden. Explorer liest eine Anzahl von Bibliotheken und Dateien in den Arbeitsspeicher während der Initialisierung neu. Konkurriert e/a aus anderen ausgeführten Komponenten können stören und Verzögerung für diese Aktivität.

**Analyse und Schritte zur Wiederherstellung**

Bestimmte Probleme werden in der Regel für länger dauern der Explorer Initialisierungsphase generiert. Sie können mehrere Einblick durch WPA öffnen, um das Zeitintervall für die Initialisierung von Explorer-Aktivität. Platzieren von Applikationen im Schlüssel **RunOnce** regelmäßig, da er Explorer Initialisierung verzögert zu vermeiden.

Untersuchen von bestimmten Problemen während der Initialisierung von Explorer ist nicht Gegenstand dieses Dokuments. Eine Liste der allgemeine bewährte Methoden finden Sie unter [Bewährte Methoden für die Zeit kritische Vorgänge](#fs-analysis).

### <a name="a-href-idoo-post-on-off-durationapost-onoff-duration"></a><a href="" id="oo-post-on-off-duration"></a>On/Off Dauer buchen

**Am besten:** Anwendungsentwickler

**Bewertung relevant:**

-   Start-Leistung (Fast Start)

-   Start-Leistung (vollständige Boot)

-   Standby-Leistung

-   Ruhezustand Leistung

Diese Metrik misst, nach Ausführung des Post ein/aus dem System wird nach vernünftigem Ermessen im Leerlauf und auf Benutzereingaben reagieren. Das Ziel dieser Phase ist, zu binden und quantifiziert Verarbeitung im Hintergrund, die fortgesetzt wird, nachdem der Startseite angezeigt. Diese Metrik misst die Dauer der Phase Beitrag weiter, die die Zeitspanne darstellt, für das System zum Sammeln von 5 Sekunden der Leerlaufzeit benötigt werden. Dieses Mal werden Mobilgeräts auf die Auslastung der CPU und Speicherung in 500 ms Zeitfenster gesammelt. Wenn weniger als 20 %, die für diesen Zeitraum dieses Fensters die kumulierte Zeit der Auslastung CPU und Speicher ist (500 ms – max \[CPU-Zeit, Zeit\] im Fenster) wird die gesamte Leerlaufzeit bis 5 Sekunden erreicht wird hinzugefügt. Die Metrik meldet diese Dauer abzüglich der gesammelten Leerlaufzeit bis 5 Sekunden.

**Hinweis**  
Niedrige Priorität CPU und Speicher Auslastung Zeiten werden für diese Berechnung ignoriert.

 

Durch Datenträger-e/a oder Berechnung ausführen können Sie jede Art von Softwarekomponente, die in dieser Phase ausgeführt wird die Phasendauer beeinflussen.

**Detaillierte untergeordnete Metriken**

Keine tatsächlichen untergeordnete Metriken in dieser Phase vorhanden sein. Da die Phasendauer proportional zur Ressourcenverwendung ist, Sie können jedoch erhalten Erkenntnisse durch Betrachtung der Prozesse, die während dieser Phase ausgeführt werden (erweitern **Prozesse pro Phase** in Windows Assessment-Konsole).

**Typische Schlüsselfaktoren Faktoren**

Keine Softwarekomponenten, die während dieser Phase CPU oder Speicherung Ressourcen verwenden können potenziell zur Gesamtzeit beitragen. Zusätzliche Autostart-Programme haben in der Regel sich negativ auf die Phase Post ein/aus.

In den Standby-Leistung und Ruhezustand Szenarien, die nicht aus der Sitzung des Benutzers anzumelden, ist dieser Phase von Clientanwendungen betroffen, die in die aktuelle Arbeitslast ausgeführt werden.

**Analyse und Schritte zur Wiederherstellung**

Identifizieren der Prozesse, die die meisten Ressourcen beanspruchen. Sie können diese indem CPU und Datenträger Auslastung Diagramme und zusammenfassenden Tabellen in WPA ansehen oder **Prozesse pro Phase** in Windows Assessment-Konsole erweitern Schritte durchführen. Probleme stehen ebenfalls für generiert werden wahrscheinlich auslösende Prozesse. Finden Sie nachschlagen unter Ressource Auslastung für weitere Details.

Des Problems für die Start-Leistung (Fast Start) und Bewertung Start-Leistung (vollständige Boot) entfernen Sie unwichtige Applications aus dem Pfad zum Starten des oder verwenden Sie der Taskplaner, um diese Anwendungen zu einem späteren Zeitpunkt zu starten. Wenn eine Anwendung für die Anmeldung des Benutzers entscheidend ist (beispielsweise bietet Credential Provider Dienste oder Netzwerkdienste), stellen Sie sicher, dass die Anwendung für die minimale Ressourcenverbrauch optimiert ist.

Vermeiden der Verwendung von verwaltetem Code (CLR-basiert) zum Starten des Applications, da die Ressource kostspielige Initialisierung von .NET Framework ihre Initialisierung aktiviert werden kann. Weitere wird Post weiter Phase Zeiten auswirken und Benutzer Reaktionsfähigkeit beeinträchtigen.

## <a name="a-href-idfs-issuesaissues"></a><a href="" id="fs-issues"></a>Probleme


Die Bewertung weiter Übergang Leistung erweiterte Problem Analysen durchführen und Links auf WPA von Problemen, die die Bewertung identifiziert wurden. Wenn WPA geöffnet wird, möglicherweise zusätzliche Informationen zu dem Datenträger oder CPU-Aktivität verfügbar, je nach Art des Problems. Dieser Abschnitt beschreibt allgemeine genauer Techniken, die Sie zum Analysieren von Leistungsproblemen verwenden können.

**Suchen Sie nach dem größten Mitwirkenden**

Öffnen Sie die Ergebnisdatei Assessment in Windows Assessment-Konsole zu, und erweitern Sie die entsprechenden übergeordneten Metrik. Die untergeordneten Unterwebsites Metriken liefern in der Regel auf bestimmte Komponenten, die Einfluss auf die Metrik "Parent".

Angenommen Sie, die [Beim Herunterfahren Prozesse Dauer](#oo-shutdown-processes) Metrik. Sie können die Metrik zum Anzeigen von drei untergeordneten metrischer Tabellen in dieser Phase erweitern. Die ersten beiden Tabellen angezeigt, die CPU und Datenträgerverwendung und die dritte Tabelle wird die Dauer der einzelnen Prozesse, die heruntergefahren werden.

Zusätzliche Spalten, wie die Spalte **Detail** enthalten weitere Einzelheiten zur die untergeordneten Metriken. In **Benutzer Sitzung zum Herunterfahren von Prozessen**wird in der Spalte **Details** eine PID.

**Hinweis**  
In der Standardansicht möglicherweise die **Detail** -Spalte den Wert enthalten "Verschiedene", da PID auf Iterationen aggregiert werden können. Erweitern Sie Iterationen, um einzelne PID finden Sie unter.

 

Windows-Assessment-Konsole können Sie die Liste der untergeordneten Metriken nach einer beliebigen Datenspalte (außer für die oberste Ebene Fast Start für Listen, die beim Herunterfahren/Start nach Phase Reihenfolge sortiert sind phase) sortieren.

Beispielsweise in der Liste der erweiterten Prozess für die Phase [Benutzer Sitzung zum Herunterfahren von Prozessen](#oo-user-session-shutdown-duration) , mit der rechten Maustaste in der Tabellenkopfzeile, und wählen Sie dann **Absteigend sortieren von Zeilen**.

Sie können dieses Verfahren für mehrere Dauer der obersten Ebene Phase verwenden.

**Sehen Sie sich die Auslastung der Ressource**

Anzeigen der detaillierten Ressource Auslastung für jeden Prozess in dieser Phase. Zum Abrufen dieser Informationen die Prozesse für jede Registerkarte Phase im Abschnitt erweitern und dieses anschließend sortieren nach CPU-Auslastung oder Gesamtverwendung des Datenträgers.

**Weitere Informationen**

Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Probleme der Depth-Analyse](common-in-depth-analysis-issues.md).

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Die Bewertung von Berichten Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Strom ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten aus:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="a-href-idfs-analysisabest-practices-for-time-critical-tasks"></a><a href="" id="fs-analysis"></a>Bewährte Methoden für die Zeit kritische Vorgänge


Wenn Sie nicht, dass eine Aufgabe verzögern möchten, stellen Sie sicher, dass es keine Funktion ist die lange dauert. Im folgenden sind einige Punkte, zu vermeiden.

-   Wenn eine zeitlich bedingte Antwort erforderlich, beispielsweise an den Prozess der WM ist\_ENDSESSION während des Herunterfahrens, nicht auf alle wesentlichen Aufgaben beim Empfang der Anforderung (neben dem Daten Zuverlässigkeit Arbeit wie speichern Benutzer Änderungen vor, was ausgeführt werden muss) planen.

-   Vermeiden Sie Operationen was mehr Zeit, es sei denn, absolut notwendig dauern kann. Zurückstellen Sie diese, bis die aktuelle Zeit wichtige Aufgabe abgeschlossen ist. Vermeiden Sie eine beliebige APIs, das die Warnung enthalten: "Vorsicht vor Überlegungen zur Leistung bei der Verwendung dieser API".

-   Vermeiden Sie Abhängigkeiten Netzwerk, da jede Anforderung Netzwerk durch Netzwerkprobleme verzögert werden kann. Dies gilt insbesondere für Szenarien beim Starten und beenden, da das Netzwerk nicht garantiert ist für die gesamte Zeit verfügbar sein soll.

-   Vermeiden Sie lange Timeouts. Wenn eine Wartezeit erforderlich ist, vergewissern Sie sich die Wartezeit nach vernünftigem Ermessen durch einen kleinen (im Zusammenhang mit der Zeit kritische Vorgänge betreffende) gebunden ist Timeoutwerts.

-   Vermeiden Sie eine übermäßige Berechnung. Behalten Sie im Hinterkopf, die Prozessoren Geschwindigkeit variieren, damit eine Berechnung Offlineschalten von 100 ms auf einem Computer sehr schnell letztlich möglicherweise Sekunden auf eine langsamer.

-   Vermeiden Sie unnötige Speicher e/a. Alle e/a-Anforderung konnte von anderen Komponenten verzögert. Können Sie jederzeit es gibt Dutzende von Anwendung und Dienste, die auf einem normalen System ausgeführt, und die Speicherressourcen beschränkt werden. Die e/a-Anforderung möglicherweise hinter Hunderten von ähnliche Anforderungen von anderen Komponenten in der Warteschlange abrufen.

-   Vermeiden Sie Datenträger geleert, z. B. die durch einen Aufruf von API FlushFileBuffers initiiert hat. Das leeren bewirkt, dass Datenträgerstapel, um den Zwischenspeicher zu löschen und so erzwingen Sie die Festplatte zum Schreiben von Daten in seine RAM Puffer zurückgegeben werden sollen. Dieser Vorgang wird in der Regel ist sehr kostspielig und Datenkonsistenz wird nicht garantiert werden, da die Festplatten oft die Anforderung ignorieren.

-   Vermeiden Sie das leeren Registrierungsstrukturen durch Aufrufen von RegFlushKey-API. Aufgrund der Registrierung entwerfen wird die API geänderte Daten für die gesamte Struktur an, die auf den Datenträger geleert werden, das eine sehr teuer Operation verursacht. Registrierungsschlüssel für das leeren ist eine Aktion, die nicht in der Regel benötigt wird, da das Betriebssystem zum alle Komponenten eine konsistenten Registrierungsansicht bietet. Darüber hinaus wird die Registrierung selbst asynchrone Leert alle mehrere Sekunden.

-   Vermeiden Sie neue RPC-Verbindungen öffnen, da der RPC-Authentifizierungsprozess kostspielig ist. Einrichten einer neuen RPC-Verbindung umfasst kostspielige sicherheitsüberprüfungen.

-   Vermeiden Sie transaktionale APIs wie TxF-APIs aufrufen, wie sie häufig eine Reihe von kostenintensive Vorgänge für jede API-Aufruf ausführen. Diese APIs erhalten Kosten der Leistung, Zuverlässigkeit, damit diese APIs nicht während der Zeit kritische Vorgänge verwendet werden soll.

## <a name="related-topics"></a>Verwandte Themen


[Bewertung](assessments.md)

[Ein-/ausschalten Übergang-Leistung](onoff-transition-performance.md)

[Automatisieren von Neustarts vor dem Ausführen einer Bewertung](automate-reboots-before-you-run-an-assessment.md)

[Windows-Assessment-Toolkit](index.md)

 

 







