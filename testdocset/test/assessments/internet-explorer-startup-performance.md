---
title: Leistung von Internet Explorer zum Starten des
description: Leistung von Internet Explorer zum Starten des
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d20e178a-b38b-4b77-ab3a-d5a3f7518242
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 8f922f8cfe48e7bb164fc0e454a60027e5b25bbf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="internet-explorer-startup-performance"></a>Leistung von Internet Explorer zum Starten des


Die Bewertung der Leistung von Internet Explorer zum Starten des kann Komponenten ermitteln, die Zeit, starten Sie Internet Explorer beeinflussen können. Die Bewertung misst, um ein neues Internet Explorer-Fenster auf dem Desktop mit einem einzelnen Registerkarte und einfacher Inhalte vollständig zu rendern. Diese Messung enthält die Ladezeit der Prozess IExplore.exe und der Frame-Erstellung und Registerkarte Intervallen. Die Bewertung misst auch die Leistung von Erweiterungen, die geladen und während des Starts initialisiert werden. Es wird nicht Netzwerk- oder Leistung beim Durchsuchen messen. Weitere Informationen zu Ergebnisse und Probleme, die diese Bewertung erzeugt, finden Sie unter [Ergebnisse für die Internet Explorer zum Starten des Leistung Bewertung](results-for-the-internet-explorer-startup-performance-assessment.md).

Die Bewertung folgt diesen Workflow:

1.  Erstellt eine benutzerdefinierte lokale Seite, die Ihnen mitgeteilt wird, dass die Bewertung ausgeführt wird und weist Sie nicht für die Interaktion mit dem computer

2.  Bereitet für Protokollanalysetool und metrische-Auflistung

3.  Internet Explorer und startet das Erfassen von Metriken

**Hinweis**  
Die Bewertung startet Internet Explorer 4-Mal. Beim ersten ist eine Schulung Iteration, und die nächsten 3 sind Timing Iterationen. Die Schulung Iteration wird sichergestellt, dass Timing Iterationen aus dem Systemcache und nicht betriebsbereiter beginnen laden. Die Ergebnisse, die erstellt werden, sind aggregierte Ergebnisse aus der Iterationen Timing an. Sie können die Anzahl der Timing Iterationen in den Einstellungen zur Bewertung ändern.

 

In der folgenden Grafik veranschaulicht Bewertungsprozess an.

![für die Leistung von Internet Explorer zum Starten des Workflows](images/dep-win8-8-techref-ielaunchflow.jpg)

In diesem Thema:

-   [Systemanforderungen](#sysrqrmts)

-   [Einstellungen](#assesssettings)

## <a name="a-href-idsysrqrmtsasystem-requirements"></a><a href="" id="sysrqrmts"></a>Systemanforderungen


Der ersten Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Führen Sie diese Bewertung nur während der Desktop im Vollbildmodus ist. Diese Bewertung kann nicht ausgeführt werden, wenn Sie eine andere Windows Store-app geöffnet-nebeneinander mit dem Desktop haben.

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows 10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Es gibt zwei Methoden zur Ausführung dieses Assessment in Windows RT:

-   Packen Sie den Assessment Auftrag in der Windows-Assessment-Konsole und führen sie dann auf Windows RW Weitere Informationen finden Sie unter [Packen Sie einen Auftrag verwenden und es auf einem anderen Computer ausführen](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausführen Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie können die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

Sie können die Einstellungen auch anpassen, wenn zum Erfassen von Daten, die unterscheidet sich von was die Bewertung standardmäßig erfasst werden soll. Beispielsweise können Sie Daten zu beschreiben, in denen Sie eine detaillierte Analyse eines bestimmten Aspekts des Computers ausführen werden.

In der folgenden Tabelle wird beschrieben, die Einstellungen für die Bewertung empfohlene Werte und alternative Werte für jede Einstellung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Empfohlene Einstellungen verwenden</p></td>
<td><p>Gibt an, ob die Bewertung die empfohlenen Einstellungen verwendet wird. Standardmäßig ist dieses Kontrollkästchen aktiviert. Um die Einstellungen für die Bewertung zu ändern, müssen Sie zunächst dieses Kontrollkästchen deaktivieren.</p></td>
</tr>
<tr class="even">
<td><p>Iterationen</p></td>
<td><p>Gibt die Anzahl der Male, dass die Bewertung Internet Explorer gestartet wird. Standardmäßig ist der Wert 4. Zum ersten Mal wird immer eine Schulung Iteration, und die nächsten 3 Timing Iterationen sind. Die Schulung Iteration wird sichergestellt, dass die Anzeigedauer Iterationen aus dem Systemcache und nicht betriebsbereiter beginnen laden. Die Ergebnisse, die erstellt werden, sind aggregierte Ergebnisse aus der Timing-Iterationen.</p></td>
</tr>
<tr class="odd">
<td><p>Alternative WPR Profil verwenden</p></td>
<td><p>Gibt eine Alternative zu verwendende Profil für Windows® Leistung Aufzeichnung (WPR). Die Bewertung verwendet das WPR-Tool zum Erstellen einer Ablaufverfolgungs. Sie können das Standardprofil verwenden, das bereitgestellt wird, oder geben Sie einen Pfad zu einem anderen Profil.</p>
<p>Um ein alternativer-Profil angeben möchten, aktivieren Sie das Kontrollkästchen <strong>Alternative WPR Profil verwenden</strong> , und geben Sie den Pfad im Feld <strong>Pfad alternative Profil</strong> . Das Tool Windows Performance Analyzer (WPA) können Sie anzeigen oder die Ablaufverfolgungsdatei analysieren.</p></td>
</tr>
<tr class="even">
<td><p>Pfad zur alternativen Profil (.wprp)</p></td>
<td><p>Gibt den Pfad zu einem anderen Windows Performance Aufzeichnung (WPR)-Profil. Nur, wenn Sie das Kontrollkästchen <strong>Alternative WPR Profil verwenden</strong> , ist diese Einstellung aktiviert.</p></td>
</tr>
<tr class="odd">
<td><p>Minifilter Diagnosemodus aktivieren</p></td>
<td><p>Gibt an, ob die Diagnose Minifilter-Option verwendet. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Wenn Minifilter Diagnosemodus aktiviert ist, generiert er Metriken, die Ihnen helfen bewerten die Auswirkungen der Minifilter beim Start von Internet Explorer. Weitere Informationen zu dieser Einstellung finden Sie unter [Minifilter Diagnose](minifilter-diagnostics.md).</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Internet Explorer zum Starten des Performance-Bewertung](results-for-the-internet-explorer-startup-performance-assessment.md)

[Bewertung](assessments.md)

 

 







