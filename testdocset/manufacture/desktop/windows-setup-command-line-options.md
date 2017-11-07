---
author: Justinha
Description: Windows Setup-Befehlszeilenoptionen
ms.assetid: 16001d04-db9f-4953-abc7-37903ef47fd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Setupbefehlszeilenoptionen für Windows"
ms.openlocfilehash: 0b4528a27c96d51db770c0798488e27639269174
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-command-line-options"></a>Windows Setup-Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen sind für Windows Setup verfügbar. Beginnend mit Windows 10, Version 1607, können Sie eine Datei Setupconfig als Alternative zu übergeben Parameter an Windows Setup auf eine Befehlszeile verwenden. Weitere Informationen finden Sie unter [Übersicht über die Automatisierung von Windows Setup](windows-setup-automation-overview.md).

**Setup.exe** \[ **/1394debug:***&lt;Channel&gt; * \[ **Baudrate:***&lt;Baudrate&gt; *\]\]

\[**/addbootmgrlast**\]

\[**/ Auto** {**Clean** | **DataOnly** | **Aktualisieren**}\]

\[**/busparams:***&lt;bus.device.function&gt;*\]

\[**/CompactOS** {**Aktivieren** | **Deaktivieren**}\]

\[**/Compat** {**IgnoreWarning** | **ScanOnly**}\]

\[**/ CopyLogs***&lt;Speicherort&gt;*\]

\[**/ debug:***&lt;Channel&gt; * \[ **Baudrate:***&lt;Baudrate&gt; *\]\]

\[**/DynamicUpdate** {**Aktivieren** | **Deaktivieren**}\]

\[**/emsport:** {**COM1** | **COM2** | **Usebiossettings** | **deaktiviert**} \[ **/emsbaudrate:***&lt;Baudrate&gt; *\]\]

\[**/ InstallDrivers***&lt;Speicherort&gt;*\]

\[**/ installFrom** * &lt;Pfad&gt;*\]

\[**/ InstallLangPacks***&lt;Speicherort&gt;*\]

\[**m:***&lt;Ordner\_Namen&gt; * \] \[ **noreboot**\] 

\[**/MigrateDrivers** {**all** | **none**}\]

\[**/netdebug:**Hostip =&lt;*w.x.y.z*&gt;, Port =&lt;*n*&gt;, Key =&lt;*q.r.s.t*&gt;\[, Nodhcp\]\[, Busparams =*n.o.p*\]\]

\[**/ NoReboot**\]

\[**/Pkey** * &lt;Product Keys&gt;*\]

\[**/ PostOOBE***&lt;Speicherort&gt;*\[**\\setupcomplete.exe**\]\]

\[**/ PostRollback***&lt;Speicherort&gt;*\[**\\setuprollback.exe**\]\]

\[**/ Quiet**\]

\[**/ ReflectDrivers***&lt;Speicherort&gt;*\]

\[**/ResizeRecoveryPartition** {**Aktivieren** | **Deaktivieren**}\]

\[**/ShowOOBE** {**vollständigen** | **keine**}\]

\[**/Telemetry** {**Aktivieren** | **Deaktivieren**}\]

\[**/ TempDrive:***&lt;Laufwerkbuchstabe&gt;*\]

\[**/ für die unbeaufsichtigte Installation:***&lt;Antwort\_Datei&gt;*\]

\[**/ Uninstall** {**Aktivieren** | **Deaktivieren**}\]

\[**/usbdebug:***&lt;Hostname&gt;*\]

\[**/wdsdiscover**\]

\[**/ WDSServer:***&lt;Servername&gt;*\]

## <a name="span-idsetupcommand-lineoptionsspanspan-idsetupcommand-lineoptionsspanspan-idsetupcommand-lineoptionsspansetup-command-line-options"></a><span id="Setup_Command-Line_Options"></span><span id="setup_command-line_options"></span><span id="SETUP_COMMAND-LINE_OPTIONS"></span>Setup-Befehlszeilenoptionen


