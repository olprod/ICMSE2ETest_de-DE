---
author: Justinha
Description: BCDBoot Befehlszeilenoptionen
ms.assetid: 294a0181-f3e9-42c1-8e7f-5a5c28323e25
MSHAttr: PreferredLib:/library/windows/hardware
title: BCDBoot Befehlszeilenoptionen
ms.openlocfilehash: 0c87080c867c883d9a7950e921e02e92938d2e2c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bcdboot-command-line-options"></a>BCDBoot Befehlszeilenoptionen


BCDBoot ist ein Befehlszeilentool verwendet, um die Startdateien auf einem PC oder Gerät zum Ausführen des Windows-Betriebssystems zu konfigurieren. Sie können das Tool in den folgenden Szenarien verwenden:

-   **Fügen Sie nach dem Anwenden eines neuen Windows-Abbilds Startdateien an einem PC.** Verwenden Sie in eine typische Image-basierte Windows-Bereitstellung, BCDBoot So richten Sie die Firmware und die Systempartition ein, das Bild zu starten. Finden Sie weitere Informationen finden Sie unter [Erfassung und Windows anwenden, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).
-   **Einrichten des PCs, eine Datei virtual Hard Disk (VHD) zu starten, die ein Windows-Abbild enthält.** Weitere Informationen finden Sie unter [Boot Festplatte (systemeigenen Start): Hinzufügen einer virtuellen Festplatte zum Menü Start](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md).
-   **Die Systempartition zu reparieren.** Wenn die Systempartition beschädigt ist, können Sie BCDBoot, die Partition Systemdateien mithilfe von neuen Kopien der Dateien aus der Windows-Partition neu erstellen.
-   **Richten Sie ein oder reparieren Sie im Startmenü auf einem PC Dual-Boot.** Wenn Sie mehr als eine Kopie von Windows auf einem PC installiert haben, können Sie BCDBoot hinzufügen oder Reparieren im Startmenü.

## <a name="span-idfilelocationsspanspan-idfilelocationsspanspan-idfilelocationsspanfile-locations"></a><span id="File_Locations"></span><span id="file_locations"></span><span id="FILE_LOCATIONS"></span>Dateispeicherorte


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>In Windows und Windows-Vorinstallation-Umgebung (Windows PE)</p></td>
<td align="left"><p>%WINDIR%\System32\BCDBoot.exe</p></td>
</tr>
<tr class="even">
<td align="left"><p>Im Windows Assessment and Deployment Kit (Windows ADK):</p></td>
<td align="left"><p>C:\Programme\Gemeinsame Dateien (x86) \Windows Kits\10\Assessment und Bereitstellung Kit\Deployment Tools\amd64\BCDBoot\BCDBoot.exe</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsupportedoperatingsystemsspanspan-idsupportedoperatingsystemsspanspan-idsupportedoperatingsystemsspansupported-operating-systems"></a><span id="Supported_operating_systems"></span><span id="supported_operating_systems"></span><span id="SUPPORTED_OPERATING_SYSTEMS"></span>Unterstützte Betriebssysteme


BCDBoot kann von Bilder von 10 Windows, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016 – Technische Vorschau, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 oder Windows Server 2008-Umgebung Startdateien kopieren.

## <a name="span-idhowitworksspanspan-idhowitworksspanspan-idhowitworksspanhow-it-works"></a><span id="How_It_Works"></span><span id="how_it_works"></span><span id="HOW_IT_WORKS"></span>Funktionsweise


Zum Konfigurieren der Systempartition kopiert BCDBoot vom installierten Windows-Abbild eine kleine Gruppe von Dateien Boot-Umgebung in der Systempartition an.

BCDBoot kann einen Speicher (Boot Configuration Data, BCD) auf der Systempartition mit der neuesten Version der Windows-Dateien erstellen:

-   BCDBoot erstellt eine neue BCD-Speicher und die Initialize-Dateien die BCD Boot-Umgebung auf der Systempartition, einschließlich der Windows-Start-Managers mit der %windir%\\System32\\Config\\BCD-Vorlagendatei.
-   Neu in Windows 10: während eines Upgrades behält BCDBoot andere vorhandene Boot Einträge, wie etwa **Debugsettings**, beim Erstellen des neuen Speichers. Verwenden Sie die **Option/c** zu ignorieren die alten Einstellungen und mit einer neuen Startkonfigurationsdatenspeicher aktuell.
-   Wenn bereits ein Boot-Eintrag für diese Windows-Partition, in der Standardeinstellung ist löscht BCDBoot den alten Boot-Eintrag und deren Werte an. Mithilfe der **Option/m** die Werte aus einem vorhandenen Boot-Eintrag beibehalten, wenn Sie zum Aktualisieren der Systemdateien.
-   In der Standardeinstellung verschiebt BCDBoot den Boot-Eintrag für die ausgewählte Windows-Partition zum oberen Rand der Startreihenfolge Windows Boot-Manager. Verwenden Sie die **Option/d** , um die vorhandenen Startreihenfolge beibehalten.

