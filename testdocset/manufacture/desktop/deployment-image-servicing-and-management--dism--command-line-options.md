---
author: Justinha
Description: Befehlszeilenoptionen von Windows 10 DISM
ms.assetid: 56e2f629-ee86-4ee3-9ba6-f8864cdf4ca3
MSHAttr: PreferredLib:/library/windows/hardware
title: Befehlszeilenoptionen von Windows 10 DISM
ms.openlocfilehash: 9581438c4f342b56f06cf5479a880a8921a82509
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-10-dism-command-line-options"></a>Befehlszeilenoptionen von Windows 10 DISM


Bereitstellung Bild Wartung und Verwaltung (DISM.exe) bindet ein Windows-Abbilddatei (WIM) oder die virtuelle Festplatte (VHD- oder .vhdx) für die Wartung. Sie können DISM auch verwenden, installieren, deinstallieren, konfigurieren und Aktualisieren von Features und Paketen in offline Windows Bilder und offline Windows Vorinstallation Environment (Windows PE) Bilder. Weitere Informationen zu gängigen DISM Szenarien finden Sie unter [Was ist DISM?](what-is-dism.md).

Zusätzlich zu den Befehlszeilentools ist DISM mithilfe von PowerShell verfügbar. Weitere Informationen finden Sie unter [Windows PowerShell-Cmdlets Bereitstellung Imaging – Wartung Management (DISM)](http://go.microsoft.com/fwlink/?LinkId=239926).

DISM ersetzt Tools einschließlich PEImg, Intlcfg, Package Manager und ImageX.

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>In diesem Abschnitt


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)</p></td>
<td align="left"><p>Bild-Management-Befehle wie erfassen, anwenden und Bereitstellen einer Windows-Abbild.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM globale Optionen für Befehlszeilensyntax](dism-global-options-for-command-line-syntax.md)</p></td>
<td align="left"><p>Grundlegende Befehlszeilensyntax und universelle Optionen für die Wartung von Funktionen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM Betriebssystem Paket Befehlszeilenoptionen zum Warten](dism-operating-system-package-servicing-command-line-options.md)</p></td>
<td align="left"><p>Paket – Wartung Befehle zum Hinzufügen, entfernen und Aufzählen CAB und MSU-Paketen und aktivieren, deaktivieren und Aufzählen von Features.</p></td>
</tr>
<tr class="even">
<td align="left">[DISM Provisioning Befehlszeilenoptionen Paket (.ppkg)](dism-provisioning-package-command-line-options.md)</td>
<td align="left"><p>Verwenden der Windows-Pakete (.ppkg) Bereitstellung</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM Funktionen Packen Befehlszeilenoptionen zum Warten](dism-capabilities-package-servicing-command-line-options.md)</p></td>
<td align="left"><p>Funktionen zur Wartung Befehle zum Hinzufügen von Sprachen, .NET und andere Windows-Features.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)</p></td>
<td align="left"><p>Warten Befehle zum Hinzufügen, entfernen und Aufzählen von app-Pakete.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM-Anwendung – Wartung-Befehlszeilenoptionen](dism-application-servicing-command-line-options.md)</p></td>
<td align="left"><p>– Wartung Befehle, die so überprüfen Sie die Verfügbarkeit der Windows Installer-Anwendungspatches (MSP-Dateien) und zum Abfragen der offline-Abbild Informationen zu installierten MSI-Anwendungen und Anwendungspatches (MSP-Dateien) verwendet werden können.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM Standard Anwendung Zuordnung Befehlszeilenoptionen zum Warten](dism-default-application-association-servicing-command-line-options.md)</p></td>
<td align="left"><p>Wartung von Befehlen zum Importieren, exportieren, entfernen und Aufzählen von den Einstellungen, die angeben, welche Anwendung eine Datei basierend auf der Dateierweiterung oder Protokoll wird geöffnet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)</p></td>
<td align="left"><p>International – Wartung Befehle zum Anpassen des internationalen Einstellungen und Konfigurationen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Befehlszeilenoptionen zum Warten DISM-Treiber](dism-driver-servicing-command-line-options-s14.md)</p></td>
<td align="left"><p>Treiber-spezifischen Wartung Befehle zum Hinzufügen, entfernen und Treiber INF-Dateien aufgelistet.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM unbeaufsichtigtes Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)</p></td>
<td align="left"><p>– Wartung Befehle, mit denen eine Unattend.xml-Datei angewendet werden können.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM Windows PE Befehlszeilenoptionen zum Warten](dism-windows-pe-servicing-command-line-options.md)</p></td>
<td align="left"><p>Windows PE-spezifische Wartungsbefehle für Vorbereiten eines Windows PE-Abbilds.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM Windows Edition zum Warten von Befehlszeilenoptionen](dism-windows-edition-servicing-command-line-options.md)</p></td>
<td align="left"><p>Edition – Wartung Befehle für die Version des Windows-Abbilds ändern.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[DISM-Themen (Deployment Image Servicing and Management)](dism-how-to-topics--deployment-image-servicing-and-management.md)

[Was ist DISM?](what-is-dism.md)

 

 






