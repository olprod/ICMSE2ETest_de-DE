---
author: Justinha
Description: Command-Line Options Wpeutil
ms.assetid: 6537713a-510e-40cd-8518-d1150422bfe8
MSHAttr: PreferredLib:/library/windows/hardware
title: Command-Line Options Wpeutil
ms.openlocfilehash: 6bd9d321c2954e6c69857461b2a7da2afbcc350c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpeutil-command-line-options"></a>Command-Line Options Wpeutil


Das Windows® PE-Dienstprogramm (Wpeutil) ist ein Befehlszeilentool, mit dem Sie während einer Sitzung Windows PE Befehle ausführen kann. Angenommen, können Sie Herunterfahren oder Windows PE neu zu starten, aktivieren oder deaktivieren eine Firewall, Festlegen von Sprachoptionen und initialisieren ein Netzwerks.

## <a name="span-idwpeutilcommand-lineoptionsspanspan-idwpeutilcommand-lineoptionsspanspan-idwpeutilcommand-lineoptionsspanwpeutil-command-line-options"></a><span id="Wpeutil_Command-Line_Options"></span><span id="wpeutil_command-line_options"></span><span id="WPEUTIL_COMMAND-LINE_OPTIONS"></span>Command-Line Options Wpeutil


Wpeutil verwendet die folgenden Konventionen.

**Wpeutil** {Befehl} \[ *Argument*\]

Beispiel:

``` syntax
Wpeutil Shutdown
Wpeutil Enablefirewall
Wpeutil SetMuiLanguage de-DE
```

