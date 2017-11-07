---
title: Media transcodieren Leistung
description: Media transcodieren Leistung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f5bc0709-7700-444f-860c-b7fc9ec085d0
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 9a6bad15ba5bcae2d9a877b1f10079aa5b73ebe6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="media-transcoding-performance"></a>Media transcodieren Leistung


Das Media transcodieren Performance Assessment misst den Prozess eine Videodatei in ein anderes Format oder Bitrate umgewandelt. Diese Bewertung führt eine Reihe von Operationen, Codierung, die allgemeine Eingabe und Ausgabe-Dateiformate und Auflösung. Weitere Informationen über die Bewertungsergebnisse und Probleme, die gefunden werden können, finden Sie unter [Ergebnisse für die Medien transcodieren Performance-Bewertung](results-for-the-media-transcoding-performance-assessment.md)

Die folgende Abbildung veranschaulicht die Bewertungsprozess.

![Workflow für Medien transcodieren Leistung](images/dep-win8-8-techref-mediatranscodingflow.jpg)

In diesem Thema:

-   [Systemanforderungen](#bkmk-sysreq)

-   [Einstellungen](#assesssettings)

## <a name="a-href-idbkmk-sysreqasystem-requirements"></a><a href="" id="bkmk-sysreq"></a>Systemanforderungen


Die erste Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Führen Sie diese Bewertung nur während der Desktop im Vollbildmodus ist. Diese Bewertung wird nicht ausgeführt, wenn Sie eine andere Windows Store app geöffnet Side-by-Side mit dem Desktop verfügen.

Sie können diese Bewertung unter den folgenden Betriebssystemen ausführen:

-   Windows 8

-   Windows-10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Es gibt zwei Methoden, um diese Bewertung auf Windows RT auszuführen:

-   Packen Sie den Bewertungssauftrag zur in der Windows-Assessment-Konsole und führen sie dann auf Windows RW Weitere Informationen finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services Bewertung auf Windows RW ausgeführt Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>Einstellungen


Standardmäßig verwendet diese Bewertung die empfohlenen Einstellungen. Microsoft definiert diese Einstellungen, damit Sie die Ergebnisse in Computerkonfigurationen mit mehreren oder über einen Zeitraum auf demselben Computer vergleichen können. Wenn Sie die Ergebnisse geprüft haben, enthält die ausführen Informationen Metadaten, die angibt, ob die Bewertung die empfohlenen Einstellungen verwendet.

In der folgenden Tabelle werden die Einstellungen für die Assessment empfohlen, Werte und alternative Werte für jede Einstellung beschrieben.

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
<td><p>Inhaltspfad</p></td>
<td><p>Gibt das Quellverzeichnis für die Mediendateien Codierung an. Standardmäßig ist der Ordner <code>..\content based assessments\Content\Streaming Media Assessment</code>. Verwenden verschiedener Mediendateien können oder anderen lokalen oder Netzwerkordner angeben.</p></td>
</tr>
<tr class="even">
<td><p>Übergeben Sie Testtyp</p></td>
<td><p>Gibt eine Power Option für die Bewertung. Wählen Sie eine der folgenden Optionen aus der Dropdownliste aus. Standardmäßig ist die Option Power auf einem Laptop <strong>Tests auf AC und DC</strong>an.</p>
<ul>
<li><p><strong>Tests auf AC und DC</strong></p></li>
<li><p><strong>Nur auf AC Tests</strong></p></li>
<li><p><strong>Nur auf DC Tests</strong></p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Ergebnisse für die Medien transcodieren Performance-Bewertung](results-for-the-media-transcoding-performance-assessment.md)

[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Bewertung](assessments.md)

 

 







