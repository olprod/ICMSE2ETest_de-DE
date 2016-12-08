---
author: Justinha
Description: Sysprep-Befehlszeilenoptionen
ms.assetid: b20ee6ea-b1c4-4cd2-91ea-52f667a704bb
MSHAttr: PreferredLib:/library/windows/hardware
title: Sysprep-Befehlszeilenoptionen
ms.openlocfilehash: 4c0c7316f8e48e79c26851b07726352d379a5c1c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-command-line-options"></a>Sysprep-Befehlszeilenoptionen


Führen Sie **Sysprep** zum Vorbereiten einer Windows-Installations erst erfasst werden. In diesem Thema wird die Befehlszeilensyntax für das Tool System Preparation (Sysprep).

Wenn Sie ein Abbild der Installation für die Bereitstellung auf einem anderen Computer erstellen möchten, müssen Sie den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** ausführen, selbst wenn der anderen Computer die gleiche Hardwarekonfiguration verfügt. Die **Sysprep / verallgemeinern** Befehl eindeutigen Informationen aus der Windows-Installation entfernt, sodass Sie das Abbild auf einem anderen Computer sicher wiederverwenden können. Beim nächsten Starten des Windows-Abbilds wird die Konfiguration [specialize](specialize.md) Durchlauf ausgeführt.

## <a name="span-idsysprepcommand-lineoptionsspanspan-idsysprepcommand-lineoptionsspanspan-idsysprepcommand-lineoptionsspansysprep-command-line-options"></a><span id="Sysprep_Command-Line_Options"></span><span id="sysprep_command-line_options"></span><span id="SYSPREP_COMMAND-LINE_OPTIONS"></span>Sysprep-Befehlszeilenoptionen


Die folgenden Befehlszeilenoptionen sind für Sysprep verfügbar:

**Sysprep.exe** \[ **/Oobe** | **/audit**\]

\[**/ Verallgemeinern**\]

\[**/Mode:VM**\]

\[**/ Neustart** | **/Shutdown** | **/ Beenden**\]

\[**/ quiet**\]

\[**/ für die unbeaufsichtigte Installation:***&lt;Antwortdatei&gt;*\]

