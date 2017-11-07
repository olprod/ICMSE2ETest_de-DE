---
title: "Ergebnisse für den Windows Store-app-Performance-Bewertung"
description: "Ergebnisse für den Windows Store-app-Performance-Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1f0cb16e-c4e1-4953-97c3-b20894d6b667
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 91c2511d5d8fd440cd157729c8a8ca189a56e7ca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-windows-store-app-performance-assessment"></a>Ergebnisse für den Windows Store app Performance-Bewertung


Das Windows Store-app Performance Assessment helfen Ihnen Ihre app für eine Steigerung der Kundenzufriedenheit zu optimieren. Die Bewertung misst wie schnell die app wird geöffnet, und hält, und die Größe der Ressourcen auf dem PC verwendet. Können diese Bewertung unterstützen sollen, eine einzelne app zu verbessern oder zur Optimierung von einem Windows-Abbild Berechnung schnelles und flüssiges Zusammenspiel apps, die auch auf Ihrem PC ausgeführt.

In diesem Thema können Sie die Ergebnisse, die mit der Windows Store-app-Performance-Bewertung zu interpretieren. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die die app-Leistung beeinträchtigen.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-metrics)

-   [Probleme](#bkmk-issues)

Weitere Informationen zu den Systemanforderungen und Bewertung Einstellungen finden Sie unter [Windows Store-App-Leistung](windows-store-app-performance.md).

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


Die folgenden Metriken werden durch das Windows Store-app Performance Assessment gemeldet.

### <a name="total-windows-store-apps"></a>Insgesamt Windows Store-apps

Die Anzahl der wie viele Windows Store-apps auf dem Gerät installiert werden.

### <a name="windows-store-apps-assessed"></a>Bewertet Windows Store-apps

Die Anzahl der wie viele Windows Store-apps in der Bewertung enthalten waren.

### <a name="windows-store-app-details"></a>Windows Store-app-details

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Metrisch</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einführung: Warm</p></td>
<td><p>Die Zeit in Millisekunden an, die für die app aus einem angehaltenen Zustand betrachten dauert.</p></td>
</tr>
<tr class="even">
<td><p>Einführung: kalt</p></td>
<td><p>Die Zeit in Millisekunden an, die es, für die app dauert zu öffnen.</p></td>
</tr>
<tr class="odd">
<td><p>Nach der Einführung</p></td>
<td><p>Ressource: Einsatz in den ersten zehn Sekunden nach dem Start der app.</p></td>
</tr>
<tr class="even">
<td><p>Im Leerlauf</p></td>
<td><p>Ressource: Einsatz während die app ohne Interaktion für 30 Sekunden, nach dem Punkt <strong>Post starten</strong> geöffnet ist.</p></td>
</tr>
<tr class="odd">
<td><p>Anhalten</p></td>
<td><p>Die Zeit in Millisekunden, die sich für die app eingeben angehaltenen Zustand dauert.</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idbkmk-issuesaissues"></a><a href="" id="bkmk-issues"></a>Probleme


Diese Bewertung führt eine Problemanalyse der erweiterten und enthält Links zu Windows Performance Analyzer (WPA) von Problemen, die identifiziert werden. In den meisten Fällen können Sie klicken Sie auf den Link WPA Analyse, um die Probleme zu beheben, die angezeigt werden. Wenn WPA ausführliche Informationen über die Datenträgeraktivität öffnet oder CPU-Aktivität ist möglicherweise verfügbar, je nach Art des Problems identifiziert. Weitere Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Depth Analysis Probleme](common-in-depth-analysis-issues.md).

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>Das Assessment Berichte Exit-Code 0x80050006

Dieser Fehler tritt auf, wenn Wartungsaufgaben auf dem PC erfasst wurden, aber nicht vor der Bewertung ausführen abgeschlossen. Dies verhindert, dass die Bewertung von ausgeführt, wie Wartungsaufgaben häufig Assessment Metriken auswirken.

Um dieses Problem zu beheben, führen Sie eine der folgenden Aktionen aus:

1.  Stellen Sie sicher, dass der Computer mit dem Netzwerk verbunden ist und auf Stromversorgung ausgeführt wird. Manuelles Initiieren Sie ausstehende Wartungsaufgaben mit dem folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten:

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  Deaktivieren Sie reguläre und im Leerlauf Wartungsaufgaben und beenden Sie alle Wartungsaufgaben vor der Bewertung wird ausgeführt.

 

 






