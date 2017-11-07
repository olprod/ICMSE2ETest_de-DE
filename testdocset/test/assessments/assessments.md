---
title: Bewertung
description: Bewertung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 23640a08-1459-4676-a522-daf8bbc49c7d
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 320f504a72d4de296124113ec9c394cb0233714f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="assessments"></a>Bewertung


Bewertung werden eine Kombination von XML und Binärdateien, die Auslösen von eines bestimmten Satz von Status auf einem Computer, messen und die Aktivität Datensatz, und die aufgezeichneten Ergebnisse zu erhalten. Die Ergebnisse enthalten Metriken und in einigen Fällen Empfehlungen für das Beheben von Problemen, die die Bewertungsfragen gefunden. Bewertung unterstützen Sie bei bewerten, Hardware und Software, die auf einem Computer hinzugefügt wurde.

Bewertung und die Windows-Konsole Assessment stehen im Rahmen des Windows Assessment Toolkit, das in dem Windows Assessment and Deployment Kit (Windows ADK) verfügbar ist. Nach der Installation des Windows Assessment Toolkit können Sie die Assessment Windows-Konsole verwenden, erstellen und Ausführen eines Auftrags, das eine oder mehrere Analysen enthält. Sie können auch Packen Aufträge, um diese auf Computern ausführen, die das Windows Assessment Toolkit installiert haben.

Bewertung stehen ebenfalls zur Verfügung, wenn Sie Windows Assessment und die Windows-Assessment-Dienste - Client (Windows ASC) installieren.

Dieses Diagramm zeigt den allgemeinen Workflows für eine Bewertung:

![Workflow-Grafik zur Bewertung](images/dep-win8-adk-assessmentoverviewflowchart.jpg)

