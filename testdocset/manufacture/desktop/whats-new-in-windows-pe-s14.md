---
author: Justinha
Description: What's New in Windows PE
ms.assetid: db434eb7-ef16-4edc-af6a-f0057c86a56e
MSHAttr: PreferredLib:/library/windows/hardware
title: What's New in Windows PE
ms.openlocfilehash: b9c3b6d71ea70261617bc2a6ceee9350f59d47b2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-windows-pe"></a>Was ist neu in Windows PE


In diesem Thema wird die neue und geänderte Funktionalität der Windows-Vorinstallation-Umgebung (Windows PE/Windows PE) beschrieben und verglichen mit früheren Versionen von Windows PE und MS-DOS.

## <a name="span-idnewandchangedfunctionalityspanspan-idnewandchangedfunctionalityspanspan-idnewandchangedfunctionalityspannew-and-changed-functionality"></a><span id="New_and_Changed_Functionality"></span><span id="new_and_changed_functionality"></span><span id="NEW_AND_CHANGED_FUNCTIONALITY"></span>Neue und geänderte Funktionalität


Diese Tabelle werden die Features und Funktionen, mit denen der vorherigen Versionen von Windows PE verglichen:

<table>
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Feature</th>
<th align="left">Windows PE für Windows 10</th>
<th align="left">Windows PE 5.0</th>
<th align="left">Windows PE 4.0</th>
<th align="left">Windows PE 3.x</th>
<th align="left">Windows PE 2.x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Betriebssysteme bereitgestellt</p></td>
<td align="left"><p>Windows 10, Windows 8.1, Windows Server 2012 R2, Windows 8, WindowsServer 2012, Windows 7 oder Windows Server 2008 R2.</p></td>
<td align="left"><p>Windows 8.1, Windows Server 2012 R2, Windows 8, WindowsServer 2012, Windows 7 oder Windows Server 2008 R2.</p>
<p>Nicht unterstützt: Windows Vista oder WindowsServer 2008.</p></td>
<td align="left"><p>Windows 8, WindowsServer 2012, Windows 7, Windows Server 2008 R2, Windows Vista oder WindowsServer 2008.</p></td>
<td align="left"><p>Windows 7, Windows Server 2008 R2, Windows Vista oder WindowsServer 2008.</p></td>
<td align="left"><p>Windows Vista oder WindowsServer 2008</p></td>
</tr>
<tr class="even">
<td align="left"><p>Skripts zum Bereitstellen von Windows PE</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>CopyPE für die Verwendung mit Windows ADK aktualisiert.</p>
<p>MakeWinPEMedia hinzugefügt haben, um die Erstellung von USB flash-Laufwerke oder ISO-Dateien einfacher zu machen.</p></td>
<td align="left"><p>CopyPE und Oscdimg Tools enthalten.</p></td>
<td align="left"><p>CopyPE und Oscdimg Tools enthalten.</p>
<p>Windows PE 2.1: Oscdimg Tool aktualisiert, um größere Bilder unterstützen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Skripting-tools</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>.NET Framework optionale Komponente in WinPE_NetFx umbenannt.</p>
<p>Optionale Komponente PowerShell in WinPE_PowerShell umbenannt.</p>
<p>Winpeshl.ini können Sie apps mit Befehlszeilen-Parametern in Anführungszeichen zu starten. Weitere Informationen finden Sie unter [Winpeshl.ini Verweis: Starten eine app beim Start von Windows PE](winpeshlini-reference-launching-an-app-when-winpe-starts.md).</p></td>
<td align="left"><p>.NET Framework 4.5 optionale Komponente hinzugefügt (WinPE_NetFx4).</p>
<p>PowerShell 3.0 optionale Komponente hinzugefügt (WinPE_PowerShell3).</p></td>
<td align="left"><p>Scripting Befehlszeilentools enthalten.</p></td>
<td align="left"><p>Scripting Befehlszeilentools enthalten.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Bild zu erfassen und Wartung von tools</p></td>
<td align="left"><p>DISM unterstützt Windows 10 und Features für Windows Imaging und Konfiguration Designer (ICD).</p></td>
<td align="left"><p>DISM unterstützt Windows 8.1 und Windows Server 2012 R2 Bilder jedoch Bilder für Windows Vista oder Windows Server 2008 nicht unterstützt. Weitere Informationen finden Sie unter [DISM - Deployment Image Servicing and Management – technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md).</p></td>
<td align="left"><p>Aufzeichnen von neu datenschutztools <code>dism /Capture-image</code> und <code>dism /Apply-image</code> Befehle.</p>
<p>Wartung Windows 8.1 oder Windows Server 2012 R2 Bilder nicht unterstützt werden.</p></td>
<td align="left"><p>[DISM - Abbildern Bereitstellung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md) hinzugefügt. DISM ist ein Befehlszeilentool, das Sie zum Anpassen einer Windows oder einem Windows PE-Abbild verwenden können.</p>
<p>Die PEImg und Pkgmgr Tools werden in Windows PE 3.0 nicht unterstützt.</p>
<p>ImageX als optional Anwendung zum Aufzeichnen und Anwenden von Bilder zur Verfügung.</p>
<p>Unterstützt keine Wartung Windows 8.1 oder Windows Server 2012 R2 Bilder.</p></td>
<td align="left"><p><strong>PEImg</strong> wird verwendet, um den Dienst Windows PE Bilder.</p>
<p>Nachdem Sie das Bild Windows PE 2.0 <strong>PEImg/prep</strong> ausführen kann nicht das Bild geändert werden.</p>
<p>ImageX steht als optionale Anwendung zum Aufzeichnen und Bilder anwenden.</p>
<p><strong>Pkgmgr</strong> wird verwendet, um zu installieren, entfernen oder Aktualisieren von Windows-Pakete in offline-Images.</p>
<p>Unterstützt keine Wartung Windows 8.1 oder Windows Server 2012 R2 Bilder.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Optimieren von Windows PE</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Das Anwendungsprofil Feature wurde entfernt.</p>
<p>Die standardmäßige Scratch Speicherplatz ist 512 MB für PCs, die mehr als 1 GB RAM verfügen.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Kleinere Standardgröße. Das Standardbild Windows PE 3.0 enthält nur die minimalen Ressourcen zur Unterstützung der meisten Bereitstellungsszenarien. Sie können optionale Komponenten mithilfe von Abbildern Bereitstellung und Verwaltung (DISM) hinzufügen.</p>
<p>Das neue <code>dism /apply-profiles</code> Befehl können Sie den Inhalt eines Windows PE 3.0-Abbilds für weiter zu verringern, nur diese Dateien zur Unterstützung von eines bestimmten Satz von apps erforderlich sind.</p></td>
<td align="left"><p>Windows PE 2.1: Unterstützt direkt von der Festplatte auf RAM-Datenträger nicht starten.</p>
<p>Windows PE 2.1: Schreibbare RAM-Laufwerk: beim Starten von einem schreibgeschützten Medium Windows PE erstellt automatisch einen beschreibbaren RAM-Datenträger (Laufwerk X) und weist 32 Megabyte (MB) RAM-Datenträger für allgemeine Speicher. Sie können die Größe in MB, mithilfe von <strong>PEImg /scratchspace</strong>anpassen. Gültige Werte sind 32, 64, 128, 256 und 512.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dateiverwaltung</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Datei Management optionale Komponente hinzugefügt, die zum Ermitteln und Wiederherstellen von Dateien aus unverschlüsselte Volumes gelöscht.</p></td>
<td align="left"><p>Windows PE 3.1: Basis-Image enthält Verbesserungen, die zur Unterstützung von 4 k/512e Laufwerk verbunden sind.</p></td>
<td align="left"><p>Laufwerk 4k/512e wird nicht unterstützt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arbeitsspeicher</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Maximum unterstützt:</p>
<ul>
<li><p>x 86: 64 GB</p></li>
<li><p>x 64: 4 TB</p></li>
</ul></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Maximum unterstützt:</p>
<ul>
<li><p>x 86: 4 GB</p></li>
<li><p>x 64: 128 GB</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Virtualisierung</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Windows PE 3.0 enthält alle Hyper-V-Treiber außer Treiber angezeigt. Auf diese Weise können Windows PE in Hypervisor ausgeführt. Unterstützte Features gehören Massenspeichergerät, Mausintegration und Netzwerkadapter.</p></td>
<td align="left"><p>Nicht unterstützt.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Netzwerke</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Optionale Remote Netzwerk Treiber Schnittstelle Spezifikation (RNDIS)-Feature für die Aktivierung von Netzwerkgeräten, die die Spezifikation RNDIS über USB implementieren hinzugefügt.</p></td>
<td align="left"><p>Das Windows PE 3.1-base-Abbild enthält RNDIS-Binärdateien.</p>
<p>Windows PE 3.0: [Hotfix](http://support.microsoft.com/kb/972831) für 802.1 X (LAN) verfügbar.</p>
<p>Windows PE 3.1 enthält 802.1 X Binärdateien als optionale Komponente. Der Dateiname des Pakets ist Windows PE-Dot3Svc.cab.</p></td>
<td align="left"><p>Unterstützt IPv4 und IPv6. Unterstützt keine andere Protokolle, wie Internetwork Packet Exchange/Sequenzierte Packet Exchange (IPX/SPX).</p>
<p>Windows PE 2.1: [Hotfix](http://support.microsoft.com/kb/975483) für 802.1 X (LAN) verfügbar.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Wiederherstellung</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>WinRE-Konfigurationsprogramm (winrecfg.exe) zur Unterstützung von Windows RE in einem offline Operating System konfigurieren hinzugefügt.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Unterstützt Windows Recovery Environment (Windows RE).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sicherheit</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Sichern Sie zum Starten des optionale Komponente für das Bereitstellen und Verwalten von BitLocker- und der Trusted Platform Module hinzugefügt.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>BitLocker und vertrauenswürdigen Platform-Modul unterstützt.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Architekturen</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>X86, X64 und ARM-basierte PCs unterstützt.</p></td>
<td align="left"><p>Keine Änderung.</p></td>
<td align="left"><p>X86, X64 und Itanium-basierte PCs unterstützt.</p></td>
</tr>
</tbody>
</table>

 

Um herauszufinden, welche Version von Windows PE Sie ausführen, geben Sie ein `regedit` , und suchen Sie diesen Registrierungsschlüssel: **HKEY\_LOKALE\_COMPUTER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Windows PE**.

## <a name="span-idcomparisonwithms-dosspanspan-idcomparisonwithms-dosspanspan-idcomparisonwithms-dosspancomparison-with-ms-dos"></a><span id="Comparison_with_MS-DOS"></span><span id="comparison_with_ms-dos"></span><span id="COMPARISON_WITH_MS-DOS"></span>Vergleich mit MS-DOS


Windows PE ist vergleichbar mit MS-DOS. Sie umfasst auch Unterstützung für die folgenden Features:

-   Die NTFS-5. *X* -Dateisystem, einschließlich dynamische Datenträger erstellen und verwalten.

-   TCP/IP-Netzwerke und Dateifreigabe (nur Client).

-   32-Bit oder 64-Bit-Windows-Gerätetreiber.

-   Eine Teilmenge der Windows Application programming Interface (API).

-   CD, DVD und USB flash-Laufwerke.

-   Windows-Bereitstellungsdienst-Server.

-   Image-Verwaltung und Wartung (DISM).

-   Hyper-V-Treiber (alle Treiber mit Ausnahme von anzeigen Treiber). Auf diese Weise können Windows PE in einem Hypervisor ausgeführt. Unterstützte Features gehören Massenspeichergerät, Mausintegration und Netzwerkadapter.

-   Optionale Unterstützung für PowerShell, Windows-Verwaltungsinstrumentation (WMI), Windows Data Access Components (Windows DAC) und HTML-Anwendung (HTAs).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

 

 