Die folgende Tabelle enthält die Setup-Befehlszeilenoptionen:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><strong>Option</strong></th>
<th align="left"><strong>Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/1394Debug:</strong><em>&lt;Channel&gt; </em> [<strong>BaudRate:</strong><em>&lt;Baudrate&gt;</em>]</p></td>
<td align="left"><p>Ermöglicht das Kernel-debugging über IEEE 1394 (FireWire)-Anschluss während Windows ausgeführt wird und während der [WindowsPE](windowspe.md) Konfiguration Durchlauf von Windows Setup.</p>
<p><em>&lt;DDE-Kanal&gt; </em> gibt den debugging DDE-Kanal an. Der Standardwert für <em> &lt;Channel&gt; </em> ist <strong>1</strong>.</p>
<p>[<strong>Baudrate:</strong><em>&lt;Baudrate&gt;</em>] Gibt die Baudrate beim Windows während des Debuggens Datenübertragungen verwendet werden. Die Standardeinstellung ist <strong>19200</strong>. Sie können auch Festlegen der <em> &lt;Baudrate&gt; </em> auf <strong>57600</strong> oder <strong>115200</strong>festlegen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /1394debug:1 /baudrate:115200</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ AddBootMgrLast</strong></p></td>
<td align="left"><p>Weist Windows Setup an der Windows-Start-Manager als der letzte Eintrag in der UEFI Firmware Startreihenfolge hinzufügen. Diese Option ist nur unter UEFI-PCs unter Windows PE 4.0 oder höher unterstützt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Auto</strong> {<strong>Clean</strong> | <strong>DataOnly</strong> | <strong>Upgrade</strong>}</p></td>
<td align="left"><p>Führt eine automatisierte Aktualisierung auf Windows 10 oder Windows 8.1 volumenlizenzeditionen nur an.</p>
<p>Wenn/Auto verwendet wird, kann eine Datei für die unbeaufsichtigte Installation verwendet werden.</p>
<p>Wenn/Auto verwendet wird, verwendet Windows Setup ei.cfg ein Kompatibilitätsprobleme überprüft vor Beginn der Installation. Wenn ei.cfg falsch formatiert ist, wird das Setup wird automatisch beendet und meldet einen Code.</p>
<p><strong>Clean</strong>: führt eine Neuinstallation von Windows.</p>
<p><strong>DataOnly</strong>: führt eine Aktualisierung von Windows, speichern nur Daten (und nicht apps.) Wenn die Option nur Daten-Installation nicht aufgrund von hauptversionsebene verfügbar ist, wird Windows Setup im Hintergrund zu beenden und melden Sie sich einen Code.</p>
<p><strong>Upgrade</strong>: führt eine Aktualisierung von Windows-apps und Daten speichern. Die Aktualisierung Installationsoption ist nicht verfügbar, oder der Benutzer muss ein Kompatibilitätsproblem app zu beheben, wird Windows Setup im Hintergrund zu beenden und melden Sie sich einen Code.</p>
<p><strong>Setup.exe Exit-Codes:</strong></p>
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Codename beenden</th>
<th align="left">Exit-code</th>
<th align="left">Ursache</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>CONX_SETUP_EXITCODE_CONTINUE_REBOOT</p></td>
<td align="left"><p>0 x 3</p></td>
<td align="left"><p>Das Upgrade erfolgreich war.</p></td>
</tr>
<tr class="even">
<td align="left"><p>CONX_SETUP_EXITCODE_RESUME_AT_COMPAT_REPORT</p></td>
<td align="left"><p>0 x 5</p></td>
<td align="left"><p>Die Kontrollkästchen erkannten Kompatibilitätsprobleme, die Lösung benötigen, vor dem Fortsetzen der Aktualisierung.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>CONX_SETUP_EXITCODE_AUTO_INSTALL_FAIL</p></td>
<td align="left"><p>0 x 7</p></td>
<td align="left"><p>Die Installationsoption (nur Daten oder Aktualisierung) nicht verfügbar war.</p></td>
</tr>
</tbody>
</table>
<p> </p>
<strong>Bereinigen</strong>
<p><strong>/noautoexit</strong>: in Windows 10 nicht verwendet. In Windows 8.1 Wenn ein Fehler gefunden wird, Windows Setup nicht beendet, aber stattdessen beendet und auf dem Setupbildschirm bleibt, bis der Benutzer das Problem behandelt. Die Installation von diesem Zeitpunkt an ist teilnahmen.</p>
<p><strong>/performDU</strong>: in Windows 10 nicht verwendet. Windows 8.1 überprüft Windows Setup für dynamische Updates für Windows Setup.</p>
<p><strong>Beispiele:</strong></p>
<pre class="syntax" space="preserve"><code>Setup /auto clean 
Setup /auto dataonly 
Setup /auto upgrade</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ BusParams:</strong><em>&lt;bus.device.function&gt;</em></p></td>
<td align="left"><p>Gibt die PCI-Adresse des ein 1394, USB- oder NET debug-Port. Die Bus, Gerät, und Zahlen Funktion müssen im Dezimalformat sein. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /busparams:0.29.7 </code></pre>
<p>Weitere Informationen finden Sie unter [Einrichten Kernel-Debuggings mit USB 2.0](http://go.microsoft.com/fwlink/?LinkId=317360).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ CompactOS</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Gibt an, ob die Funktion Compact OS Festplattenspeicher gespeichert. Standardmäßig bestimmt Windows Setup, ob dieses Feature automatisch verwenden können.</p>
<p><strong>Aktivieren</strong>: Setup installiert Windows mithilfe der komprimierten-Systemdateien.</p>
<p><strong>Deaktivieren von</strong>: Setup installiert Windows mithilfe der nicht komprimierten Systemdateien</p>
<p>Weitere Informationen zum Compact OS finden Sie unter [Compact OS Single instancing und Optimierung Bild](compact-os.md).</p>
<pre class="syntax" space="preserve"><code>Setup /compactos enable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Compat</strong> {<strong>IgnoreWarning</strong> | <strong>ScanOnly</strong>}</p></td>
<td align="left"><p><strong>IgnoreWarning</strong>: Abschluss des Setups Installation, ignorieren alle Nachrichten, die zwar Kompatibilität</p>
<p><strong>ScanOnly</strong>: Windows Setup über Kompatibilität Überprüfungen ausgeführt wird und mit einem Exitcode, um anzugeben, ob alle Kompatibilitätsprobleme vorhanden sind (ohne den Abschluss der Installation) beendet. Wenn keine Probleme gefunden werden, wird Setup 0xC1900210 zurückgegeben. Wenn Kompatibilitätsprobleme gefunden werden, wird Setup 0xC1900208 zurückgegeben.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /compat /IgnoreWarning</code></pre>
<p>Wenn Sie Setup mit starten <code>/Compat ScanOnly</code>:</p>
<ul>
<li>Wenn alle Compat Problem nicht findet, wird MOSETUP_E_COMPAT_SCANONLY (0xC1900210) zurückgegeben.</li>
<li>Findet bearbeitungsfähige Compat Probleme, wie Apps wird MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208) zurückgegeben.</li>
<li>Wenn sie feststellt, dass die Mig-Auswahl nicht verfügbar ist, wird MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204) zurückgegeben.</li>
<li>Wenn es, dass der Computer nicht für Windows 10 berechtigt ist feststellt, wird MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200) zurückgegeben.</li>
<li>Wenn es, dass diesen Computer nicht genügend freien Speicherplatz findet für die Installation vorhanden ist, wird MOSETUP_E_INSTALLDISKSPACE_BLOCK (0xC190020E) zurückgegeben.</li>
</ul>
<p>Dieser Befehl funktioniert mit anderen Optionen. Beispiel für das Ausführen von Setup im Hintergrund ohne Benutzeroberfläche:</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly</code></pre>
<p>Allgemeine Haftungsausschlüsse in der Benutzeroberfläche, beispielsweise Sprache Änderungen ignorieren:</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning</code></pre>
<p>In den meisten Fällen, möchte ein Administrator die Compat XML betrachten, wenn Setup Compat Probleme gefunden. Für die der Administrator Kopie Protokolle Flag können sogar Setupprotokolle erfassen:</p>
<pre class="syntax" space="preserve"><code>Setup /Auto Upgrade /Quiet /Compat ScanOnly /Compat IgnoreWarning /CopyLogs &lt;folder_path&gt; </code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ CopyLogs</strong><em>&lt;Speicherort&gt;</em></p></td>
<td align="left"><p>Setup kopieren oder Hochladen von logs(compressed) bei Auftreten eines Fehlers an der angegebenen Position (vorausgesetzt, Computerbenutzer/Berechtigung und Netzwerkzugriff auf Pfad hat).</p>
<p>Akzeptierte Parameter sind lokale Dateipfade und Netzwerkpfade UNC an.</p>
<div class="alert">
<strong>Hinweis</strong>  Dies wird im Systemkontext ausgeführt, sodass es möglicherweise nicht Berechtigungen an Speicherorte zu kopieren, die Benutzerberechtigungen erfordern.
</div>
<div>
 