## <a name="in-this-section"></a>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>[Verbundene Standby Energie-Effizienz](connected-standby-energy-efficiency.md)</p></td>
<td><p>Diese Bewertung misst wirken sich die Software und Geräte an, für die Akkulaufzeit eines Systems, während sie im Standbymodus verbunden ist. Die Bewertung misst auch die aufgewendete Zeit Übergang in und aus dem Standbymodus verbunden.</p></td>
</tr>
<tr class="even">
<td><p>[Überprüfung der Treiber](driver-verification.md)</p></td>
<td><p>Diese Bewertung überprüft, ob ein offline-Windows-Abbild oder einem ausgeführten Windows-Betriebssystem die korrekte Liste der Treiber enthält.</p></td>
</tr>
<tr class="odd">
<td><p>[Edge Security Software Auswirkungen](edge-security-software-impact.md)</p></td>
<td><p>Diese Bewertung misst Aspekte der Microsoft Edge, die in der Regel von Modul betroffen sind. Die Bewertung misst die Auswirkung auf die Einführung und navigieren Sie Zeiten Microsoft Edge.</p></td>
</tr>
<tr class="even">
<td><p>[Dateiverarbeitung durch den](file-handling.md)</p></td>
<td><p>Diese Bewertung simuliert Dateivorgänge wie kopieren, verschieben, komprimieren, dekomprimieren und Löschen von Dateien. Auch gemessen Dauer und Durchsatz für Ihnen zum Auswerten der Leistung des Computers.</p></td>
</tr>
<tr class="odd">
<td><p>[Leistung von Internet Explorer zum Starten des](internet-explorer-startup-performance.md)</p></td>
<td><p>Diese Bewertung misst, um eine leere Seite in Internet Explorer vollständig zu rendern. Diese Messung enthält die Ladezeit der Prozess IExplore.exe und der Frame-Erstellung und Registerkarte Intervallen. Es misst auch die Auswirkung des alle Erweiterungen, Add-Ins und Symbolleisten, die auf dem System installiert sind. Es wird keine Netzwerk- oder Browser-Leistung gemessen.</p></td>
</tr>
<tr class="even">
<td><p>[Internet Explorer Software Sicherheitsrisiko](internet-explorer-security-software-impact.md)</p></td>
<td><p>Diese Bewertung misst Aspekte von Internet Explorer, die von Modul und andere Browser-add-ins in der Regel betroffen sind.</p></td>
</tr>
<tr class="odd">
<td><p>[Lokale Videowiedergabe](local-video-playback.md)</p></td>
<td><p>Diese Bewertung misst die Anzahl der Batterie des Computers für die Verwendung während des ganzen Bildschirms lokale Videowiedergabe.</p></td>
</tr>
<tr class="even">
<td><p>[Media Transcoding-Leistung](media-transcoding-performance.md)</p></td>
<td><p>Diese Bewertung misst die Codierung Dauer und die relative Geschwindigkeit eine Videodatei in ein anderes Format oder Bitrate umgewandelt.</p></td>
</tr>
<tr class="odd">
<td><p>[Speicherbedarf](memory-footprint.md)</p></td>
<td><p>Diese Bewertung erstellt eine Momentaufnahme der Speicherverwendung während der eine Reihe von Systemstart. Sie können dann Möglichkeiten zur Verbesserung von Leistung und Effizienz durch Optimieren der Speicherverwendung zu identifizieren. Dieser Assessment können auch um eine geplante Betriebssystemabbilds gegen Schwelle Original Equipment Manufacturer (OEM) zu vergleichen.</p></td>
</tr>
<tr class="even">
<td><p>[Minifilter Diagnose](minifilter-diagnostics.md)</p></td>
<td><p>Beschreibt die Diagnose Minifilter-Einstellung, die in verschiedene Bewertung verfügbar ist. Die Diagnose Minifilter Einstellung können Sie messen die Zeit, die der Computer im Minifilter Vorgänge verbringt identifizieren und Minifilter Treiber ineffiziente, mithilfe viel Arbeitsspeicher, oder nicht funktionsfähig.</p></td>
</tr>
<tr class="odd">
<td><p>[Ein-/ausschalten Übergang Leistung](onoff-transition-performance.md)</p></td>
<td><p>Beschreibt die Systemanforderungen, Assessment-Einstellungen, Ergebnisse und Probleme, die der Start-Leistung (Fast Start), Ruhezustand Leistung und Standby-Leistung Bewertung zugeordnet sind. Bei Ihrer Bewertung misst den Übergang vom Computer mit verschiedenen Status.</p></td>
</tr>
<tr class="even">
<td><p>[Nicht genügend Box-Experience](out-of-box-experience.md)</p></td>
<td><p>Diese Bewertung misst die Dauer der wichtigsten Aspekte der ersten Start Experience (OOBE), die in der Regel von Bild Anpassungen und Software Add-ons, die auf das Windows Retail Bild angewendet betroffen sind. Die Bewertung misst die Dauer der ersten Anmeldung als auch bestimmte Aspekte wie Active Setup und Installieren der App bereitgestellt.</p></td>
</tr>
<tr class="odd">
<td><p>[Streaming Media-Leistung](streaming-media-performance.md)</p></td>
<td><p>Dieser Assessment Datenströme Media in Internet Explorer mithilfe von Videoinhalten liegt, die aus niedriger Auflösung und hoher Auflösung. Dann wird die Qualität der Videowiedergabe basierend auf der Anzahl der Fehler, die Geräte-ausgewertet.</p></td>
</tr>
<tr class="even">
<td><p>[Windows Media Player-Leistung und Qualität](windows-media-player-performance-and-quality.md)</p></td>
<td><p>Diese Bewertung wertet die Leistung und die Qualität der Wiedergabe von Windows Media® Player und wird in einer Reihe von multimedia Akkulaufzeit Bewertung.</p></td>
</tr>
<tr class="odd">
<td><p>[Windows Store-App-Leistung](windows-store-app-performance.md)</p></td>
<td><p>Diese Bewertung helfen Ihnen Ihre app für eine Steigerung der Kundenzufriedenheit optimieren.</p></td>
</tr>
<tr class="even">
<td><p>[Häufige Probleme von eingehenderen Analysen](common-in-depth-analysis-issues.md)</p></td>
<td><p>Beschreibt allgemeine eingehenderen Analysen Probleme, die Sie in der Windows-Konsole zur Bewertung anzeigen und weiteren Analyse in Windows® Performance Analyzer (WPA).</p></td>
</tr>
<tr class="odd">
<td><p>[Problembehandlung bei der Bewertung](troubleshooting-assessments-wac.md)</p></td>
<td><p>Beschreibt allgemeine Probleme, die dazu führen, dass bei der Bewertung zu einem Importfehler führen.</p></td>
</tr>
</tbody>
</table>

 

 

 






