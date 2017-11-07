---
title: "Ergebnisse für die Bewertung Out Of-Box-Experience"
description: "Ergebnisse für die Bewertung Out Of-Box-Experience"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CE1CE800-D2DB-41DD-B98E-650E5D676C28
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 9238eccf6542ca89483b22c4284dd6b6f1f3c36f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-out-of-box-experience-assessment"></a>Ergebnisse für die Bewertung Out Of-Box-Experience


Betrifft: Windows 8.1 Windows 10

Diese Bewertung misst die Dauer der wichtigsten Aspekte der ersten Start Experience (OOBE), die normalerweise von Bild Anpassungen und Software Add-ons, die auf das Windows Retail Bild angewendet betroffen sind. Leistung Spuren Event Tracing for Windows (ETW) beim ersten Starten einer Windows-10-System mit gesammelt werden die Maße abgerufen. Die Bewertung misst die Dauer der ersten Anmeldung als auch bestimmte Aspekte wie Active Setup und Installieren der App bereitgestellt.

Dieses Thema hilft Ihnen die interpretiert werden die Ergebnisse von das OOBE Performance Assessment erzeugt. Er enthält außerdem Hinweise zum Verwenden der Ergebnisse zu identifizieren und Beheben von Problemen, die den Eindruck OOBE beeinflussen.

## <a name="metrics"></a>Metriken


Die folgenden Metriken werden durch das OOBE Performance Assessment gemeldet.

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
<td><p>Erste Anmeldung</p></td>
<td><p>Gibt die Zeit in Sekunden, sich anzumelden. Hierbei handelt es sich um die Zeit aus der Benutzer die letzte Eingabe vor der Anmeldung Anfang Wiedergabe bereitstellen, bis auf der Desktop nach Abschluss die Anmeldung-Wiedergabe gestartet wird.</p></td>
</tr>
<tr class="even">
<td><p>Shell-Anmeldung Framework</p></td>
<td><p>Gibt die Zeit in Sekunden des Teils der Anmeldung, in der Shell Framework initialisiert wird.</p></td>
</tr>
<tr class="odd">
<td><p>Active Setup</p></td>
<td><p>Gibt die Zeit in Sekunden des aktiven Setup.</p></td>
</tr>
<tr class="even">
<td><p>Zeitpunkt der bereitgestellten App-Installation</p></td>
<td><p>Gibt die Zeit in Sekunden für den bereitgestellten dienstanwendungen So installieren Sie.</p></td>
</tr>
<tr class="odd">
<td><p>Führen Sie einmal erste Anmeldung-Befehle</p></td>
<td><p>Misst die Zeit in Sekunden, die Ausführung der Ausführung einmal zuerst abschließen Befehle anmelden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="issues"></a>Probleme


Die Leistung der Out Of the Box-Experience kann erheblich beeinträchtigt werden, durch zusätzliche CPU- und Laufwerk e/a-Aktivität Identitätsdaten durch Treiber, Dienste und Anwendungen, die während des Szenarios ausgeführt werden.

Ein empfohlener Ansatz zum Identifizieren der Quellen von Leistungsproblemen in OOBE ist einzelnen Details des Modells dokumentiert in Windows Assessment Toolkit Verwendung sowie die bewährten Methoden befolgen, bei der Sammeln der Ergebnisse von einem System 'Baseline' mit einem Windows-Abbild Retail und Vergleichen von Ergebnissen, die auf einem System "Test" mit einer benutzerdefinierten Windows Bild mit der relevante Erweiterungen und Add-On-Software ist erfassten. Die Bewertungsergebnisse für die zwei Konfigurationen können nebeneinander in Windows Assessment Konsole (WAC) zum Identifizieren der Metriken mit den größten unterschieden verglichen werden. Durch Klicken auf die Links zu den ETW Spuren in WAC angezeigt wird den entsprechende Performance Trace in Windows Performance Analyzer (WPA) angezeigt. WPA Drilldown in die Auslastung CPU und die Datenträgertypen jede Konfiguration verwendet werden kann, und entsprechend die beiden Konfigurationen nebeneinander vergleichen können die Prozesse identifiziert werden, die den größten Deltas in ihrer Verwendung von CPU und Datenträger sichtbar sind.

## <a name="related-topics"></a>Verwandte Themen


[Bewertung](assessments.md)

[Nicht genügend Box-Experience](out-of-box-experience.md)

[Windows-Assessment-Toolkit](index.md)

 

 







