---
author: Justinha
Description: "DISM globale Optionen für Befehlszeilensyntax"
ms.assetid: b902ff42-6718-48ca-878b-f3824d3229d4
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM globale Optionen für Befehlszeilensyntax"
ms.openlocfilehash: cb9563c0f2a1692dd494d48b468b4dbb6f93f61d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-global-options-for-command-line-syntax"></a>DISM globale Optionen für Befehlszeilensyntax


Globale Optionen können die meisten Optionen zum Warten und imaging im Tool Deployment Image Servicing and Management (DISM) hinzugefügt werden. Diese Optionen können der Command-Line-Hilfe, geben Sie den Speicherort der Dateien verwenden und Protokollierung verwendet werden.

## <a name="span-idbasicsyntaxforservicingcommandsspanspan-idbasicsyntaxforservicingcommandsspanspan-idbasicsyntaxforservicingcommandsspanbasic-syntax-for-servicing-commands"></a><span id="Basic_Syntax_for_Servicing_Commands"></span><span id="basic_syntax_for_servicing_commands"></span><span id="BASIC_SYNTAX_FOR_SERVICING_COMMANDS"></span>Grundlegende Syntax für die Wartung von Befehlen


Nachdem die eingebunden oder ein Bild Windows® angewendet, sodass sie verfügbar ist offline als Flatfile-Struktur, können Sie angeben, DISM globalen Optionen, die Wartungsoptionen, das das Bild und den Speicherort des Bilds offline aktualisiert wird. Sie können nur eine Wartungsoptionen pro Befehlszeile verwenden.

Wenn Sie einen ausgeführten Computer warten, können Sie die **Option/Online** anstelle des Speicherorts des offline Windows-Abbilds verwenden. Die Befehle und die verfügbaren Optionen für die Wartung eines Abbilds abhängen, die welches Windows-Betriebssystem bedienen. Sie hängen auch, ob das Bild offline ist oder einem ausgeführten Betriebssystem. Alle Befehle arbeiten Schwelle Windows offline. Teilmenge der Befehle sind zum Warten eines ausgeführten Betriebssystems zur Verfügung.

Die grundlegende Syntax für DISM zum Warten Befehle ist:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_Bild*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Weitere Informationen zur Wartung Befehle finden Sie unter [Deployment Image Servicing and Management (DISM) Command-Line Options](deployment-image-servicing-and-management--dism--command-line-options.md).

## <a name="span-idbasicsyntaxforimagingcommandsspanspan-idbasicsyntaxforimagingcommandsspanspan-idbasicsyntaxforimagingcommandsspanbasic-syntax-for-imaging-commands"></a><span id="Basic_Syntax_for_Imaging_Commands"></span><span id="basic_syntax_for_imaging_commands"></span><span id="BASIC_SYNTAX_FOR_IMAGING_COMMANDS"></span>Grundlegende Syntax für Imaging Befehle


Viele der globalen Optionen sind auch für imaging Befehle zur Verfügung. Die grundlegende Syntax für DISM imaging Befehle ist:

**DISM.exe** \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Weitere Informationen zur Verwendung von DISM für wie anwenden oder Bereitstellen eines Abbilds des Image-Verwaltung finden Sie unter [Befehlszeilenoptionen für DISM Bild Management](dism-image-management-command-line-options-s14.md).

## <a name="span-idglobaloptionsforservicingandimagingcommandsspanspan-idglobaloptionsforservicingandimagingcommandsspanspan-idglobaloptionsforservicingandimagingcommandsspanglobal-options-for-servicing-and-imaging-commands"></a><span id="Global_Options_for_Servicing_and_Imaging_Commands"></span><span id="global_options_for_servicing_and_imaging_commands"></span><span id="GLOBAL_OPTIONS_FOR_SERVICING_AND_IMAGING_COMMANDS"></span>Globale Optionen für die Wartung und Imaging Befehle


Die folgenden globalen DISM-Optionen stehen für ein offline-Abbild.

**DISM.exe /image:**&lt;*path\_to\_offline\_image\_directory*&gt; \[**/WinDir:**&lt;*path\_to\_%WINDIR%*&gt;\] \[**/LogPath:**&lt;*path\_to\_log\_file.log*&gt;\] \[**/LogLevel:**&lt;n&gt;\] \[**/SysDriveDir:**&lt;*path\_to\_bootMgr\_file*&gt;\] \[**/Quiet**\] \[**/NoRestart**\] \[**/ScratchDir:**&lt;*path\_to\_scratch\_directory*&gt;\] \[**/English**\] \[ **/Format:**&lt;*Ausgabe\_Format* &gt;\]

Die folgenden globalen DISM-Optionen stehen für ein Betriebssystem ausgeführt wird.