</div>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /copylogs \\server\share\ </code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Debug:</strong><em>&lt;Port&gt; </em> [<strong>BaudRate:</strong><em>&lt;Baudrate&gt;</em>]</p></td>
<td align="left"><p>Ermöglicht das Kernel-debugging über einen Kommunikationsport (COM), wenn Windows ausgeführt wird und während der [WindowsPE](windowspe.md) Konfiguration Durchlauf von Windows Setup.</p>
<p><em>&lt;Port&gt; </em> gibt den debugging Port. Der Standardwert für <em> &lt;Port&gt; </em> ist <strong>1</strong>.</p>
<p>[<strong>Baudrate:</strong><em>&lt;Baudrate&gt; </em> gibt die Baudrate beim Windows während des Debuggens Datenübertragungen verwendet werden. Die Standardeinstellung ist <strong>19200</strong>. Sie können auch Festlegen der <em> &lt;Baudrate&gt; </em> auf <strong>57600</strong> oder <strong>115200</strong>festlegen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /1394debug:1 /baudrate:115200</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Dynamische Updates</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Gibt an, ob Setup dynamisches Update-Operationen (Suche, herunterladen und Installieren von Updates) ausgeführt werden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /DynamicUpdate disable </code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ EMSPort:</strong> {<strong>COM1</strong> | <strong>COM2</strong> || <strong>off</strong>} [<strong>/emsbaudrate:</strong><em>&lt;Baudrate&gt;</em>]</p></td>
<td align="left"><p>Aktiviert oder deaktiviert (Emergency Management Services, EMS) während der Installation von Windows und nachdem das Serverbetriebssystem installiert wurde. Die folgenden Argumente dienen zum Angeben des Verhaltens der zur Abstimmung während der Installation von Windows.</p>
<p><strong>COM1</strong> zur Abstimmung über COM1 ermöglicht. Für X86 unterstützt nur Systeme.</p>
<p><strong>COM2</strong> zur Abstimmung über COM2 ermöglicht. Für X86 unterstützt nur Systeme.</p>
<p><strong>Usebiossettings</strong> verwendet die Einstellung, die das BIOS angibt. Für X86 Systeme, Windows verwendet den Wert aus der Tabelle Serial Port Console-Umleitung (SPCR). Wenn keine SPCR-Tabelle oder EFI Konsole Gerätepfad im BIOS angegeben ist, wird Windows <strong>Usebiossettings</strong>deaktiviert. <strong>Usebiossettings</strong></p>
<p><strong>deaktiviert</strong> zur Abstimmung deaktiviert. Wenn zur Abstimmung in Windows-Setup deaktiviert ist, können Sie später zur Abstimmung aktivieren, indem Sie die Boot-Einstellungen ändern.</p>
<p></p>
<p>[<strong>/emsbaudrate:</strong><em>&lt;Baudrate&gt;</em>] Gibt die Baudrate beim Windows während des Debuggens Datenübertragungen verwendet werden. Der Standardwert ist <strong>19200</strong>an. Sie können auch Festlegen der <em> &lt;Baudrate&gt; </em> Einstellung kann auch auf <strong>57600</strong> oder <strong>115200</strong>festgelegt werden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /emsport:COM1 /emsbaudrate:115200</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ InstallDrivers</strong><em>&lt;Speicherort&gt;</em></p></td>
<td align="left"><p>Die Neuinstallation von Windows 10 hinzugefügt INF-Schreibweise Treiber. Die Treiber INF kann in einem Ordner innerhalb der angegebenen Position entsprechen. Der Befehl wird über den angegebenen Speicherort rekursiv. Beispiel:</p>
<p>Akzeptierte Parameter sind ein lokaler Pfad oder UNC Netzwerkpfad zu einem Ordner, der INF-Dateien enthält.</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /installdrivers C:\Fabrikam\drivers /noreboot </code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ InstallFrom</strong> <em>&lt;Pfad&gt;</em></p></td>
<td align="left"><p>Gibt eine andere Install.wim Datei während der Installation von Windows verwenden. Dadurch können Sie eine einzelne Vorinstallation Umgebung verwenden, um mehrere Versionen der Windows-Abbilder installieren. Eine 32-Bit-Version des Windows-Setups können Sie beispielsweise eine 64-Bit-Windows-Abbild bereit. Sie können auch eine Antwortdatei für plattformübergreifende Bereitstellungen verwenden. Weitere Informationen finden Sie unter "Erstellen eines WIM für mehrere Architekturtypen" in [Windows Setup unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md).</p>
<p><em>&lt;Pfad&gt; </em> gibt den Pfad der WIM-Datei zu installieren. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /installfrom D:\custom.wim</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ InstallLangPacks</strong><em>&lt;Speicherort&gt;</em></p></td>
<td align="left"><p>Die Neuinstallation von Windows 10 hinzugefügt Language Packs (lp.cab).</p>
<p>Die Sprachpakete können in einem Ordner innerhalb der angegebenen Position sein. Der Befehl installiert alle lp.cab Dateien und Sprachfunktionen wie Text-Sprach-Erkennung in die Ordner und Unterordner an der angegebenen Position ein.</p>
<p>Akzeptierte Parameter sind ein lokaler Pfad oder UNC Netzwerkpfad zu einem Ordner, der INF-Dateien enthält.</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /installlangpacks C:\Fabrikam\Languages\French /noreboot</code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>m:</strong><em>&lt;Ordnername&gt;</em></p></td>
<td align="left"><p>Weist Setup alternative Dateien von einem anderen Speicherort kopieren. Diese Option weist Setup zuerst in alternativen Speicherort suchen und, wenn Dateien sind vorhanden, um diese anstelle der Dateien aus dem Speicherort verwenden.</p>
<p><em>&lt;Ordnername&gt; </em> gibt den Namen und den Speicherort des Ordners, den enthält die Replacement-Dateien und einem lokalen Laufwerk Standort dargestellt werden kann. UNC-Pfade werden nicht unterstützt.</p>
<p>Sie müssen wissen, wo die Dateien auf der Windows-Installation installiert werden sollen. Alle zusätzlichen Dateien müssen kopiert werden, in einen $OEM$-Ordner in Ihrem Installationsquellen oder in der <em> &lt;Ordnername&gt;</em>. Die $OEM$ Struktur enthält eine Darstellung der Ziel-Installations-CD. Beispiel:</p>
<pre class="syntax" space="preserve"><code>$OEM$\$1</code></pre>
<p>Maps SYSTEMLAUFWERK %, die Laufwerk c: festgelegt. werden konnte</p>
<pre class="syntax" space="preserve"><code>$OEM$\$$</code></pre>
<p>Ordnet % windir%, der C:\windows\ werden konnte.</p>
<pre class="syntax" space="preserve"><code>$OEM$\$progs</code></pre>
<p>wird das Verzeichnis für Programmdateien.</p>
<pre class="syntax" space="preserve"><code>$OEM$\$docs</code></pre>
<p>Benutzerordner Eigene Dateien wird.</p>
<p>Erstellen beispielsweise um eine aktualisierte C:\Program Files\Messenger\Msmsgs.exe Datei in der Windows-Installation kopieren, die folgende Ordnerstruktur auf den Pro\Sources\$OEM$\$Progs\Messenger\Msmsgs.exe Installationsquelle mithilfe des Befehls <strong>Setup</strong> :</p>
<pre class="syntax" space="preserve"><code>Pro\sources\setup.exe /m</code></pre>
<p>Wenn Sie eine Datei ersetzen, Windows-Datei Protection schützt, müssen Sie auch die aktualisierte Datei kopieren, in die lokalen Quellen mit Windows installiert werden soll. Beispielsweise können Sie die Datei in den Ordner C:\Windows\i386 kopieren. Der Dateiname muss identisch mit dem Namen, die im Windows-Setup verwendet wird. Fügen Sie beispielsweise die folgenden Dateien und Ordner-Struktur zum Verzeichnis$ $OEM hinzu:</p>
<pre class="syntax" space="preserve"><code>Pro\sources\$OEM$\$$\i386\msmsgs.ex_</code></pre>
<p>Wenn Sie Dateien, die nicht auf einer Installationsfreigabe sind verwenden, müssen Sie den Namen des Ordners angeben. In diesem Beispiel wird der <em> &lt;Ordnername&gt; </em> C:\additional_files ist:</p>
<pre class="syntax" space="preserve"><code>Setup /m:C:\additional_files</code></pre>
<p>wobei C:\additional_files die angepasste $OEM$ Directory ist. Beispiel:</p>
<pre class="syntax" space="preserve"><code>C:\additional_files\$$\i386\msmsgs.ex_</code></pre>
<p>Wenn Sie Ressourcen in den Ersatzdateien ändern, müssen Sie die aktualisierten Multilanguage User Interface (MUI)-Dateien für die Installation hinzufügen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ MigrateDrivers</strong> {<strong>Alle</strong> | <strong>keine</strong>}</p></td>
<td align="left"><p>Weist Setup an, ob die Treiber aus der vorhandenen Installation während des Upgrades zu migrieren. Sie können <strong>Alle</strong> oder <strong>keine</strong>festlegen. Standardmäßig entscheidet Setup die für jeden einzelnen Treiber basierend auf der Auswahl Installation am besten geeignet ist.</p>
<p>Sie können mit <strong>/installdrivers</strong>, diese Option verwenden, obwohl es nicht erforderlich ist.</p>
<pre class="syntax" space="preserve"><code>Setup /auto upgrade /migratedrivers all 
Setup /auto upgrade /migratedrivers none /installdrivers N:\NewDrivers</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ NetDebug:</strong>Hostip =&lt;<em>w.x.y.z</em>&gt;, Port =&lt;<em>n</em>&gt;, Key =&lt;<em>q.r.s.t</em>&gt;[, Nodhcp] [, Busparams =<em>n.o.p</em>]</p></td>
<td align="left"><p>Ermöglicht das Kernel-debugging über das Netzwerk.</p>
<p>Verwenden Sie Hostip, um die IP-Adresse des Hostcomputers zu identifizieren.</p>
<p>Verwenden Sie Port, um den Port zu identifizieren. Der Standardport für den Start ist 49152 und der End-Standardport ist 65535. </p>
<p>Schlüssel verwenden, geben Sie ein Kennwort, um eine sichere Verbindung einzurichten.</p>
<p>Verwenden Sie zum Vermeiden der Verwendung von DHCP-Verbindung Nodhcp. (optional)</p>
<p>Verwenden Sie Busparams um die Bus-Nummer sowie die Nummer des Geräts und die Funktion Anzahl ein Adapter für ein bestimmtes PCI-Bus-Gerät auszuwählen. (optional)</p>
<p>Beispiele für die:</p>
<pre class="syntax" space="preserve"><code>setup /netdebug:hostip=10.125.4.86,port=50000,key=0.0.0.0 
setup /netdebug:hostip=10.125.4.86,port=50000,key=abcdefg.123.hijklmnop.456,nodhcp 
setup /netdebug:hostip=10.125.4.86,port=50000,key=dont.use.previous.keys,busparams=1.5.0</code></pre>
<p>Weitere Informationen hierzu finden Sie unter [Einrichten im Kernelmodus Debuggens über ein Netzwerk Kabel manuell](http://go.microsoft.com/fwlink/p/?linkid=317384).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ NoReboot</strong></p></td>
<td align="left"><p>Weist Windows Setup nicht für den Computer neu starten, nachdem die kompatible Phase der Windows-Installation abgeschlossen ist. Die Option <strong>noreboot</strong> können Sie weitere Befehle ausführen, bevor Sie Windows neu gestartet wird. Diese Option wird nur den ersten Neustart unterdrückt. Die Option unterdrückt keine nachfolgenden Neustarts. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /noreboot</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Primärschlüssel</strong> <em>&lt;Product Keys&gt;</em></p></td>
<td align="left"><p>Stellt Setup mit der Product Key ein. Beispiel:</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /pkey xxxxx-xxxxx-xxxxx-xxxxx-xxxxx </code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ PostOOBE</strong><em>&lt;Speicherort&gt;</em>[<strong>\setupcomplete.exe</strong>]</p></td>
<td align="left"><p>Nach Abschluss des Setups führen Sie ein Skript aus.</p>
<p>Akzeptierte Parameter sind ein lokaler Pfad oder Netzwerkpfad UNC, in eine Datei mit dem Namen setupcomplete.cmd oder in einen Ordner, der setupcomplete.cmd enthält.</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postoobe c:\Fabrikam\setupcomplete.cmd</code></pre>
<p>Pfad zum Ordner, die ein Skript mit dem Namen enthält: <strong>setupcomplete.cmd</strong>: kopiert den gesamten Inhalt des Ordners in $Windows. ~ BT nach OOBE ausgeführt werden.</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postoobe c:\Fabrikam\</code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ PostRollback</strong><em>&lt;Speicherort&gt;</em>[<strong>\setuprollback.exe</strong>]</p></td>
<td align="left"><p>Wenn der Benutzer ihre Version von Windows zurückgesetzt wird, führen Sie ein Skript.</p>
<p>Akzeptierte Parameter sind ein lokaler Pfad oder Netzwerkpfad UNC in eine Datei namens setuprollback.cmd oder in einen Ordner, der setuprollback.cmd enthält.</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postrollback c:\Fabrikam\setuprollback.cmd</code></pre>
<p>Pfad zum Ordner, die ein Skript mit dem Namen enthält: <strong>setuprollback.cmd</strong>: kopiert den gesamten Inhalt des Ordners in $Windows. ~ BT nach OOBE ausgeführt werden.</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /postrollback \\server\share</code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Quiet</strong></p></td>
<td align="left"><p>Dadurch wird eine Setup-Benutzeroberfläche die Rollback-Benutzeroberfläche einschließlich unterdrückt. Beispiel:</p>
<pre class="syntax" space="preserve"><code>setup /auto upgrade /quiet</code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ReflectDrivers</strong><em>&lt;Speicherort&gt;</em></p></td>
<td align="left"><p>Gibt den Pfad zu einem Ordner, die Verschlüsselung Treiber für einen Computer mit Drittanbieter-Verschlüsselung aktiviert ist.</p>
<pre class="syntax" space="preserve"><code>Setup /ReflectDrivers &lt;folder_path&gt; </code></pre>
<p>Diese Einstellung ist für Windows-10, Version 1607 neu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ ResizeRecoveryPartition</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Gibt an, ob es OK, um die Größe der vorhandenen Partition Windows Recovery Environment (Windows RE) oder eine neue während der Installation erstellt wird.</p>
<p><strong>Aktivieren Sie</strong>: Windows können während der Installation Ändern der Größe der vorhandenen Windows RE-Tools Partition oder einen neuen Anwendungspool erstellen, bei Bedarf.</p>
<p><strong>Deaktivieren von</strong>: Windows nicht ändern Sie die Größe der vorhandenen Windows RE-Tools Partition oder erstellen Sie einen neuen Anwendungspool während der Installation.</p>
<p>Weitere Informationen zu Windows RE Partitionen finden Sie unter [UEFI/GPT-basierten Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md) und [BIOS/MBR-basierte-Partitionen](configure-biosmbr-based-hard-drive-partitions.md).</p>
<pre class="syntax" space="preserve"><code>Setup /resizerecoverypartition disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ShowOOBE</strong> {<strong>vollständigen</strong> | <strong>keine</strong>}</p></td>
<td align="left"><p><strong>vollständige</strong>: bewirkt, dass den Benutzer für die Durchführung interaktiv außerhalb der Box-Experience (OOBE).</p>
<p><strong>keine</strong>: überspringt OOBE und wählt die Standardeinstellungen.</p>
<p>Beispiel:</p>
<pre class="syntax" space="preserve"><code>setup.exe /auto upgrade /showoobe full</code></pre>
<p>Diese Einstellung ist für Windows 10 neu.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Telemetrie</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Gibt an, ob Windows Setup Installation Daten und erfassen soll.</p>
<p><strong>Aktivieren</strong>: Setup erfasst und Berichte Installationsdaten.</p>
<p><strong>Deaktivieren von</strong>: Es wird nicht Erfassung und Bericht Installationsdaten.</p>
<pre class="syntax" space="preserve"><code>Setup /telemetry disable</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ TempDrive</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Weist Windows Setup an temporären Dateien auf der angegebenen Partition zu platzieren. Für ein Upgrade der <strong>/tempdrive:</strong> Option betrifft nur die Platzierung der temporären Dateien. Das Betriebssystem wird in der Partition aktualisiert, von dem Sie die Datei Setup.exe ausführen.</p><p>Der Parameter/tempdrive steht in Windows-10, Version 1607, jedoch ist nicht verfügbar in früheren Versionen von Windows-10.</p>
<p><em>&lt;Laufwerkbuchstabe&gt; </em> gibt die Partition, um während der Installation der Windows-Installationsdateien zu kopieren. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /tempdrive:H</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Für die unbeaufsichtigte Installation:</strong><em>&lt;Antwortdatei</em>&gt;</p></td>
<td align="left"><p>Können Sie eine Antwortdatei mit Windows Setup verwenden. Dies wird als unbeaufsichtigte Installation bezeichnet. Geben Sie einen Wert für <em> &lt;Antwortdatei&gt;</em>. Windows-Setup wendet die Werte in die Antwortdatei während der Installation.</p>
<p><em>&lt;Antwortdatei&gt; </em> gibt den Pfad und Dateinamen der unbeaufsichtigten Windows Setup Antwortdatei.</p>
<pre class="syntax" space="preserve"><code>Setup /unattend:\\server\share\unattend.xml</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Uninstall</strong> {<strong>Aktivieren</strong> | <strong>Deaktivieren</strong>}</p></td>
<td align="left"><p>Bestimmt, ob Windows Steuerelemente, die dem Benutzer einschließt, um das vorherige Betriebssystem wieder zu ermöglichen.</p>
<p>Diese Einstellung ist für Windows 10 neu.</p>
<pre class="syntax" space="preserve"><code>Setup /uninstall disable</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ USBDebug:</strong><em>&lt;Hostname&gt;</em></p></td>
<td align="left"><p>Richtet das debugging auf einem USB-Anschluss. Debugdaten sind beim nächsten Neustart wirksam.</p>
<p><em>&lt;Hostname&gt; </em> gibt den Namen des Computers zu debuggen. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Setup /usbdebug:testmachine01</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ WDSDiscover</strong></p></td>
<td align="left"><p>Gibt an, dass der Windows Deployment Services (WDS) Client sein sollen Modus ermitteln.</p>
<p>Wenn Sie mit dieser <strong>Option/WDSServer</strong> nicht angeben, sucht WDS für einen Server. Diese dynamische entdecken beispielsweise so starten Sie den WDS-Client in Modus, führen Sie den folgenden Befehl:</p>
<pre class="syntax" space="preserve"><code>Setup /wds /wdsdiscover</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ WDSServer:</strong><em>&lt;Servername&gt;</em></p></td>
<td align="left"><p>Gibt den Namen des Windows-Bereitstellungsdienst-Servers, den der Client eine Verbindung herstellen soll.</p>
<p>Sie müssen auch verwenden, um diese Einstellung zu verwenden, die <code>/wdsdiscover</code> Option.</p>
<p><em>&lt;Servername&gt; </em> kann eine IP-Adresse, einen NetBIOS-Namen oder einen vollqualifizierten Domänennamen (FQDN) sein. Windows-Bereitstellungsdienst-Client in dieser statischen entdecken beispielsweise so starten Sie Modus, führen Sie den folgenden Befehl:</p>
<pre class="syntax" space="preserve"><code>Setup /wds /wdsdiscover /wdsserver:MyWDSServer</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows-Setup-Status](windows-setup-states.md)

[Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

[Windows-Setup-Protokolldateien und Ereignisprotokolle](windows-setup-log-files-and-event-logs.md)

 

 
