---
author: Justinha
Description: Command-Line Options Copype
ms.assetid: 3342c1d4-7dff-4e0b-ab86-1f28d5057f12
MSHAttr: PreferredLib:/library/windows/hardware
title: Command-Line Options Copype
ms.openlocfilehash: 8562546856e643c64b41c505948ef16f1dabe932
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="copype-command-line-options"></a>Command-Line Options Copype


Das **Copype** Tool erstellt einem Arbeitsverzeichnis, das enthält eine Reihe von Windows Vorinstallation Environment (Windows PE) Dateien. Verwenden Sie diese Dateien zum Anpassen von Bildern und (zusammen mit der **Makewinpemedia** Skript) startbare Medien erstellen. Weitere Informationen finden Sie unter [Makewinpemedia Command-Line Options](makewinpemedia-command-line-options.md).

## <a name="span-idcopypecommand-lineoptionsspanspan-idcopypecommand-lineoptionsspanspan-idcopypecommand-lineoptionsspancopype-command-line-options"></a><span id="Copype_Command-Line_Options"></span><span id="copype_command-line_options"></span><span id="COPYPE_COMMAND-LINE_OPTIONS"></span>Command-Line Options Copype


**Copype** verwendet die folgenden Befehlszeilenoptionen.

**Copype.cmd** Architektur WorkingDirectory

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Befehlszeilenoption</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>Architektur</em></p></td>
<td align="left"><p>Kopiert die Startdateien und Basis Windows PE-Abbild (wird) in <em> &lt;WorkingDirectory&gt;</em>\Media.</p>
<p>Werte enthalten <strong>amd64</strong>, <strong>X86</strong>oder <strong>Arm</strong>.</p>
<p>Die X86 Version von Windows PE kann 32-Bit-UEFI, BIOS-32-Bit- oder 64-Bit-BIOS-basierten PCs starten.</p>
<p>Die amd64-Version von Windows PE kann entweder 64-Bit-BIOS-basierten oder 64-Bit-basierte UEFI-PCs gestartet werden.</p>
<p>Die Arm-Version von Windows PE kann ARM-basierte PCs gestartet werden.</p>
<p>Weitere Informationen zum Ausführen von Windows PE auf PCs mit verschiedenen Architekturen finden Sie unter [Windows-Setup-unterstützte Plattformen und plattformübergreifende-Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md).</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>WorkingDirectory</em></p></td>
<td align="left"><p>Gibt den Namen des Verzeichnisses arbeiten, in dem <strong>Copype</strong> erstellt die Verzeichnisstruktur und kopiert Windows PE-Dateien. Beispiel:</p>
<pre class="syntax" space="preserve"><code>copype amd64 C:\winpe_amd64</code></pre>
<p><strong>Copype</strong> die folgenden Verzeichnisstruktur erstellt.</p>
<pre class="syntax" space="preserve"><code>&lt;WorkingDirectory&gt;
&lt;WorkingDirectory&gt;\media
&lt;WorkingDirectory&gt;\mount</code></pre>
<p>Beim <strong>Copype</strong> kopiert des Basis Windows PE-Bilds zur Darstellung der <em> &lt;WorkingDirectory&gt;</em>\Media\Sources-Ordner wird die Basis-Image aus wird zum Boot.wim umbenannt.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Command-Line Options Makewinpemedia](makewinpemedia-command-line-options.md)

 

 






