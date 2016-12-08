---
title: "Ergebnisse für Internet Explorer Security Software Auswirkungen Bewertung"
description: "Ergebnisse für Internet Explorer Security Software Auswirkungen Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: df4ffbd3-69fc-4d3a-b174-c7abe5f13e2d
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 6007d94242f4fcbc0306c73cbe849a64dd28fb07
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-internet-explorer-security-software-impact-assessment"></a>Ergebnisse für Internet Explorer Security Software Auswirkung Bewertung


Internet Explorer Software Auswirkungen Bestandsaufnahme misst Aspekte von Internet Explorer, die in der Regel durch Modul und andere Browser-add-ins beeinflusst werden. Die Bewertung misst die Auswirkungen der Sicherheits-Software auf Anzeigedauer, CPU­Zeit und Ressourcenverwendung von Internet Explorer.

Dieses Thema hilft Ihnen die interpretiert werden die Ergebnisse von Internet Explorer Software Auswirkungen Bestandsaufnahme erzeugt. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und beheben häufig auftretender Probleme, die sich negativ auf die Leistung auswirken.

In diesem Thema:

-   [Ziele-Datei](#bkmk-goals)

-   [Metriken](#bkmk-metrics)

-   [Probleme](#bkmk-issues)

Weitere Informationen zu den Systemanforderungen und Bewertung Einstellungen finden Sie unter [Internet Explorer Software Sicherheitsrisiko](internet-explorer-security-software-impact.md).

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


Die folgenden Metriken werden vom Internet Explorer Software Auswirkungen Bestandsaufnahme gemeldet.

### <a name="page-display-time"></a>Seitenanzeige Zeit

Gibt die Zeit in Millisekunden, die Internet Explorer akzeptiert Startseite Inhalte nach Bewertung navigiert zu der Webseite angezeigt.  Möglicherweise werden zusätzliche Aktivitäten von Internet Explorer aus, nachdem die Seite zu Beginn angezeigt wird, jedoch bevor die Seite vollständig geladen wurde. Seite Anzeigezeit ist eine Teilmenge der Post Seitennavigation.

### <a name="post-page-navigation"></a>POST-Seitennavigation

Ressource: Einsatz wird gemessen, zehn Sekunden, nach die Bewertung auf die Webseite navigiert. POST-Seitennavigation enthält die Seitenanzeige Zeit. Beide Metriken bei Navigation, wie Sie eine URL eingeben, oder klicken auf einen Link zu starten.

![Beide Metriken starten, wenn die Url eingegeben wurde.](images/dep-iessi.png)

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
<td><p>Gesamte CPU-Auslastung</p></td>
<td><p>Zeit in Millisekunden an, die die Seite Auslastung die CPU betroffen.</p></td>
</tr>
<tr class="even">
<td><p>Gesamtverwendung des Datenträgers</p></td>
<td><p>Größe in KB des Speicherplatzes verwendet, um die Webseite zu laden.</p></td>
</tr>
<tr class="odd">
<td><p>Dauer des gesamten Netzwerks</p></td>
<td><p>Zeit in Millisekunden der Dauer des Netzwerkaktivität erforderlich, um die Seite zu laden.</p></td>
</tr>
<tr class="even">
<td><p>Gesamtdauer JavaScript</p></td>
<td><p>Zeit in Millisekunden der Dauer des JavaScript-Modul Aktivität zum Laden der Seite erforderlich sind.</p></td>
</tr>
<tr class="odd">
<td><p>Gesamtlänge des Dokuments Zusammensetzung Dauer</p></td>
<td><p>Zeit in Millisekunden zum Verfassen einer Webseite, einschließlich Anwenden von CSS.</p></td>
</tr>
<tr class="even">
<td><p>Gesamtlänge des Dokuments Renderdauer für Diagramme</p></td>
<td><p>Zeit in Millisekunden zum Rendern von einer Webseite, die geladen wird.</p></td>
</tr>
<tr class="odd">
<td><p>Prozesse</p></td>
<td><p>Anzahl der Prozesse erforderlich, um die Webseite zu laden.</p></td>
</tr>
</tbody>
</table>

 

### <a name="antimalware-products-count"></a>Modul Produkte Count

Die Anzahl der Modul Softwareprodukte installiert auf dem PC.

## <a name="a-href-idbkmk-issuesaissues"></a><a href="" id="bkmk-issues"></a>Probleme


Diese Bewertung führt eine Problemanalyse der erweiterten und enthält Links zu Windows Performance Analyzer (WPA) von Problemen, die identifiziert werden. In den meisten Fällen können Sie klicken Sie auf den Link WPA Analyse, um die Probleme zu beheben, die angezeigt werden. Wenn WPA ausführliche Informationen über die Datenträgeraktivität öffnet oder CPU-Aktivität ist möglicherweise verfügbar, je nach Art des Problems identifiziert. Weitere Informationen zu Problemen eingehenderen Analysen und Empfehlungen finden Sie unter [Häufige Depth Analysis Probleme](common-in-depth-analysis-issues.md).

 

 