**DISM.exe / online** \[**/LogPath:**&lt;*path\_to\_log\_file*&gt;\] \[**/LogLevel:**&lt;*n*&gt;\] \[**/SysDriveDir:**&lt;*path\_to\_bootMgr\_file*&gt;\] \[**/Quiet**\] \[**/NoRestart**\] \[**/ScratchDir:**&lt;*path\_to\_scratch\_directory*&gt;\] \[**/English**\] \[**/Format:**&lt;*output\_format*&gt;\]

Die folgende Tabelle enthält eine Beschreibung des wie jede globale DISM-Option verwendet werden kann. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Globale option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Get-Help</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>Zeigt Informationen zu den verfügbaren DISM-Befehlszeilenoptionen und Argumente.</p>
<p>Verwendung der <strong>/?</strong> <strong>/Get-Help</strong> Option oder ohne Angabe einer Bilddatei, erhalten Sie Hilfe zu Management-Befehle wie <strong>/Mount-Image</strong>Bild.</p>
<p>Beispiel:</p>
<p><strong>DISM /?</strong></p>
<p>Geben Sie eine Image-Datei mit der <strong>/Image:</strong>&lt;<em>Path_to_an_image</em> &gt; option oder mithilfe der <strong>Option/Online</strong> erhalten Sie Hilfe zu Befehls zum Warten in das <strong>Bild/Get-Packages</strong>. Die verfügbaren Optionen zum Warten eines Abbilds hängen die Wartung Technologie, die in Ihrem Bild verfügbar ist.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /?</strong></p>
<p><strong>DISM / online /?</strong></p>
<p>Sie können zusätzliche Hilfe anzeigen, indem Sie eine Befehlszeilenoption angeben.</p>
<p>Beispiel:</p>
<p><strong>/ Add DISM-/image:C:\test\offline Driver /?</strong></p>
<p><strong>DISM /image:C:\test\offline/Add-Package /?</strong></p>
<p><strong>DISM / online/Get-Drivers /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ LogPath:</strong>&lt;<em>Pfad_zur_Protokolldatei.log</em>&gt;</p></td>
<td align="left"><p>Gibt den vollständigen Pfad und Namen zur Anmeldung bei. Wenn kein Wert festgelegt, der Standardwert ist: <strong>%WINDIR%\Logs\Dism\dism.log</strong></p>
<div class="alert">
<strong>Wichtige</strong>  
<p>In Windows PE ist das Standardverzeichnis der RAMDISK Scratch-Speicherplatz, der so niedrig wie 32 MB sein kann.</p>
<p>Die Protokolldatei wird automatisch archiviert werden. Die archivierte Protokolldatei wird mit bak an den Dateinamen angefügt gespeichert und eine neue Protokolldatei generiert werden. Jedes Mal die Protokolldatei ist der BAK archiviert Datei überschrieben werden.</p>
</div>
<div>
 