In der folgenden Tabelle sind die Sysprep-Befehlszeilenoptionen aufgeführt:

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
<td align="left"><p><strong>/ Audit</strong></p></td>
<td align="left"><p>Neustart des Computers im Überwachungsmodus an. Im Überwachungsmodus können Sie zusätzliche Treiber oder Anwendungen zu Windows hinzufügen. Sie können auch eine Installation von Windows testen, bevor Sie die Installation an Endbenutzer senden. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Sysprep /audit</code></pre>
<p>Wenn Sie eine Antwortdatei angeben, wird vom Überwachungsmodus von Windows Setup Konfigurationsphasen [AuditSystem](auditsystem.md) und [AuditUser](audituser.md) ausgeführt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Verallgemeinern</strong></p></td>
<td align="left"><p>Bereitet die Windows-Installation zum Erstellen eines Abbilds vor. Sysprep entfernt alle eindeutigen Systeminformationen aus der Windows-Installation. Sysprep setzt die Sicherheits-ID (SID), werden alle Wiederherstellungspunkte gelöscht und Ereignisprotokolle löscht. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /shutdown</code></pre>
<p>Beim nächsten des Computers starten führt die Konfiguration [specialize](specialize.md) übergeben. Übergeben Sie die Konfiguration erstellt eine neue Sicherheits-ID (SID).</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ OOBE</strong></p></td>
<td align="left"><p>Neustart des Computers in den OOBE-Modus. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /shutdown /oobe</code></pre>
<p>OOBE ermöglicht Endbenutzern auf ihre Windows-Betriebssystem anpassen, Erstellen von Benutzerkonten, nennen Sie den Computer und andere Aufgaben ausführen. Sysprep Prozesse übergeben Sie alle Einstellungen in die Konfiguration [OobeSystem](oobesystem.md) eine Antwortdatei bevor OOBE beginnt.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/Mode:VM</strong></p></td>
<td align="left"><p>Verallgemeinert eine Virtual Hard Disk (VHD), sodass Sie als eine virtuelle Festplatte auf dem gleichen Virtual Machine (VM) oder dem Hypervisor die virtuelle Festplatte bereitstellen können. Nach dem Neustart der VM wird kann die VM OOBE starten. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Sysprep /generalize /oobe /mode:vm</code></pre>
<p>Befehlszeilenoptionen für die nur zusätzlichen VM-Modus gilt <strong>sind/neu starten</strong>, <strong>Shutdown</strong>und <strong>/ Beenden</strong>. Sie müssen die virtuelle Festplatte auf einer Virtual Machine (VM) oder mit demselben Hardwareprofil Hypervisor bereitstellen. Angenommen, wenn Sie in Microsoft Hyper-V VHD-DATEI erstellt, können Sie nur Ihre VHD Microsoft Hyper-V VM mit einem übereinstimmenden Hardwareprofil bereitstellen. Bereitstellung der virtuellen Festplatte in einer anderen VM mit einem anderen Hardwareprofil möglicherweise unerwartete Probleme.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Sie können nur VM-Modus innerhalb eines virtuellen Computers ausführen.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Reboot</strong></p></td>
<td align="left"><p>Startet den Computer neu. Sie können diese Option verwenden, um den Computer zu überwachen und zu überprüfen, ob die erste Ausführung korrekt funktioniert.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Shutdown</strong></p></td>
<td align="left"><p>Fährt den Computer ein, nachdem Sie der Befehl <strong>Sysprep</strong> beendet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ quiet</strong></p></td>
<td align="left"><p>Das Sysprep Tool wird ausgeführt, ohne dass auf dem Bildschirm angezeigt wird die Nachricht zur Bestätigung. Sie können diese Option verwenden, wenn Sie das Tool Sysprep automatisieren.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Beenden</strong></p></td>
<td align="left"><p>Schließt das Sysprep-Tool ohne neu zu starten oder Herunterfahren des Computers ein, nachdem Sysprep die angegebenen Befehle ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ für die unbeaufsichtigte Installation:</strong><em>&lt;Antwortdatei&gt;</em></p></td>
<td align="left"><p>Windows-Einstellungen in einer Antwortdatei betrifft, bei einer unbeaufsichtigten Installation, wobei <em> &lt;Antwortdatei&gt; </em> gibt den Pfad und den Namen der Antwortdatei verwendet. Beispiel:</p>
<pre class="syntax" space="preserve"><code>Sysprep /audit /reboot /unattend:F:\Unattend.xml</code></pre>
<p>wobei <em>F</em> der Laufwerkbuchstabe des Speichergeräts tragbaren ist, auf dem sich die Antwortdatei (Unattend.xml) befindet.</p></td>
</tr>
</tbody>
</table>

 

**Wichtige**  
Sie müssen verwenden die **Sysprep / verallgemeinern** Befehl aus, um eine vollständige Installation von Windows verallgemeinern, bevor Sie die Installation für die Bereitstellung auf einem neuen Computer verwenden können, ob Sie Imaging, Festplattenduplizierung oder eine andere Methode verwenden. Verschieben oder Kopieren eines Windows-Abbilds auf einen anderen Computer ohne Ausführung der **Sysprep / verallgemeinern** Befehl wird nicht unterstützt.

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md)

[Sysprep-Prozess (Übersicht)](sysprep-process-overview.md)

[Sysprep (verallgemeinern) einer Windows-installation](sysprep--generalize--a-windows-installation.md)

[Sysprep-Unterstützung für Serverrollen](sysprep-support-for-server-roles.md)

[Verwenden von Antwortdateien mit Sysprep](use-answer-files-with-sysprep.md)

 

 