Auf UEFI-PCs kann BCDBoot die Einträge der Firmware des Geräts NVRAM aktualisieren:

-   BCDBoot Fügt einen Firmware-Eintrag in der NVRAM, zeigen Sie auf der Windows-Start-Manager. Dieser Eintrag wird standardmäßig als das erste Element in der Liste Boot platziert. Verwenden Sie die **Befehlszeilenoption/p** die vorhandene UEFI Startreihenfolge beibehalten. Verwenden Sie **/addlast** noch am Ende der Liste der Boot-Reihenfolge hinzugefügt.

## <a name="span-idcommand-lineoptionsspanspan-idcommand-lineoptionsspanspan-idcommand-lineoptionsspancommand-line-options"></a><span id="Command-Line_Options"></span><span id="command-line_options"></span><span id="COMMAND-LINE_OPTIONS"></span>Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen stehen für BCDBoot.exe.

**BCDBOOT** &lt;*source*&gt; \[**/l** &lt;*locale*&gt;\] \[**/s** &lt;*volume-letter*&gt; \[**/f** &lt;*firmware type*&gt;\]\] \[**/v**\] \[**/m** \[{*OS Loader GUID*}\]\] \[**/addlast** or **/p**\] \[**/d**\] \[**/c**\]

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
<td align="left"><p><em>&lt;Quelle&gt;</em></p></td>
<td align="left"><p>Erforderlich. Gibt den Speicherort des Windows-Verzeichnisses, das als Quelle zum Kopieren von Dateien Boot-Umgebung verwenden.</p>
<p>Im folgende Beispiel werden die Systempartition mithilfe von BCD-Dateien aus dem Ordner C:\Windows initialisiert:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/ l <em> &lt;Gebietsschema&gt;</em></p></td>
<td align="left"><p>Optional Gibt das Gebietsschema. Der Standardwert ist Englisch (USA) (<code>en-us</code>).</p>
<p>Im folgenden Beispiel wird das Standardgebietsschema BCD für Japanisch:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /l ja-jp</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/ s <em> &lt;Volumebuchstabe&gt;</em></p></td>
<td align="left"><p>Optional Gibt den Volumebuchstaben der Systempartition an. Diese Option sollte nicht in normalen Bereitstellungsszenarien verwendet werden.</p>
<p>Verwenden Sie diese Einstellung eine Systempartition angeben, wenn Sie ein Laufwerk, das auf einem anderen Computer gestartet wird konfigurieren, wie ein USB-Laufwerk oder eine zweite Festplatte.</p>
<p><strong>UEFI</strong>:</p>
<ul>
<li><p>BCDBoot kopiert die Startdateien in die EFI-Systempartition oder die durch die Option/s angegebenen Partition.</p>
<p>BCDBoot dient Startkonfigurationsdaten in der gleichen Partition.</p>
<p>Standardmäßig erstellt BCDBoot einen Windows-Start-Manager-Eintrag im NVRAM auf die Firmware die Startdateien auf der Systempartition identifiziert. Wenn die Option/s verwendet wird, wird dieser Eintrag nicht erstellt. Stattdessen nutzt BCDBoot die Standardeinstellungen Firmware, um die Startdateien auf der Systempartition zu identifizieren. Durch die UEFI 2.3.1 Spec, die Standardeinstellungen für Firmware sollte die Datei geöffnet werden: \efi\boot\bootx64.efi in EFI System Partition (ESP).</p></li>
</ul>
<p><strong>BIOS</strong>:</p>
<ol>
<li><p>BCDBoot kopiert die Startdateien in der aktiven Partition auf der primären Festplatte oder Partition durch die Option/s angegeben.</p></li>
<li><p>BCDBoot erstellt Startkonfigurationsdaten in derselben Partition.</p></li>
</ol>
<p>Das folgende Beispiel kopiert BCD-Dateien aus dem Ordner C:\Windows in einer Partition auf einer sekundären Festplatte gestartet wird, die auf einem anderen Computer. Die Systempartition auf dem sekundären Laufwerk wurde den Volumebuchstaben <em>S</em>zugewiesen:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S:</code></pre>
<p>Das folgende Beispiel erstellt Starteinträge auf einem USB-Laufwerk mit dem Volumebuchstaben F, einschließlich Startdateien zur Unterstützung einer UEFI-basierten oder einem BIOS-basierten Computer:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S: /f ALL</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/ f <em> &lt;Firmware-Typ&gt;</em></p></td>
<td align="left"><p>Optional Gibt den Typ der Firmware. Gültige Werte sind <code>UEFI</code>, <code>BIOS</code>, und <code>ALL</code>.</p>
<ul>
<li><p>Auf BIOS/MBR-basierte Systeme, der Standardwert ist <code>BIOS</code>. Diese Option wird das <strong>\Boot</strong> -Verzeichnis auf der Systempartition erstellt und alle erforderlichen Boot-Umgebung Dateien in dieses Verzeichnis kopiert.</p></li>
<li><p>Auf UEFI/GPT-basierte Systeme, der Standardwert ist <code>UEFI</code>. Diese Option wird das <strong>\Efi\Microsoft\Boot</strong> -Verzeichnis erstellt und alle erforderlichen Boot-Umgebung Dateien in dieses Verzeichnis kopiert.</p></li>
<li><p>Bei der Angabe der <code>ALL</code> -Wert BCDBoot erstellt die <strong>\Boot</strong> und die Verzeichnisse <strong>\Efi\Microsoft\Boot</strong> und Boot-Umgebung kopiert alle erforderlichen Dateien für BIOS und UEFI auf diese Verzeichnisse.</p></li>
</ul>
<p>Wenn Sie über <strong>die/f</strong> -Option angeben, müssen Sie auch die <strong>Option/s</strong> , um die Lautstärke Buchstaben der Systempartition zu identifizieren angeben.</p>
<p>Das folgende Beispiel kopiert BCD-Dateien, die auf einer UEFI-basierten oder einem BIOS-basierten Computer aus dem Ordner C:\Windows auf einem USB-Laufwerk, die den Brief Volume <em>F</em>entzogen starten unterstützen:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S: /f ALL </code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/ v</p></td>
<td align="left"><p>Optional Aktiviert den ausführlichen Modus. Beispiel:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /v</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/ m [<em>{OS Loader GUID}</em>]</p></td>
<td align="left"><p>Optional Führt die Werte aus einem vorhandenen Boot-Eintrag in einen neuen Eintrag Boot zusammen.</p>
<p>In der Standardeinstellung führt diese Option nur globale Objekte zusammen. Wenn Sie eine <em>OS Loader GUID</em>angeben, werden diese Option Loader-Objekts in der Systemvorlage um einen startbaren Eintrag zu erstellen.</p>
<p>Im folgenden Beispiel werden das Betriebssystem-Ladeprogramm im aktuellen BCD-Speicher, den die angegebene GUID in der neuen Startkonfigurationsdatenspeicher identifiziert:</p>
<pre class="syntax" space="preserve"><code>bcdboot c:\Windows /m {xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/AddLast</p></td>
<td align="left"><p>Optional Gibt an, dass der Windows-Start-Manager Firmware Eintrag zuletzt hinzugefügt werden soll. Das Standardverhalten ist es zunächst hinzufügen. Kann nicht mit/p verwendet werden.</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /addlast</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/ p</p></td>
<td align="left"><p>Optional Gibt an, dass die vorhandenen Windows-Start-Manager Firmware Eintrag Position in der Startreihenfolge UEFI beibehalten werden soll. Wenn der Eintrag nicht vorhanden ist, wird ein neuer Eintrag in der ersten Position hinzugefügt. Kann nicht mit /addlast verwendet werden.</p>
<p>Standardmäßig verschiebt während einer Aktualisierung BCDBoot der Windows-Start-Manager auf den ersten Eintrag in der Startreihenfolge UEFI sein.</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /p
bcdboot C:\Windows /p /d</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/ d</p></td>
<td align="left"><p>Optional Beibehalten den vorhandenen Standardeintrag Betriebssystem im {Bootmgr}-Objekt im Windows-Start-Manager.</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /d</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/ c</p></td>
<td align="left"><p>Optional Gibt an, dass alle vorhandenen BCD-Elemente nicht migriert werden sollen.</p>
<p>Neu in Windows 10: standardmäßig während eines Upgrades BCD Elemente wie <strong>Debugsettings</strong> oder <strong>Flightsigning</strong> werden beibehalten.</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /c</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrepairthesystempartitionspanspan-idrepairthesystempartitionspanspan-idrepairthesystempartitionspanrepair-the-system-partition"></a><span id="Repair_the_system_partition"></span><span id="repair_the_system_partition"></span><span id="REPAIR_THE_SYSTEM_PARTITION"></span>Reparieren der Systempartition


Wenn die Systempartition beschädigt ist, können Sie BCDBoot, um die Systemdateien Partition neu zu erstellen, mithilfe von neuen Kopien der Dateien aus der Windows-Partition verwenden.

1.  Starten Sie den PC an eine Befehlszeile. Angenommen, starten Sie den Windows-Installationsdatenträger und drücken Sie UMSCHALT + F10 oder starten Sie Windows PE ([Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)).

2.  Verwenden Sie Diskpart, um zu bestimmen, welche Laufwerkbuchstaben Ihrer Windows und Systempartition enthält (`diskpart, list vol, exit`).

3.  Optional: Formatieren der Systempartition:`format (drive letter of your system partition) /q`

4.  Fügen Sie einen Boot-Eintrag für die Windows-Partition hinzu:`bcdboot D:\Windows`

5.  Starten Sie den PC neu. Windows sollte angezeigt werden.

## <a name="span-idsetuporrepairthebootmenuonadual-bootpcspanspan-idsetuporrepairthebootmenuonadual-bootpcspanspan-idsetuporrepairthebootmenuonadual-bootpcspanset-up-or-repair-the-boot-menu-on-a-dual-boot-pc"></a><span id="Set_up_or_repair_the_boot_menu_on_a_dual-boot_PC"></span><span id="set_up_or_repair_the_boot_menu_on_a_dual-boot_pc"></span><span id="SET_UP_OR_REPAIR_THE_BOOT_MENU_ON_A_DUAL-BOOT_PC"></span>Richten Sie ein oder reparieren Sie im Startmenü auf einem PC Dual-boot


Beim Einrichten von eines PCs, mehr als ein Betriebssystem zu starten, können Sie die Möglichkeit zum Starten eines der Betriebssysteme verloren gehen. Die Option BCDBoot können Sie schnell Startoptionen für ein Windows-basierten Betriebssystem hinzufügen. So richten einen Dual-Boot-PC

1.  Installieren einer separaten Festplatte oder zur Vorbereitung einer separaten Partition für jedes Betriebssystem.

2.  Installieren Sie die Betriebssysteme. Beispielsweise weist auf Ihrem PC Windows 7, installieren Sie Windows 10 auf der anderen Festplatte oder Partition.

3.  Starten Sie den PC neu. Die Menüs Boot sollte mit beiden genannten Betriebssysteme angezeigt werden.

    Wenn beide Betriebssysteme aufgeführt sind:

    1.  Öffnen Sie eine Befehlszeile, entweder als Administrator aus innerhalb der Fenster oder mithilfe einer Befehlszeile mithilfe von Windows-Installationsmedium, und drücken UMSCHALT + F10 starten oder durch Starten von Windows PE ([Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md)).
    2.  Hinzufügen von Startoptionen für ein Windows-Betriebssystem.

        ``` syntax
        bcdboot D:\Windows
        ```

    3.  Starten Sie den Computer neu. Nun wird das Startmenü beide Menüoptionen im angezeigt.

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


Informationen zum Reparieren von Boot-Dateien auf einem PC mit Windows XP oder einer neueren Version von Windows wie Windows 7 finden Sie in der Microsoft Knowledge Base-Artikel [2277998](http://go.microsoft.com/fwlink/?LinkId=234039).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Aufzeichnen und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md)

[Konfigurieren von Partitionen BIOS/MBR-basierten Festplatte](configure-biosmbr-based-hard-drive-partitions.md)

[Konfigurieren von Partitionen UEFI, GPT-basierten Festplatte](configure-uefigpt-based-hard-drive-partitions.md)

[BCDedit](http://go.microsoft.com/fwlink/?LinkId=128459)

[Bootsect Befehlszeilenoptionen](bootsect-command-line-options.md)

[Diskpart Befehlssyntax Linie](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