</div>
<p>Wenn Sie eine Netzwerkfreigabe verwenden, die nicht Mitglied einer Domäne ist, verwenden Sie den Befehl <strong>net Use</strong> zusammen mit Domänenanmeldeinformationen Zugriffsberechtigungen festlegen, bevor Sie den Protokollpfad für das DISM-Protokoll festlegen aus.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /LogPath:AddPackage.log/Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ LogLevel:</strong>&lt;<em>n</em>&gt;</p></td>
<td align="left"><p>Gibt die maximale Ausgabe in den Protokollen angezeigt. Die standardmäßige Protokollierungsstufe ist 3. Die zulässigen Werte sind wie folgt:</p>
<p>1 = nur Fehler</p>
<p>2 = Fehler und Warnungen</p>
<p>3 = Fehler, Warnungen, und Informationszwecken</p>
<p>4 = alle oben aufgeführten Informationen sowie Debugausgabe</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /LogPath:AddPackage.log /LogLevel:1/Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Bild:</strong>&lt;<em>Pfad_zum_Offlineabbildverzeichnis</em>&gt;</p></td>
<td align="left"><p>Dies ist der vollständige Pfad zum Stammverzeichnis des offline Windows-Abbilds Ihnen gewartet wird. Wenn das Verzeichnis mit dem Namen Windows kein Unterverzeichnis des Stammverzeichnisses ist, muss <strong>die/windir</strong> angegeben werden.</p>
<p>Diese Option kann nicht <strong>mit/Online</strong>verwendet werden.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /LogPath:AddPackage.log /LogLevel:1/Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Windir%:</strong>&lt;<em>Pfad_zu_ % WINDIR%</em>&gt;</p></td>
<td align="left"><p>Mit der <strong>Option/Image</strong> verwendet, um den Pfad zum Windows-Verzeichnis relativ zum Pfad Bildes anzugeben. Dies kann nicht den vollständigen Pfad zum Windows-Verzeichnis sein. Es sollte ein relativer Pfad sein. Wenn nicht angegeben, ist die Standardeinstellung der Windows-Verzeichnis in den Stamm des Verzeichnisses offline-Abbild.</p>
<p>Diese Option kann nicht mit der <strong>Option/Online</strong> verwendet werden.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /WinDir:WinNT/Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Online</strong></p></td>
<td align="left"><p>Gibt an, dass die Aktion unter dem Betriebssystem getroffen werden, die derzeit ausgeführt wird.</p>
<p>Diese Option kann nicht mit der <strong>/image/Image</strong> oder die <strong>Option/windir</strong> verwendet werden. <strong>Wenn/Online</strong> verwendet wird, wird das Windows-Verzeichnis für das Bild online automatisch erkannt.</p>
<p>Beispiel:</p>
<p><strong>DISM / online/Get-Packages</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ SysDriveDir:</strong>&lt;<em>Path_to_sysdrive_directory</em>&gt;</p></td>
<td align="left"><p>Verwenden Sie <strong>/SysDriveDir</strong> , um eine installierte Windows-Abbild aus einer Windows PE-Umgebung.</p>
<p>Die Option <strong>/SysDriveDir</strong> gibt den Pfad zum Speicherort der BootMgr-Dateien. Dies ist erforderlich, nur, wenn die BootMgr-Dateien auf einer anderen als der Partition befinden, die Sie den Befehl ausführen.</p>
<p>Geben Sie zum Beispiel an einer Eingabeaufforderung Windows PE:</p>
<p><strong>DISM /image:C:\Windows /SysDriveDir:C: \</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Quiet</strong></p></td>
<td align="left"><p>Informationen und Fortschritt Ausgabe in der Konsole deaktiviert. Nur Fehlermeldungen werden angezeigt.</p>
<p>Wenn im stillen Modus ausgeführt werden soll, muss diese Option jedes Mal festlegen, die das Befehlszeilenprogramm ausgeführt wird.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Verwenden Sie die <strong>Option/Quiet</strong> nicht <strong>mit/Get</strong> -Befehle. Es werden keine Informationen wird angezeigt.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline/Add-Package /PackagePath:C:\packages\package.cab/quiet</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ NoRestart</strong></p></td>
<td align="left"><p>Neustart unterdrückt. Wenn ein Neustart des Computers nicht erforderlich ist, führt diesen Befehl keine Aktion. Diese Option wird lassen Sie die Anwendung zu einem Neustart aufgefordert (oder verhindern, dass Sie einen Neustart automatisch, wenn die <strong>Option/Quiet</strong> verwendet wird).</p>
<p>Beispiel:</p>
<p><strong>DISM / online/Add-Package /PackagePath:C:\packages\package.cab/norestart/quiet</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ScratchDir:</strong>&lt;<em>Path_to_scratchdirectory</em>&gt;</p></td>
<td align="left"><p>Gibt ein temporäres Verzeichnis, das beim Extrahieren der Dateien für die temporäre Verwendung während der Wartung verwendet werden. Das Verzeichnis muss lokal vorhanden sein. Falls nicht angegeben, das \Windows\-Verzeichnis<em>%Temp%</em> , mit dem Unterverzeichnisnamen willkürlich generierten Hexadezimalwert für die Ausführung von DISM verwendet wird. Elemente in das Verzeichnis Scratch werden nach jedem Vorgang gelöscht.</p>
<p>Sie sollten einen Speicherort der Netzwerkfreigabe als Scratch Verzeichnis nicht verwenden, um ein Paket (CAB-Dateien oder MSU-Datei) für die Installation zu erweitern. Der Ordner zum Extrahieren der Dateien für die temporäre Verwendung während der Wartung sollte ein lokales Verzeichnis.</p>
<p>Beispiel:</p>
<p><strong>DISM /image:C:\test\offline /ScratchDir:C:\Scratch/Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Englisch</strong></p></td>
<td align="left"><p>Zeigt die Befehlszeilenausgabe in Englisch.</p>
<div class="alert">
<strong>Hinweis</strong>  
<p>Einige Ressourcen können nicht in Englisch angezeigt werden.</p>
<p>Diese Option wird nicht unterstützt, wenn Sie verwenden die <strong>DISM /?</strong> Befehl.</p>
</div>
<div>
 
</div>
<p>Beispiel:</p>
<p><strong>DISM /Get-ImageInfo /ImageFile:C:\test\offline\install.wim/Index: 1 /English</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Formatieren: {Tabelle | Liste}</strong></p></td>
<td align="left"><p>Gibt das Ausgabeformat für den Bericht an.</p>
<p>Beispiel:</p>
<p><strong>DISM /Image:C:\test\offline Get-Apps /Format:Table</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[DISM Anwendung Befehlszeilenoptionen zum Warten](dism-application-servicing-command-line-options.md)

[DISM Windows Edition zum Warten von Befehlszeilenoptionen](dism-windows-edition-servicing-command-line-options.md)

[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)

[Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)

[DISM unbeaufsichtigte Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

[DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md)

 

 






