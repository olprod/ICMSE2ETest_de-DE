---
title: "Ergebnisse für die Bewertung Edge Sicherheitsrisiko Software"
description: "Ergebnisse für die Bewertung Edge Sicherheitsrisiko Software"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 47dd67f5-e980-4bb0-a17b-2e4aa241b752
ms.openlocfilehash: ffdb2c74e59809ad059aaa9e53f321a3fc7df6e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-edge-security-software-impact-assessment"></a>Ergebnisse für die Bewertung Edge Sicherheitsrisiko Software


Betrifft: Windows 10

Die Edge-Software Sicherheitsrisiko Assessment Measure Aspekte der Microsoft Edge, die in der Regel von Modul betroffen sind. Die Bewertung misst die Auswirkung auf die Einführung und navigieren Sie Zeiten Microsoft Edge.

In diesem Thema finden Sie die Ergebnisse, die mit der Edge-Software Sicherheitsrisiko Bewertung zu interpretieren.

In diesem Thema:

-   [Metriken](#metrics)

-   [Probleme](#issues)

## <a name="metrics"></a>Metriken


Die folgenden Metriken werden durch die Bewertung Edge Software Sicherheitsrisiko gemeldet.

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
<td><p>Edge, und navigieren Sie zu starten</p></td>
<td><p>Zeit in Millisekunden für die Microsoft Edge Anwendung starten und haben die angeforderte URL verfügbar.</p></td>
</tr>
<tr class="even">
<td><p>Aktivieren der App</p></td>
<td><p>Zeit in Millisekunden für die zu aktivierende Microsoft-Edge-Anwendung.</p></td>
</tr>
<tr class="odd">
<td><p>Registerkarte Erstellen</p></td>
<td><p>Zeit in Millisekunden für die Registerkarte Erstellen in Microsoft Edge.</p></td>
</tr>
<tr class="even">
<td><p>Seite zur Verfügung</p></td>
<td><p>Zeit in Millisekunden für die Seite für den Benutzer sichtbar sein soll.</p></td>
</tr>
<tr class="odd">
<td><p>Nach der Seite Verfügbare durchgearbeitet Laden der Seite</p></td>
<td><p>Zeit in Millisekunden für die Seite vollständig geladen werden, nachdem die Seite sichtbar ist. Präsentieren Sie nur, wenn die Seite verfügbar waren, bevor es vollständig geladen wurde.</p></td>
</tr>
</tbody>
</table>

 

## <a name="issues"></a>Probleme


Ein empfohlener Ansatz zum Identifizieren der Quellen von Leistungsproblemen ist einzelnen Details des Modells dokumentiert in Windows Assessment Toolkit Verwendung sowie die bewährten Methoden befolgen, bei der Sammeln der Ergebnisse von einem System "Baseline" mit einem Windows-Abbild Retail und Vergleichen von Ergebnissen, die auf einem System "Test" mit einer benutzerdefinierten Windows Bild mit der relevante Erweiterungen und Add-On-Software ist erfassten.

Die Bewertungsergebnisse für die zwei Konfigurationen können nebeneinander in Windows Assessment Konsole (WAC) zum Identifizieren der Metriken mit den größten unterschieden verglichen werden. Durch Klicken auf die Links zu den ETW Spuren in WAC angezeigt wird den entsprechende Performance Trace in Windows Performance Analyzer (WPA) angezeigt. WPA Drilldown in die Auslastung CPU und die Datenträgertypen jede Konfiguration verwendet werden kann, und entsprechend die beiden Konfigurationen nebeneinander vergleichen können die Prozesse identifiziert werden, die den größten Deltas in ihrer Verwendung von CPU und Datenträger sichtbar sind.

## <a name="related-topics"></a>Verwandte Themen


[Edge-Software Sicherheitsrisiko](edge-security-software-impact.md)

[Assessment Toolkit technische Referenz zu Windows](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







