---
author: Justinha
Description: "Befehlszeilenoptionen für REAgentC"
ms.assetid: da498872-1c26-4cb8-a5da-80a0d45200f3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Befehlszeilenoptionen für REAgentC"
ms.openlocfilehash: 82b55bbe9b8b98380d2a5a563c25545322bf1e67
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reagentc-command-line-options"></a>REAgentC Befehlszeilenoptionen


Sie können das Tool REAgentC.exe so konfigurieren Sie eine Windows Recovery Environment (Windows RE) Start- und Image-Wiederherstellung Drucktaste zurücksetzen und zum Verwalten von Wiederherstellungsoptionen und Anpassungen verwenden. Sie können den Befehl **REAgentC** auf ein offline-Windows-Abbild oder auf einem ausgeführten Windows-Betriebssystem ausführen.

**Hinweis**  
Wenn Sie Windows PE 2.X, 3.X oder 4.X für die Wiederherstellung auf eine offline Windows 10 Installation konfigurieren verwenden, müssen Sie die Datei Winrecfg.exe aus der Wiederherstellung Ordner mit dem Windows Assessment and Deployment Kit (Windows ADK) verwenden. Winrecfg.exe unterstützt nur die offline-Vorgänge, die REAgentC.exe unterstützt.

 

## <a name="span-idreagentccommandsspanspan-idreagentccommandsspanspan-idreagentccommandsspanreagentc-commands"></a><span id="REAgentC_Commands"></span><span id="reagentc_commands"></span><span id="REAGENTC_COMMANDS"></span>REAgentC (Befehle)


Die folgenden Befehlszeilenoptionen stehen für Windows RE:

**REAgentC.exe** &lt;Befehl&gt; &lt;Argumente&gt;

