---
title: "Ergebnisse für die verbundene Standby Energie Effizienz Bewertung"
description: "Ergebnisse für die verbundene Standby Energie Effizienz Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 598d29c6-3d81-4316-99ce-da50473f34aa
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: e2e318b357177909bfb357edb56a0ac2e453aabd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-connected-standby-energy-efficiency-assessment"></a>Ergebnisse für die verbundene Standby Energie Effizienz Bewertung


**Standby verbunden Energie-Effizienz** Assessment Ergebnisse zeigen Metriken und Probleme, die Energie Effizienz Probleme zu markieren. Wenn möglich, wird die Ursache des Problems Effizienz Energie identifiziert. Beispielsweise könnte es Treiber, Dienste oder Prozesse. Empfohlene Lösungen für diese Probleme stehen zur Verfügung.

Dieses Thema hilft Ihnen die interpretiert werden die Ergebnisse, die mit einer **Akkulaufzeit während verbunden Standby** Auftrag, der die Bewertung **Standby verbunden Energie-Effizienz** verwendet. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die Computer Akkulaufzeit auswirken.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-metrics)

-   [Probleme](#bkmk-idleissues)

Weitere Informationen zu Energie Effizienz-bezogene Aufträgen finden Sie unter [Dem Standbymodus Energie-Effizienz verbunden](connected-standby-energy-efficiency.md).

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>Ziele-Datei


Sie können benutzerdefinierte Ziele Ihrer Verbesserungen in der Ergebnisanzeige gemessen erstellen. Ziele Dateien sind eine Ursachenanalyse Tool, das helfen zu verstehen, wie ein PC ausgeführt wird und zum Vergleichen von PCs in Ihrem Unternehmen.

Beispielsweise Ziele für einen einfachen Laptop möglicherweise nicht die Ziele für einen high-End-Desktopcomputer festgelegten oder erwartet Land/Ihrer Region möglicherweise so, dass Sie die Flexibilität, verschiedene Ziele zu definieren möchten und verbessert die wichtige Anforderungen als Zeit und Technologie ändern.

Bei dem Ziel für diese Metrik ein metrischer Wert verglichen wird, ist der Status farblich in der Ansicht Ergebnis wie folgt an:

-   Hellviolett bedeutet, dass das System einen größeren Benutzerkomfort verfügt und keine wahrgenommene Probleme vorliegen.

-   Mittlere Lila bedeutet, dass die Benutzeroberfläche zulässige ist und Sie können das System optimieren. Überprüfen Sie die Empfehlungen und Analyse, um herauszufinden, welche Verbesserungen an das System hergestellt werden können. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich.

-   Dunkles Lila bedeutet, dass das System benutzerfreundlich verfügt und erhebliche Platz für Verbesserungen vorhanden ist. Überprüfen der Empfehlungen und Analyse, um die Verbesserungen, die das System vorgenommen werden können, finden Sie unter. Diese Software Änderungen, konfigurationsänderungen oder Hardware Änderungen möglich. Möglicherweise müssen Sie erwägen Kompromissen, um eine hohe Qualität-Windows-Erfahrung zu übermitteln.

-   Keine Farbe bedeutet, dass es keine Ziele für die Metrik definiert sind.

**Hinweis**  
In der Windows Assessment Toolkit für Windows 8 umfassen einige Bewertung Ziele Standarddateien. Zum ersten Mal anzeigen von Ergebnisse mit dieser Version der Tools, wird die Ziele-Standarddatei verwendet. Jedoch können Sie auch benutzerdefinierte Ziele für Windows 8 die gleiche Weise definieren, die Sie für Windows 8.1 und Windows-10 können.

 

Sie können legen Sie die Ziele und eine Datei Ziele zu diesem Speicherort hinzufügen, bevor Sie die Benutzeroberfläche verwenden können, um die benutzerdefinierten Ziele anzuwenden. Nach dem Auswählen einer Datei Ziele wird weiterhin die Ziele-Datei sein, die für alle Ergebnisse verwendet wird, die geöffnet werden.

Nur eine Ziele Datei kann zu einem Zeitpunkt verwendet werden. Ziele für alle Bewertung sind in einer einzigen Ziele Datei festzulegen. Die Bewertungstools sucht Ziele in der folgenden Reihenfolge:

1.  Eine benutzerdefinierte Ziele-Datei

2.  Ziele, die in der Ergebnisdatei definiert sind

3.  Ziele, die im Manifest Assessment definiert sind

Können die Ziele-Beispieldatei, die bereitgestellt wird unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\SDK\\Beispiele\\Ziele Ihrer eigenen Ziele-Datei zu erstellen.

**Hinweis**  
Nicht in eine Datei Ziele mit einem Auftrag Pakete, jedoch können sie für andere Benutzer freigegeben gespeichert werden.

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>Metriken


Die folgenden Metriken werden von der Standby verbunden Energie Effizienz Bewertung generiert:

### <a name="time-spent-in-drips"></a>Zeit in DRIPS

Diese Metrik stellt die Zeit in die unterste Runtime im Leerlauf Power Zustand (DRIPS) als Prozentsatz der Zeit Widerstandsfähigkeit ist.

### <a name="in-quiet-hours"></a>Im stillen Stunden

Diese Metrik stellt die Gesamtzeit in Sekunden, die das System im stillen Stunden während der Ausführung Assessment war. Stille Stunden reduzieren Hintergrundaktivitäten Standby verbunden, die die Ergebnisse beeinträchtigen können.

### <a name="resiliencyin-connected-standby"></a>Resiliency ' In verbundenen Standby

Diese Metrik stellt die Zeit, in Sekunden, Widerstandsfähigkeit, wird während der Geräte opportunistische Ausführung zulässig sind, um tiefere im Leerlauf Zustände an, um Energie zu sparen.

### <a name="sub-metrics"></a>Untergeordnete Metriken

**Geräte**

Diese Metrik stellt die Zeit in Sekunden, die Geräte und Komponenten des Computers gehindert DRIPS einzugeben.

Die Geräte untergeordnete Metrik ist weiter in einzelne Geräte unterteilt. Jedes Gerät ist separat zusammen mit der Gesamtzeit aufgeführt, dass das Gerät verhindert, dass den Computer DRIPS Eingabe.

**Für eine Aktivierung**

In diesem Satz von Metriken stellt die Zeit in Sekunden, die eine Aktivierung verhindert, dass den Computer DRIPS eingeben. Jede Aktivierung wird als eine separate Metrik dargestellt. Einige für eine Aktivierung sind weitere in Unteraufgaben unterteilt.

Für eine Aktivierung, die den Computer für die Eingabe DRIPS verhindern können, sind unten aufgeführt:

-   WNS (Windows-Notification-Services)

-   IDM (Bild Download Manager)

-   Business Intelligence (Broker Infrastruktur)

-   WU (Windows-Aktualisierung)

-   GP (Gruppenrichtlinien)

-   NCSI (Status Netzwerkkonnektivität)

-   Toast-Benachrichtigung

-   PLM (Prozess Lebensdauer Manager)

-   PDC für eine interne Aktivierung

**Resiliency Phase nicht eingegeben.**

Diese Metrik stellt die gesamte Zeit, in Sekunden, die der Computer daran gehindert wurde, Resiliency einzugeben. Diese Metrik wird weitere Zeit beim Eingeben von Standby verbunden und die Uhrzeit beim Beenden von verbunden Standby aufgeschlüsselt.

**CPU-Aktivität**

Diese Metrik stellt die gesamte Zeit, in Sekunden, die Prozessoren aktiv waren, während der Computer im Standbymodus angeschlossen war.

Die CPU-Aktivität untergeordnete Metrik ist weiter in einzelne Prozesse unterteilt. Jeder Prozess ist separat sowie die gesamte Zeit aufgeführt, die der Prozess beim Standby verbunden aktiv war.

### <a name="enterexit-connected-standby"></a>Geben Sie/Exit Standby verbunden

Diese Metrik stellt die gesamte Zeit, in Sekunden, die auf der Computer verbringt ein- und ausgehenden Standby verbunden. Jeder Phase ist in sechs untergeordnete Phasen unterteilt.

**Lp-Phase**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase Energiesparmodus verbringt während der Rückruf Benachrichtigungen für ein- und ausgehenden den Energiesparmodus gesendet werden, um registrierte Treibern und Diensten, die während der Phase PLM oder der Phase DAM nicht angehalten wurden.

**DAM Phase**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase Desktop Aktivität Moderator (DAM) benötigt, während dessen die DAM angehalten oder fortgesetzt, die Ausführung des Benutzer-Sitzung desktop Prozesse.

**PLM Phase**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase Prozess Lebensdauer Manger (PLM) benötigt, während dessen die PLM angehalten oder fortgesetzt, die Ausführung von Windows Store-apps.

**Resiliency Benachrichtigung Phase**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase Resiliency Benachrichtigung verbringt während der sendet der PDC Power Benachrichtigungsereignisse zurück, der angibt, dass es Resiliency als Nächstes wechseln kann.

**Phase der indexverwaltung**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase Wartung verbringt während der zugrunde liegenden Wartungsaktivitäten ausgeführt werden.

**Phase der Verbindung**

Diese Metrik stellt die Zeit in Sekunden, die der Computer in der Phase verbringt, während der Windows filtert Eingabe und remote-Sitzungen behandelt.

## <a name="a-href-idbkmk-idleissuesaissues"></a><a href="" id="bkmk-idleissues"></a>Probleme


Das Assessment verbunden Standby Energie Effizienz führt eine Problemanalyse der erweiterten und enthält Links zu Windows® Performance Analyzer (WPA) von Problemen, die identifiziert werden. WPA möglicherweise zusätzliche Informationen zu dem Datenträger oder CPU-Aktivität je nach den Arten von Problemen, die identifiziert wurden darstellen. Weitere Informationen zu eingehenderen Analysen Probleme und Empfehlungen finden Sie unter, [Häufig auftretender Probleme der Depth-Analyse](common-in-depth-analysis-issues.md).

### <a name="-time-in-lowest-c-state-is-0-for-arm-based-devices"></a>Zeitdauer in Prozent niedrigsten C-Status ist 0 für ARM-basierte Geräte

Bei der Ausführung der Standby verbunden Energie Effizienz Bewertung auf ein ARM-basierten Geräts, wird die-Zeitdauer in Prozent niedrigsten C-Status Metrik als 0 gemeldet. Daten im Zusammenhang eingehalten C-Status-Werte bei der Bewertung Ausführung über Idle Staaten Diagramm in [Windows Performance Analyzer](../wpt/windows-performance-analyzer.md)verfügbar sind.

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Das Assessment Berichte Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Standby Energie-Effizienz verbunden](connected-standby-energy-efficiency.md)

[Erstellen und Ausführen eines Energie Effizienz Auftrags](create-and-run-an-energy-efficiency-job.md)

 

 







