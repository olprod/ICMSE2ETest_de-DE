---
title: "Windows Media Player-Leistung und Qualität"
description: "Windows Media Player-Leistung und Qualität"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0c0c1485-ab34-42a4-bcc7-690b09b51347
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ab3e4c48ddaa355c67c9dcbb8a71cd3d5f4ec19e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-media-player-performance-and-quality"></a>Windows Media Player-Leistung und Qualität


Die Windows Media Player-Leistung und die Qualität der Bewertung Windows Media Player startet und spielt mehrere Medienclips nach dem anderen. Der Schwerpunkt dieses Assessment ist für die Qualität und Leistung von stabilen Zustand Wiedergabe in Windows Media Player, die die Arbeitslast eines Benutzers ansehen eines Films imitiert wird. Die Ergebnisse, die mit dieser Bewertung helfen Ihnen die Medienwiedergabe Funktionen und Probleme mit der Leistung und Qualität bewerten. Dieses Assessment wird durch Suchvorgänge oder Anhalten Funktionen nicht ausgewertet werden. Weitere Informationen zu den Ergebnissen, die durch diese Bewertung erstellt werden, finden Sie unter [Ergebnisse für die Windows Media Player-Leistung und die Qualität Bewertung](results-for-the-windows-media-player-performance-and-quality-assessment.md).

In der folgenden Grafik veranschaulicht Bewertungsprozess an.

![Workflow-Grafik für Windows MediaPlayer p & q](images/dep-win8-8-techref-wmpassessmentflow.jpg)

In diesem Thema:

-   [Systemanforderungen](#bkmk-systemrequirements)

-   [Einstellungen](#assesssettings)

## <a name="a-href-idbkmk-systemrequirementsasystem-requirements"></a><a href="" id="bkmk-systemrequirements"></a>Systemanforderungen


Bei der Ausführung dieser Bewertung auf Windows 8.1, stellen Sie sicher, dass die Einstellung **Sammeln Analysis Trace** bei der Beurteilung der erwarteten Akkulaufzeit deaktiviert ist. Wenn diese Option aktiviert ist, wird diese Option eine falsche Schätzung erstellt.

Aktivieren Sie Analyse Trace-Auflistung nur, wenn Sie weitere Informationen zum Untersuchen von anderen Probleme im Zusammenhang mit Energie benötigen.

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows 10

Unterstützte Architekturen enthalten X86 und X64-basierte Systeme.

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie können die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

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
<td><p>Inhaltspfad</p></td>
<td><p>Gibt den Quellordner für die Mediendateien. In der Standardeinstellung befindet sich der Ordner unter <code>..\Content\Streaming Media Assessment</code>. Sie können die Mediendateien in den Standardspeicherort verwenden oder geben Sie einen anderen Ordner. Wenn Sie Ihre eigenen Mediendateien angeben, unterstützt die Bewertung die Verwendung von einem Ordner im Netzwerk.</p></td>
</tr>
<tr class="odd">
<td><p>Übergeben Sie Testtyp</p></td>
<td><p>Gibt eine Power Option für die Bewertung. Wählen Sie eine der folgenden Optionen aus der Dropdownliste aus. In der Standardeinstellung ist die Option Power auf einem Laptop <strong>Tests auf AC und DC</strong>.</p>
<ul>
<li><p><strong>Tests auf AC und DC</strong></p></li>
<li><p><strong>Nur auf AC Tests</strong></p></li>
<li><p><strong>Nur auf DC Tests</strong></p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

[Ergebnisse für die Windows Media Player-Leistung und die Qualität Bewertung](results-for-the-windows-media-player-performance-and-quality-assessment.md)

[Media Transcoding-Leistung](media-transcoding-performance.md)

 

 







