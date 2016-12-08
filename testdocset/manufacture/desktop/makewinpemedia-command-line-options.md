---
author: Justinha
Description: Command-Line Options Makewinpemedia
ms.assetid: b3fc26e8-96a0-4fca-9678-ac895835b7e0
MSHAttr: PreferredLib:/library/windows/hardware
title: Command-Line Options Makewinpemedia
ms.openlocfilehash: 1801c235255c49c44a8b8b92b20349902c3f8c74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="makewinpemedia-command-line-options"></a>Command-Line Options Makewinpemedia


Das Tool **Makewinpemedia** ist neu in Windows 8. **Makewinpemedia** können Sie das startbare Windows Vorinstallation Environment (Windows PE) Medien erstellen. Ausführen des Tools **Copype** ist eine Voraussetzung für das startbare Medien erstellen. **Copype** erstellt eine Verzeichnisstruktur für Windows PE-Dateien und die erforderlichen Windows PE Mediendateien kopiert. Weitere Informationen finden Sie unter [Command-Line Options Copype](copype-command-line-options.md) und [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

## <a name="span-idmakewinpemediacommand-lineoptionsspanspan-idmakewinpemediacommand-lineoptionsspanspan-idmakewinpemediacommand-lineoptionsspanmakewinpemedia-command-line-options"></a><span id="Makewinpemedia_Command-Line_Options"></span><span id="makewinpemedia_command-line_options"></span><span id="MAKEWINPEMEDIA_COMMAND-LINE_OPTIONS"></span>Command-Line Options Makewinpemedia


Das **Makewinpemedia** -Tool verwendet die folgenden Befehlszeilenoptionen.

**Makewinpemedia** {*/ufd* | */iso*} \[ */f* \] * &lt;WorkingDirectory&gt; &lt;DestinationLocation&gt; *

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
<td align="left"><p><strong>/UFD</strong></p></td>
<td align="left"><p>Gibt an, ein USB-Flashlaufwerk als den Typ von Medien zu erstellen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /ufd C:\winpe_amd64 F:</code></pre>
<p>wobei F der Laufwerkbuchstabe des USB flash-Laufwerk ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ISO</strong></p></td>
<td align="left"><p>Gibt eine ISO-Datei (CD- oder DVD) als den Typ von Medien zu erstellen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /iso C:\winpe_amd64 C:\winpe_x64\winpe_amd64.iso</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ f</strong></p></td>
<td align="left"><p>Optional Unterdrückt die bestätigungsmeldung, die angezeigt wird, vor dem format USB flash-Laufwerk oder eine vorhandene ISO-Datei überschreiben. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /ufd /f C:\winpe_amd64 F:</code></pre>
<p>wobei F der Laufwerkbuchstabe des USB flash-Laufwerk ist.</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;WorkingDirectory&gt;</em></p></td>
<td align="left"><p>Gibt den Namen des Verzeichnisses arbeiten, in dem das <strong>Copype</strong> Tool erstellt die Windows PE Verzeichnisstruktur und kopiert die erforderlichen Dateien für das startbare Medien erstellen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>C:\winpe_amd64</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;DestinationLocation&gt;</em></p></td>
<td align="left"><p>Gibt an, wenn Sie die Option <strong>/ufd</strong> oder den Namen der ISO-Datei verwenden, wenn Sie die Option <strong>/iso</strong> verwenden der Laufwerkbuchstabe des USB flash-Laufwerk.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[Oscdimg Befehlszeilenoptionen](oscdimg-command-line-options.md)

 

 