In der folgenden Tabelle werden die Befehlszeilenoptionen beschrieben:

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Online-/Offline</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Path /setreimage</strong> <em>&lt;Path_to_Windows_RE_image&gt; </em> [<strong>/ target</strong> <em>&lt;Path_to_offline_image&gt;</em>]</p>
<p></p></td>
<td align="left"><p> Beides</p></td>
<td align="left"><p>Legt den Speicherort eines Bilds Boot Windows RE. In Windows 10, Windows 8.1, Windows 8, Windows Server 2016 – Technische Vorschau, Windows Server 2012 R2 und Windows Server 2012 <strong>unterstützt/Path</strong> UNC-Pfade zu Speicherorten auf dem lokalen Datenträger. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setreimage /path S:\Recovery\WindowsRE</code></pre>
<p>Geben Sie den Speicherort des Windows-Abbilds aus, wenn Sie die Einstellung anwenden mithilfe der <strong>Option/target</strong> offline. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ enable</strong> [<strong>/auditmode</strong>] [<strong>/osguid</strong> &lt;Bcd_guid&gt;]</p></td>
<td align="left"><p>Online</p></td>
<td align="left"><p>Ermöglicht einem Windows RE Boot-Abbild.</p>
<p>Die <strong>Option/enable</strong> wird automatisch während des Konfigurationsdurchgangs ausgeführt. Wenn Sie eine Windows RE Boot-Abbild nicht angeben, versucht der Computer Windows RE mithilfe der Standard-Winre.wim-Datei aus dem Ordner \Windows\System32\Recovery aktivieren.</p>
<ul>
<li><p><strong>/auditmode</strong>:</p>
<p>In der Standardeinstellung durchführen nicht die <strong>Option/enable</strong> keine Aktionen, wenn Windows im Überwachungsmodus aktiviert wird. Zum Überschreiben des Standardverhaltens und Windows RE im Überwachungsmodus aktivieren, geben Sie die Option <strong>/auditmode</strong> . Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /enable /auditmode</code></pre>
<p>Wenn Sie das Bild nach dem Verwenden der <strong>Option/Aktivieren</strong> im Überwachungsmodus verallgemeinern, ist Windows RE, bis Sie die <strong>Option/enable</strong> erneut oder bis verwenden nach der Ausführung des Konfigurationsdurchgangs deaktiviert.</p></li>
<li><p><strong>/osguid</strong> &lt;Bcd_guid&gt;:</p>
<p>Diese Option können Sie Ihre Windows RE Boot-Abbild von Windows PE zu aktivieren. Es kann nur verwendet werden, nachdem bcdboot.exe ausgeführt wurde. &lt;Bcd_guid&gt; ist der Bezeichner (Boot Configuration Data, BCD), der das Ziel des Windows-Installation durch Ausführen von abgerufen <code>bcdedit -enum -v</code>.</p>
<pre class="syntax" space="preserve"><code>Reagentc /enable /osguid {00000000-0000-0000-0000-000000000000}</code></pre></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Disable</strong></p></td>
<td align="left"><p>Online</p></td>
<td align="left"><p>Deaktiviert alle aktiven Windows RE-Abbild, das das online Bild zugeordnet ist. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/boottore</strong></p></td>
<td align="left"><p>Online</p></td>
<td align="left"><p>Gibt an, dass Windows RE automatisch das nächste Mal gestartet wird, die das System gestartet wird. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /boottore</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Path /setosimage</strong> <em>&lt;Path_to_recovery_image&gt;</em> <strong>/Index</strong> <em>&lt;Abbild_Index&gt; </em> [<strong>/ target</strong> <em>&lt;Path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> Beides</p></td>
<td align="left"><p>Diese Einstellung wird nicht in Windows 10 verwendet.</p>
<p>Registriert die Position eines Bilds Drucktaste zurücksetzen in einem Bild online oder offline. Das Wiederherstellungsabbild muss im Windows-WIM-Format.</p>
<p>Die <strong>Option/Index</strong> gibt die Indexnummer des Wiederherstellungsabbilds von innerhalb einer WIM-Datei verwendet. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setosimage /path R:\RecoveryImage /index 1</code></pre>
<p>Verwenden Sie die <strong>Option/target</strong> an den Speicherort des Windows-Abbilds offline. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setosimage /path R:\RecoveryImage /index 1 /target W:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Info</strong> [<strong>/ target</strong> <em>&lt;Path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> Beides</p></td>
<td align="left"><p>Den aktuellen Status der Windows RE und alle verfügbaren Wiederherstellungsabbild auf ein Bild online oder offline angezeigt. Der folgende Befehl wird beispielsweise der Status des Betriebssystems online zurückgegeben:</p>
<pre class="syntax" space="preserve"><code>Reagentc /info</code></pre>
<p>Verwenden <strong>Sie/target</strong> -Option, um Konfigurationsinformationen zu einem offline-Abbild abzurufen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /info /target W:\Windows</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/setbootshelllink</strong> [<strong>/ ConfigFile</strong> <em>&lt;Path_to_BootShellXML&gt;</em>] [<strong>/ target</strong> <em>&lt;Path_to_offline_image&gt;</em>]</p></td>
<td align="left"><p> Beides</p></td>
<td align="left"><p>Den Link, um ein benutzerdefiniertes Tool, das angezeigt wird registriert in das Windows-Startmenü Optionen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setbootshelllink /configfile F:\BootMenu\AddDiagnosticsToolToBootMenu.xml</code></pre>
<p>Die Datei BootShellXML ist an.xml Datei, enthält die <em> &lt;BootShell&gt; </em> Element und die <em> &lt;Name&gt; </em> und <em> &lt;Beschreibung&gt; </em> Attribute, die in der Verknüpfung angezeigt werden soll. Weitere Informationen finden Sie unter [Windows RE anpassen](customize-windows-re.md).</p>
<p>Verwenden <strong>Sie/target</strong> -Option, um die Position des offline Windows-Abbilds anzugeben. Wenn dieses Argument nicht verwendet wird, wird das Betriebssystem ausgeführt wird. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Reagentc /setbootshelllink /target W:\Windows</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows RE-Problembehandlung von Features](windows-re-troubleshooting-features.md)

 

 






