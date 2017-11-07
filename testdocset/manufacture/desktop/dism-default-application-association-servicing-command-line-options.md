---
author: Justinha
Description: DISM Standard Anwendung Zuordnung Befehlszeilenoptionen zum Warten
ms.assetid: 78cad8f9-2048-48f7-8eb6-44011adbca24
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Standard Anwendung Zuordnung Befehlszeilenoptionen zum Warten
ms.openlocfilehash: bdaa2162794c485ac22e5399a47632484d646c99
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-default-application-association-servicing-command-line-options"></a>DISM Standard Anwendung Zuordnung Befehlszeilenoptionen zum Warten


Die Standard-Zuordnung – Wartung Befehle können Sie importieren, exportieren, Liste, und entfernen die Einstellungen, die angeben, welche Anwendung eine Datei basierend auf dem Dateinamenerweiterung oder Protokoll wird geöffnet.

Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_ Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Die folgenden standardmäßigen Anwendungsoptionen stehen für ein offline-Abbild.

**DISM.exe/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis* &gt; \[ **/Get-DefaultAppAssociations** | **/Import-DefaultAppAssociations** | **/Remove-DefaultAppAssociations**\]

Die folgenden standardmäßigen Anwendung Association-Optionen stehen für ein Betriebssystem ausgeführt wird.

**DISM.exe / Online** \[ **/Export-DefaultAppAssociations** | **/Get-DefaultAppAssociations** | **Import DefaultAppAssociations** | **Remove-DefaultAppAssociations**\]

In der folgenden Tabelle enthält eine Beschreibung der Verwendung jeder Anwendung Zuordnung zum Warten Standardoption. Diese Optionen sind nicht zwischen Groß-und Kleinschreibung.

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
<td align="left"><p><strong>/ Get-Help</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>Wenn unmittelbar nach einer Zuordnung für den Standard-Anwendung – Wartung Befehlszeilenoption verwendet wird, wird die Informationen über die Option und die Argumente angezeigt. Zusätzliche Themen möglicherweise verfügbar, wenn ein Bild festgelegt ist.</p>
<p>Beispiele:</p>
<p><strong>DISM /image:C:\test\offline /Import-DefaultAppAssociations /?</strong></p>
<p><strong>DISM / online /Get-DefaultAppAssociations /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Export-DefaultAppAssociations:</strong>&lt;<em>Path_to_export_file</em>&gt;</p></td>
<td align="left"><p>Die Standard-Anwendung Zuordnungen exportiert aus einem ausgeführten Betriebssystem in eine XML-Datei.</p>
<p>Beispiel:</p>
<p><strong>DISM.exe / Online /Export-DefaultAppAssociations:C:\AppAssoc.xml</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get-DefaultAppAssociations</strong></p></td>
<td align="left"><p>Zeigt die Liste der standardmäßigen Zuordnungen von dienstanwendungen, die im angegebenen Windows-Abbild festgelegt wurden. Diese Option können Sie diese standardanwendung überprüfen, die Zuordnungen für das Bild erfolgreich importiert wurden.</p>
<p>Beispiele:</p>
<p><strong>DISM.exe /Image:C:\test\offline /Get-DefaultAppAssociations</strong></p>
<p><strong>DISM.exe / Online /Get-DefaultAppAssociations</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Import DefaultAppAssociations:</strong>&lt;<em>Path_to_xml_file</em>&gt;</p></td>
<td align="left"><p>Einen Satz von Zuordnungen von dienstanwendungen importiert zu einem angegebenen Windows-Bild aus einer XML-Datei. Die Standard-Anwendung Zuordnungen werden für jeden Benutzer während der ersten Anmeldung angewendet.</p>
<p>Beispiele:</p>
<p><strong>DISM.exe /Image:C:\test\offline /Import-DefaultAppAssociations:C:\AppAssoc.xml</strong></p>
<p><strong>DISM.exe / Online /Import-DefaultAppAssociations:C:\AppAssoc.xml</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Remove-DefaultAppAssociations</strong></p></td>
<td align="left"><p>Entfernt die standardmäßige Anwendung Zuordnungen aus dem angegebenen Windows-Bild.</p>
<p>Beispiele:</p>
<p><strong>DISM.exe /Image:C:\test\offline /Remove-DefaultAppAssociations</strong></p>
<p><strong>DISM.exe / Online /Remove-DefaultAppAssociations</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






