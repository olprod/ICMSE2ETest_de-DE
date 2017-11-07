---
author: Justinha
Description: DISM Windows PE Befehlszeilenoptionen zum Warten
ms.assetid: d759221d-47ee-4f50-957e-3b978be22dea
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Windows PE Befehlszeilenoptionen zum Warten
ms.openlocfilehash: da01f2b9a623d8873295be731e6eb558b72257e0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-windows-pe-servicing-command-line-options"></a>DISM Windows PE Befehlszeilenoptionen zum Warten


Bereitstellen ein Abbilds Windows Vorinstallation Environment (Windows PE) und hinzufügen oder Entfernen von Paketen, Treiber und Language Packs mithilfe des entsprechenden Treibers-Paket oder Befehle International zum Warten. Es bestehen auch Befehle, die speziell für ein Windows PE-Abbild zum Vorbereiten der Windows PE-Umgebung, aktivieren Sie ein Profil erstellen, Pakete auflisten und Vorbereiten der Bereitstellung des Windows PE-Abbilds.

**Wichtige**  
Windows PE und möchten präsentieren Funktionalität wurde entfernt Windows 8.1 ab.

 

Die grundlegende Syntax zum Warten eines Abbilds Windows PE wird:

**DISM.exe** **/Image:***&lt;Pfad\_an\_Bild\_Verzeichnis&gt; * \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ * &lt;– Wartung\_Argument&gt; *\]

Zusätzlich zu den Optionen für die Bereitstellung Bild Wartung und Verwaltung (DISM) sind folgenden Windows PE-Wartungsoptionen für ein Image offline verfügbar.

**DISM.exe/Image:** * &lt;Pfad\_an\_Bild\_Verzeichnis&gt; * \[ **/Get-PESettings** | **die Optionen** | **/Get-ScratchSpace** | **/Get-TargetPath** | **/Set-ScratchSpace:***&lt;Größe\_der\_Onlinetreiberinstallation&gt;* | **/Set-TargetPath:***&lt;Ziel\_Pfad&gt;* | **/Enable-Profiling** | **/Disable-Profiling** | **/Apply-Profiles:***&lt;Pfad\_an\_myprofile.txt&gt; *\]

**Wichtige**  
Diese Optionen können nicht mit einer ausgeführte Version von Windows PE verwendet werden. Geben Sie ein Windows PE-Bild mit der **/Image:***&lt;Pfad\_an\_Bild\_Verzeichnis&gt; * Option.

 

Die folgende Tabelle enthält eine Beschreibung für die wie jedes Windows PE-Wartungsoptionen für ein Windows PE-Abbild verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Get-PESettings</strong></p></td>
<td align="left"><p>Zeigt eine Liste der Windows PE-Einstellungen im Windows PE-Abbild an. Die Liste enthält die aktuellen Anwendungsprofil Zustand, Scratch-Speicherplatz-Einstellungen und Ziel Pfad Einstellungen. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Get-PESettings</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Get-Profil</strong></p></td>
<td align="left"><p>Ruft den Status aktiviert/deaktiviert des Windows PE-Tool ein Profil erstellen. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline-Optionen</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get-Onlinetreiberinstallation</strong></p></td>
<td align="left"><p>Ruft den konfigurierten Windows PE System Volume Scratch Abstand. Diese Einstellung stellt den Betrag beschreibbaren verfügbaren Speicherplatz auf dem Systemdatenträger Windows PE, wenn im Ramdisk-Modus gestartet. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /Get-ScratchSpace</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Get-Zielpfad</strong></p></td>
<td align="left"><p>Ruft den Zielpfad des Windows PE-Abbilds ab. Der Zielpfad stellt einen Pfad in den Stamm des Windows PE-Abbild beim Starten. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Get-TargetPath</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Set-Onlinetreiberinstallation:</strong><em>&lt;Größe des sicheren Speicherplatzes&gt;</em></p></td>
<td align="left"><p>Legt den verfügbaren Scratch Speicherplatz in Megabyte fest. Gültige Werte sind 32, 64, 128, 256 und 512. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-ScratchSpace:128</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Set-Zielpfad:</strong><em>&lt;Bereitstellungspfad&gt;</em></p></td>
<td align="left"><p>Für Festplatte Boot-Szenarien legt diese Option den Speicherort des Windows PE-Abbild auf dem Datenträger.</p>
<p>Beachten Sie beim Festlegen des Zielpfad für die folgenden Nachteile:</p>
<ul>
<li><p>Der Pfad muss mindestens drei Zeichen sein und darf nicht mehr als 32 Zeichen</p></li>
<li><p>Der Pfad muss mit einem Buchstaben (einer der Buchstaben von C bis Z) beginnen.</p></li>
<li><p>Der Buchstabe des Laufwerks muss folgen *:\*</p></li>
<li><p>Das restliche Pfad darf keine ungültigen Zeichen, beispielsweise Unicode-Zeichen enthalten.</p></li>
<li><p>Der Pfad muss absolut sein &quot;.&quot; or &quot;..&quot; Elemente</p></li>
<li><p>Der Pfad darf keine Leerzeichen enthalten oder&quot;\\&quot;</p></li>
</ul>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Set-TargetPath:X: \</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Enable-Profil</strong></p></td>
<td align="left"><p>Ermöglicht das Profil (Datei Protokollierung) erstellen, damit Sie eigene Profile erstellen können. Profil ist standardmäßig deaktiviert. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Enable-Profiling</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Disable-Profil</strong></p></td>
<td align="left"><p>Deaktiviert die Protokollierung von Datei, die zum Erstellen eines Profils verwendet wird.</p>
<p><strong>DISM /image:C:\test\offline /Disable-Profiling</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Anwenden Profile:</strong><em>&lt;path_to_myprofile.txt&gt;</em></p></td>
<td align="left"><p><em>&lt;path_to_myprofiles.txt&gt; </em> muss eine durch Kommas getrennte Liste der Profile Dateinamen.</p>
<p>Entfernt alle Dateien aus dem Windows PE-Abbild, die nicht Teil der benutzerdefinierten Profile sind. Es wird überprüft, benutzerdefinierten Profils gegen das Profil CORE, um sicherzustellen, dass benutzerdefinierte Anwendungsdateien und wichtige Dateien nicht gelöscht werden. Ein Windows PE-Abbild, das mit einem Profil angepasst wurde, kann nicht gewartet werden. <strong>Die Optionen</strong>, <strong>/ Get-TargetPath</strong> <strong>und/Get-PESettings</strong> funktioniert jedoch. Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /Apply-Profiles:C:\test\profiles\myprofile.txt</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


Die Befehle Windows PE können nur in Windows PE 3.0 und Windows PE 4.0 Bilder internationale Einstellungen ändern verwendet werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Wpeutil Befehlszeilenoptionen](wpeutil-command-line-options.md)

[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






