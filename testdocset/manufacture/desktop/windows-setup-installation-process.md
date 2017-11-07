---
author: Justinha
Description: Windows Setup-Installationsvorgang
ms.assetid: e88c0c88-cc6d-436c-a1c0-b109c923ab7e
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows Setup-Installationsvorgang
ms.openlocfilehash: 7114e79a1592618ee4b7aa85e1cb04c7ae647789
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-installation-process"></a>Windows Setup-Installationsvorgang


Windows® Setup ist das Programm, das zur Installation von Windows oder führt ein Upgrade eine vorhandene Windows-Installation. Es ist außerdem die Basis für die Installation und Upgrade folgenden Methoden:

-   Interaktive Installation

-   Automatische installation

-   Windows-Bereitstellungsdienste

In diesem Thema:

-   [Windows-Setup-Installationstyp](#installationtypes)

-   [Windows-Setup-Vorgang](#windowssetupprocess)

## <a name="span-idinstallationtypesspanspan-idinstallationtypesspanspan-idinstallationtypesspan-windows-setup-installation-types"></a><span id="InstallationTypes"></span><span id="installationtypes"></span><span id="INSTALLATIONTYPES"></span>Installationstyp für Windows-Setup


Windows-Setup kann clean und Upgrade-Installationen durchführen. Es führt jedoch keine Computer-zu-Computer-Migrationen. Stattdessen müssen Sie Windows-EasyTransfer, User State Migration Tool (USMT) oder ein anderes Migrationstool verwenden, um Daten aus einer Outlook-Installation für das neue Betriebssystem zu verschieben.

-   **Benutzerdefinierte Installationen.** Windows Setup kann es sich um eine benutzerdefinierte Installation, auch bekannt als einer Neuinstallation, durchführen die speichert der vorherigen Windows-Installations, jedoch die Einstellungen werden nicht migriert. Die vorherige Windows-Installation wird nach einer Neuinstallation nicht gestartet.

-   **Upgrade-Installationen.** Windows-Setup können eine Installation ausgeführt werden, die Ihre Einstellungen und-Voreinstellungen behält während der Aktualisierung des Betriebssystems.

## <a name="span-idwindowssetupprocessspanspan-idwindowssetupprocessspanspan-idwindowssetupprocessspan-windows-setup-process"></a><span id="WindowsSetupProcess"></span><span id="windowssetupprocess"></span><span id="WINDOWSSETUPPROCESS"></span>Windows-Setupvorgang


Das Setup-Programm startet und startet den Computer neu, sammelt Informationen, kopiert Dateien, und erstellt oder Konfigurationseinstellungen passt. In der folgenden Tabelle zeigt den gesamten Vorgang für die Windows-Installation:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Phase der Windows-Installation</th>
<th align="left">Setup-Aktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Speichern als</strong> (für benutzerdefinierte Installationen und Upgrades)</p>
<p>-oder -</p>
<p><strong>Windows PE</strong> (zum Starten der Windows-DVD oder einer benutzerdefinierten Windows PE-Abbild starten)</p></td>
<td align="left"><ol>
<li><p>Geben Sie Windows Setup-Konfigurationen mithilfe von entweder die Windows Setup-Dialogfelder (interaktiv) oder eine Antwortdatei (unbeaufsichtigte) oder eine Kombination aus beidem. Windows-Setup Konfigurationen enthalten einen Product Key hinzufügen und Konfigurieren eines Datenträgers.</p></li>
<li><p>Anwenden von Antwort dateieinstellungen im Durchgang [WindowsPE](windowspe.md) Konfiguration, um die Installation des Verhaltens und benutzerfreundlichkeit konfigurieren.</p></li>
<li><p>Konfigurieren Sie die Festplatte.</p></li>
<li><p>Kopieren Sie das Windows-Abbild auf den Datenträger.</p></li>
<li><p>Vorbereiten der Boot-Informationen.</p></li>
<li><p>Antwort dateieinstellungen im [OfflineServicing](offlineservicing.md) Konfiguration Durchgang zu verarbeiten. Die Einstellungen gelten für das Windows-Abbild vor dieser Windows-Abbilds ausgeführt. Beim Start des Computers zuerst, alle optionalen Komponenten, werden die Treiber, Updates oder Sprachpakete verarbeitet.</p></li>
</ol></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Online-Konfiguration</strong></p></td>
<td align="left"><p>Erstellen Sie spezifische Konfigurationen, die Windows-Installation eindeutige tätigen.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Windows-Willkommensseite</strong></p></td>
<td align="left"><ol>
<li><p>Antwort dateieinstellungen in [der Konfigurationsphase](oobesystem.md) anwenden.</p></li>
<li><p>Inhaltsdatei Einstellungen aus der Datei "Oobe.xml" anwenden.</p></li>
<li><p>Starten Sie Windows-Willkommensseite.</p></li>
</ol></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Automatisieren der Windows-Setup](automate-windows-setup.md)

[Einstellungen für die Automatisierung von OOBE](settings-for-automating-oobe.md)

[Windows-Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md)

[Übersicht über die Automatisierung von Windows-Setup](windows-setup-automation-overview.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)

[Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






