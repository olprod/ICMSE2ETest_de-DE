---
title: Windows Performance Toolkit
description: "In dem Windows Assessment and Deployment Kit enthalten, umfasst Windows Performance Toolkit Leistungsüberwachungstools, die detaillierte Leistung Profile von Windows-Betriebssystemen und Anwendungen erzeugt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ef3d3649-4d0e-4207-833c-f58130aca12f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d2951093c53630f877b476afa62f4689c6f4c63f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-performance-toolkit"></a>Windows Performance Toolkit


Enthalten in [Windows Assessment and Deployment Kit](http://go.microsoft.com/fwlink/p/?LinkId=526740), umfasst Windows Performance Toolkit Leistungsüberwachungstools, die detaillierte Leistung Profile von Windows-Betriebssystemen und Anwendungen erzeugt. In dieser Dokumentation werden Windows Performance-Aufzeichnung (WPR) und Windows Performance Analyzer (WPA).

## <a name="windows-performance-toolkit"></a>Windows Performance Toolkit


Windows Performance Toolkit besteht aus zwei unabhängigen Tools: Windows Performance-Aufzeichnung (WPR) und Windows Performance Analyzer (WPA). Darüber hinaus wird die Unterstützung für das vorherige Befehlszeilentool Xperf verwaltet. Xperfview wird jedoch nicht mehr unterstützt. Alle Aufzeichnungen müssen geöffnet und mithilfe von WPA analysiert werden.

Im folgenden sind die Systemanforderungen für die Ausführung von Windows Performance Toolkit:

-   Windows Performance-Aufzeichnung (WPR): Windows 8 oder höher.

-   Windows Performance Analyzer (WPA): Windows 8 oder höher mit Microsoft .NET Framework 4.5 oder höher.

### <a name="windows-performance-recorder"></a>Windows Performance Aufzeichnung

WPR ist eine leistungsstarke Aufzeichnung-Tool, mit dem Event Tracing for Windows (ETW) Aufzeichnungen erstellt. Sie können WPR von der Benutzeroberfläche (UI) oder über die Befehlszeile ausführen. WPR bietet integrierten Profile an, denen Sie verwenden können, um die Ereignisse auszuwählen, die festzuhalten. Alternativ können Sie benutzerdefinierte Profile in XML-DATEI erstellen. WPR kann auch aufgerufen und mithilfe der **WPRControl** Application programming Interface (API) gesteuert. Weitere Informationen zur API WPRControl finden Sie unter [WPRControl-API-Referenz](http://go.microsoft.com/fwlink/p/?linkid=223235).

Grundlegenden Verfahren und eine detaillierte Vorgehensweise finden Sie unter [WPR Quick Start](wpr-quick-start.md). Die vollständige Dokumentation der WPR-UI finden Sie unter [WPR Features](http://go.microsoft.com/fwlink/p/?linkid=223236). Referenz der Befehlszeilenoptionen finden Sie unter [WPR Command-Line Options](http://go.microsoft.com/fwlink/p/?linkid=223233). Schrittweise Anweisungen finden Sie unter [WPR-Hilfethemen](http://go.microsoft.com/fwlink/p/?linkid=223237). Erläuterung der Schlüsselszenarien finden Sie unter [WPR Scenarios](windows-performance-recorder-common-scenarios.md). Vollständiges Referenzmaterial, einschließlich einer Aufzeichnung Profil XML (engl.) und einen legacy Xperf Verweis finden Sie unter [WPR Verweis](http://go.microsoft.com/fwlink/p/?linkid=223245).

### <a name="windows-performance-analyzer"></a>Windows Performance Analyzer

WPA ist eine leistungsstarke Analysetool, das eine sehr flexibel Benutzeroberfläche mit umfangreichen Funktionen Diagrammerstellungsfunktion kombiniert und Datentabellen, pivotiert werden können und für die Volltext-Suchfunktionen. WPA bietet **eine Problemfenster zum Untersuchen der Ursache eines identifiziert** .

Grundlegenden Verfahren und eine detaillierte Vorgehensweise finden Sie unter [WPA Quick Start Guide](wpa-quick-start-guide.md). Die vollständige Dokumentation der WPR-UI finden Sie unter [WPA Features](http://go.microsoft.com/fwlink/p/?linkid=223251). Schrittweise Anweisungen finden Sie unter [WPA Vorgehensweisen Themen](http://go.microsoft.com/fwlink/p/?linkid=223252). Erweiterte Erläuterung von wichtigen Szenarien finden Sie unter [WPA Scenarios](windows-performance-analyzer-common-scenarios.md).

Sie können [Windows Insider Programm](https://insider.windows.com/)besuchen Windows Performance Toolkit herunterladen.

## <a name="contents"></a>Inhalt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Abschnitt</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Was ist neu in Windows Performance Toolkit](whats-new-in-the-windows-performance-toolkit.md)</p></td>
<td><p>Beschreibt die neuen Features in dieser Version verfügbar.</p></td>
</tr>
<tr class="even">
<td><p>[Windows Performance Aufzeichnung](windows-performance-recorder.md)</p></td>
<td><p>Enthält eine vollständige Dokumentation für WPR. Auf der MSDN umfasst dies eine vollständige Referenz für Command-Line und Extensible Markup Language (XML).</p></td>
</tr>
<tr class="odd">
<td><p>[Command-Line Reference Xperf](http://go.microsoft.com/fwlink/?LinkId=234381)</p></td>
<td><p>Bietet Referenzmaterial für Xperf abgeschlossen werden.</p></td>
</tr>
<tr class="even">
<td><p>[Kernel Trace Steuerelement-API-Referenz](kernel-trace-control-api-reference.md)</p></td>
<td><p>Behandelt den Kernel Trace-Steuerelement API eine Erweiterung der ETA Ereignis Tracing-API, die für die Abwärtskompatibilität mit vorhandenen Skripts und Profile unterstützt wird.</p></td>
</tr>
<tr class="odd">
<td><p>[Windows Performance Analyzer](windows-performance-analyzer.md)</p></td>
<td><p>Enthält eine vollständige Dokumentation für WPA, damit Sie Aufzeichnungen mit WPR oder von der Plattform zur Bewertung erstellt analysieren können.</p></td>
</tr>
<tr class="even">
<td><p>[Windows Performance Leitfäden](windows-performance-step-by-step-guides.md)</p></td>
<td><p>Enthält Informationen zum Durchführen der Übungseinheiten das allgemeine Leistung Szenarien aufgelistet.</p></td>
</tr>
</tbody>
</table>

 

 

 






