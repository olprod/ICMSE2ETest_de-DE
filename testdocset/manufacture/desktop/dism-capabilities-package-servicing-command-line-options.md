---
author: Justinha
Description: "Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) nur."
ms.assetid: b5f9740e-070c-48c0-9f79-42b25dfeb219
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Funktionen Packen Befehlszeilenoptionen zum Warten
ms.openlocfilehash: 97da6bb10c30114b207ae50641defdb15b43f01f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-iddismcapabilitiespackageservicingcommand-lineoptionsspandism-capabilities-package-servicing-command-line-options"></a><span id="dism_capabilities_package_servicing_command-line_options"></span>DISM Funktionen Packen Befehlszeilenoptionen zum Warten


Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) nur. Verwenden Sie Abbildern Bereitstellung und Verwaltung (DISM.exe), um die Funktionen der Windows-service. Funktionen werden einer Windows Pakettyp-Dienste wie .NET oder Sprachen anfordern, ohne die Angabe der Version ermöglicht. Mithilfe von DISM mehrere Quellen wie Windows Update oder Ihre Unternehmensserver zum Suchen und installieren die neueste Version.

Um die verfügbaren Funktionen finden Sie unter, wechseln Sie zur [Features auf bei Bedarf V2 (Funktionen)](features-on-demand-v2--capabilities.md).

## <a name="span-iddismcommand-lineoptionsspanspan-iddismcommand-lineoptionsspanspan-iddismcommand-lineoptionsspandism-command-line-options"></a><span id="DISM_Command-Line_Options"></span><span id="dism_command-line_options"></span><span id="DISM_COMMAND-LINE_OPTIONS"></span>DISM-Befehlszeilenoptionen


Nachfolgend finden Sie wie jede DISM Option verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

Beachten Sie, dass dieser Befehle erfordert die **/online/Online** oder **/Image:**&lt;*Pfad\_auf\_offline\_Bild\_Datei* &gt; Argument.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Options</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Add-Funktion</strong></p>
<p><strong>/ Name:</strong>&lt;<em>Capability_name</em> &gt; <strong>[/ Source:</strong>&lt;<em>Quelle</em>&gt;<strong>] [/LimitAccess]</strong></p></td>
<td align="left">Fügt eine Funktion zu einem Bild.
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0</code></pre>
<div class="alert">
<strong>Hinweis</strong>  DISM überprüft die Quelldateien in der folgenden Reihenfolge:
<ol>
<li><strong>Wenn/Source</strong> angegeben ist, sieht DISM zuerst an den angegebenen Speicherorten.</li>
<li><strong>Wenn/Source</strong> nicht angegeben ist oder wenn die Quelldateien in den angegebenen Ordnern nicht gefunden werden, überprüft DISM, um festzustellen, ob eine Gruppenrichtlinie festgelegt ist. Wenn dies der Fall, überprüft DISM die durch die Gruppenrichtlinie angegebenen Speicherorte.</li>
<li>Wenn die Dateien noch nicht gefunden, und ob DISM gegen Schwelle online ordnungsgemäß funktioniert und <strong>/LimitAccess</strong> nicht angegeben ist, für die Dateien auf Windows Update sieht.</li>
</ol>
</div>
<div>
 
</div>
<p><strong>/ Source</strong>: ermöglicht es Ihnen, einen Speicherort wie ein Server auszuwählen, in dem sich die Quelldateien Funktion befinden. Sie können <strong>mehrere/Source</strong> Argumente verwenden.</p>
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0 /Source:\\server\share /Source:\\server2\share</code></pre>
<p><strong>/ LimitAccess</strong>: DISM teilt, Windows Update oder Windows Server Update Services für die Funktion Quelldateien nicht überprüft.</p>
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0 /Source:\\server\share /LimitAccess</code></pre></td>
</tr>
<tr class="even">
<td align="left"><strong>/ Get-Funktionen</strong></td>
<td align="left"><p>Profitieren Sie von Funktionen im Bild. Beispiel:</p>
<pre class="syntax" space="preserve"><code>DISM /Online /Get-Capabilities</code></pre></td>
</tr>
<tr class="odd">
<td align="left">/<strong>/ Get-CapabilityInfo/CapabilityName:</strong>&lt;<em>Capability_name</em>&gt;</td>
<td align="left"><p>Abrufen von Informationen zu einer bestimmten Funktion. Beispiel:</p>
<pre class="syntax" space="preserve"><code>DISM /Online /Get-CapabilityInfo
 /CapabilityName:Language.Basic~~~en-US~0.0.1.0</code></pre></td>
</tr>
<tr class="even">
<td align="left"><strong>/ Remove-Funktion</strong>
<p>Zusätzliche Argument erforderlich:</p>
<strong>/ CapabilityName:</strong>&lt;<em>Capability_name_in_image</em>&gt;</td>
<td align="left"><pre class="syntax" space="preserve"><code>Dism /Online /Remove-Capability /Name:Language.Basic~~~en-US~0.0.1.0
Dism /Image:C:\test\offline /Remove-Capability /Name:Language.Basic~~~en-US~0.0.1.0</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Features für Demand V2 (Funktionen)](features-on-demand-v2--capabilities.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[Was ist DISM?](what-is-dism.md)

[DISM globale Optionen für Befehlszeilensyntax](dism-global-options-for-command-line-syntax.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

 

 