**Hinweis**  
Wpeutil kann nur ein Befehl pro Zeile akzeptiert.

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Befehl</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>CreatePageFile [/ Pfad =&lt;Pfad&gt;] [/ size =&lt;Größe&gt;]</strong></p></td>
<td align="left"><p>Erstellt eine Auslagerungsdatei auf einem angegebenen Pfad und Größe. Der Standardpfad lautet C:\pagefile.sys und Standardgröße ist 64 MB. Es muss mindestens eine Option angegeben werden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil CreatePageFile /path=C:\pagefile.sys</code></pre>
<p>\endash oder \endash</p>
<pre class="syntax" space="preserve"><code>Wpeutil CreatePageFile /path=C:\pagefile.sys /size=128</code></pre>
<div class="alert">
<strong>Wichtige</strong>  
<p>Wenn eine Page-Datei vorhanden ist, muss die Option <strong>/CreatePageFile</strong> festgelegt werden, gleich oder größer als die aktuelle Größe der Auslagerungsdatei oder der Befehl schlägt fehl.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><strong>DisableExtendedCharactersForVolume &lt;Path_on_target_volume&gt;</strong></p></td>
<td align="left"><p>Deaktiviert die Unterstützung erweiterter Zeichen für DOS-kompatible Dateinamen (8.3-Format) für das Volume, <em>das Pfad auf dem Ziel-Volume</em>enthält. Dieser Befehl gilt nur für NTFS-Volumes. Der <em>Pfad auf dem Ziel-Volume</em> muss im Stammverzeichnis des Volumes angeben. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil DisableExtendedCharactersForVolume C:\</code></pre>
<p>Wenn deaktiviert, werden alle Dateien, die mit Sonderzeichen erstellt wurden in einen kurzen Dateinamen konvertiert werden.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>DisableFirewall</strong></p></td>
<td align="left"><p>Deaktiviert eine Firewall. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil DisableFirewall</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>EnableExtendedCharactersForVolume</strong> <em>&lt;Path_on_target_volume&gt;</em></p></td>
<td align="left"><p>Ermöglicht das 8.3-Format Dateinamen Sonderzeichen auf dem Datenträger enthalten, die <em>Ziel-Volume-Pfad</em>enthält. Dieser Befehl gilt nur für NTFS-Volumes. Der <em>Pfad auf dem Ziel-Volume</em> muss im Stammverzeichnis des Volumes angeben. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil EnableExtendedCharactersForVolume C:\</code></pre>
<div class="alert">
<strong>Hinweis</strong>  
<p>Wenn Sie ein Betriebssystem in einer anderen Sprache installieren, die erweiterte Zeichen, die wie etwa ja-JP oder Ko-KR oder mit einer Kopie der Windows PE in einer Sprache, erweiterte Zeichen aktiviert, wie En-US, die nicht in der Standardeinstellung aktiviert sind wird die Installation beim ersten Starten einen Chkdsk-Fehler verursacht. Durch Aktivieren dieser Option vor der Installation auf diesem Volume wird Ausführen den Befehl Chkdsk aus verhindern.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>EnableFirewall</strong></p></td>
<td align="left"><p>Aktiviert eine Firewall. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil EnableFirewall</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>InitializeNetwork</strong></p></td>
<td align="left"><p>Initialisiert Netzwerkkomponenten und Treiber und legt den Namen des Computers auf einen zufällig ausgewählten Wert fest. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil InitializeNetwork</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ListKeyboardLayouts</strong> <em>&lt;LCID&gt;</em></p></td>
<td align="left"><p>Listet die Tastaturlayouts unterstützte (Name und ID) für einen angegebenen Wert für die Gebietsschema-ID (LCID). Die Tastaturlayouts werden auch in der Registrierung unter dem Schlüssel aktualisiert: <strong>HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\WinPE\KeyboardLayouts</strong>. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil ListKeyboardLayouts 0x0409</code></pre>
<p>\endash oder \endash</p>
<pre class="syntax" space="preserve"><code>Wpeutil ListKeyboardLayouts 1033</code></pre>
<p>Eine Liste der gültigen Gebietsschema-IDs finden Sie unter [Locale ID (LCID) Chart](http://go.microsoft.com/fwlink/?LinkId=209839).</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Neustart</strong></p></td>
<td align="left"><p>Startet die aktuelle Windows PE-Sitzung neu. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil Reboot</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SaveProfile</strong></p></td>
<td align="left"><p>Beendet die Protokollierung und speichert das benutzerdefinierte Profil zum Speicherort den Benutzer mit dem Befehl <strong>Dism/Enable-Profiling</strong> zuvor angegeben haben. Weitere Informationen über die <strong>Befehlszeilenoption/Enable-Profiling</strong> finden Sie unter [DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md). Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil SaveProfile profile_file_name &quot;short description&quot;</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SetKeyboardLayout</strong> <em>&lt;Keyboard_layout_ID&gt;</em></p></td>
<td align="left"><p>Legt das Tastaturlayout in der aktuellen Windows PE-Sitzung. Dadurch gelangen Effekt für Prozesse, nachdem der Befehl erfolgreich ausgeführt wird. Um eine Liste der unterstützten Tastaturlayout zu erhalten, geben Sie Folgendes ein:</p>
<pre class="syntax" space="preserve"><code>ListKeyboardLayouts LCID</code></pre>
<p>So legen Sie die Tastatur für En-US, beispielsweise fest:</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetKeyboardLayout 0409:00000409</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SetMuiLanguage</strong> <em>&lt;sprachennamens&gt;</em>[<strong>;</strong><em> &lt;Name der Sprache&gt;</em>]</p></td>
<td align="left"><p>Legt die Sprache fest. <em> &lt;Name der Sprache&gt; </em> verwendet das Format für internationale Sprachen (z. B. En-US für US-Englisch). Sie können mehrere Sprachen in Prioritätsreihenfolge ausprobiert, indem Sie diese durch ein Semikolon voneinander angeben. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetMuiLanguage de-DE;en-US</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SetUserLocale</strong> <em>&lt;sprachennamens&gt;</em>[<strong>;</strong><em> &lt;sprachennamens&gt;</em>]</p></td>
<td align="left"><p>Das Gebietsschema des Benutzers festgelegt. <em> &lt;sprachennamens&gt; </em> das Format für internationale Sprachen (z. B. En-US für die englische Sprache US) verwendet. Sie können mehrere Sprachen in Prioritätsreihenfolge ausprobiert, angeben, indem Sie diese durch ein Semikolon voneinander. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetUserLocale de-DE;en-US</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Herunterfahren</strong></p></td>
<td align="left"><p>Beendet die aktuelle Windows PE-Sitzung. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil Shutdown</code></pre>
<div class="alert">
<strong>Hinweis</strong>  
<p>Sie können auch in das Eingabeaufforderungsfenster Folgendes ausführen:</p>
<ul>
<li><p>Klicken Sie auf die Schaltfläche <strong>Schließen</strong></p></li>
<li><p>Typ BEENDEN</p></li>
</ul>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><strong>UpdateBootInfo</strong></p></td>
<td align="left"><p>Füllt die Registrierung mit Informationen zu Windows PE wie zu starten.</p>
<p>Nachdem Sie diesen Befehl ausführen, Fragen Sie die Registrierung. Beispiel:</p>
<pre class="syntax" space="preserve"><code>wpeutil UpdateBootInfo
reg query HKLM\System\CurrentControlSet\Control /v PEBootType</code></pre>
<p>Die Ergebnisse dieses Vorgangs möglicherweise nach dem Laden zusätzlicher Treiber ändern.</p>
<p>Um zu bestimmen, wo Windows PE gestartet wird, überprüfen Sie Folgendes:</p>
<ul>
<li><strong>PEBootType</strong>: Fehler, flach, Remote, Ramdisk:SourceIdentified Ramdisk:SourceUnidentified, Ramdisk:OpticalDrive</li>
<li><strong>PEBootTypeErrorCode</strong>: HRESULT-Code</li>
<li><strong>PEBootServerName</strong>: Windows-Bereitstellungsdienst-Servernamen</li>
<li><strong>PEBootServerAddr</strong>: IP-Adresse für Windows-Bereitstellungsdienst-Servers</li>
<li><strong>PEBootRamdiskSourceDrive suchen</strong>: Laufwerkbuchstabe Quelle, falls verfügbar.</li>
<li><strong>PEFirmwareType</strong>: Startmodus Firmware: 0 x 1 für BIOS, 0 x 2 für UEFI.</li>
</ul>
<p>Wenn Sie Windows-Bereitstellungsdienste nicht starten, ist die beste Möglichkeit, um zu ermitteln, auf dem Windows PE von gestartet zum ersten Suchen nach dem Registrierungsschlüssel PEBootRamdiskSourceDrive suchen. Wenn es nicht vorhanden ist, überprüfen Sie die Laufwerke, auf die richtige PEBootType, und suchen Sie nach verschiedenste Tag-Datei, die das Startlaufwerk identifiziert.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>WaitForNetwork</strong></p></td>
<td align="left"><p>Wartet, bis der Netzwerkkarte initialisiert werden. Verwenden Sie diesen Befehl beim Erstellen von Skripts, um sicherzustellen, dass die Netzwerkkarte vor dem Fortfahren vollständig initialisiert wurde.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>WaitForRemovableStorage</strong></p></td>
<td align="left"><p>Während des Startvorgangs Windows PE mit diesem Befehl zum Starten des blockieren, bis die Wechseldatenträgern, wie USB-Festplatten, initialisiert werden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Wpeutil WaitForRemovableStorage</code></pre>
<div class="alert">
<strong>Hinweis</strong>  
<p>In der <strong>WaitForRemovableStorage</strong> die Rechtschreibung ist korrekt.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Bereitstellen und anpassen](winpe-mount-and-customize.md)

[DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md)

 

 






