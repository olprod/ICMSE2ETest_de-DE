---
author: Justinha
Description: "Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen"
ms.assetid: 044cbb4f-7330-473d-8654-3371b2d6aff1
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen"
ms.openlocfilehash: b4a8d89666d56033d73360609cedb80830f17a58
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-supported-platforms-and-cross-platform-deployments"></a>Windows Setup-unterstützte Plattformen und plattformübergreifende Bereitstellungen


In diesem Thema werden die unterstützten Plattformen und Szenarien für die Bereitstellung ausführen, für die Installation von Windows.

Wenn Sie verschiedene Arten von PCs bereitstellen, können Sie Windows Setup als eine Möglichkeit, die zwischen Ihren Bildern über die Benutzeroberfläche der Windows-Setup auf ein bestimmtes Bild wählen auswählen. Sie können die Bilder für eine Vielzahl von Hardware-Plattformen (wie BIOS und UEFI 32-Bit- und 64-Bit-PCs) einschließen und für die verschiedenen Versionen von Windows (wie Windows 8.1, Windows Server 2012 R2 und Windows 7).

Sie können auch ein Skript Windows Setup ausführen. Starten Sie den PC zu Windows PE, und klicken Sie dann verwenden die \\Quellen\\setup.exe-Datei, um das Bild anzugeben.

## <a name="span-idfirmwareconsiderationsbiosvsuefispanspan-idfirmwareconsiderationsbiosvsuefispanfirmware-considerations-bios-vs-uefi"></a><span id="firmware_considerations__bios_vs._uefi"></span><span id="FIRMWARE_CONSIDERATIONS__BIOS_VS._UEFI"></span>Aspekte der Firmware: BIOS im Vergleich zu UEFI


Stellen Sie für UEFI-basierte PCs, die in UEFI oder legacy BIOS-Modi starten unterstützen sicher, dass auf Ihrem PC in den richtigen Firmware Modus gestartet wird, vor dem Starten der Installation von Windows ein. Anderenfalls Windows Setup möglicherweise die Festplattenpartitionen nicht ordnungsgemäß eingerichtet, oder die Installation möglicherweise abgebrochen wird, wenn die Festplatten vorkonfiguriert sind. Weitere Informationen finden Sie unter [Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md).

## <a name="span-idfirmwarebios32-bitand64-bitspanspan-idfirmwarebios32-bitand64-bitspanspan-idfirmwarebios32-bitand64-bitspanfirmware-bios-32-bit-and-64-bit"></a><span id="Firmware__BIOS_32-bit_and_64-bit"></span><span id="firmware__bios_32-bit_and_64-bit"></span><span id="FIRMWARE__BIOS_32-BIT_AND_64-BIT"></span>Firmware: BIOS 32-Bit- und 64-bit


So richten einen einzelnen Umgebung oder eine Gruppe von Skripts, die Bereitstellung von Windows auf 32-Bit- und 64-Bit-BIOS-PCs, verwenden Sie eine 32-Bit-Version von Windows PE und eine 32-Bit-Version von Windows Setup.

Die 64-Bit-Version von Windows-Setup wird nicht auf der 32-Bit-Version von Windows PE ausgeführt.

**So installieren eine 64-Bit-Version von Windows von einer 32-Bit-Version von Windows PE:**

1.  Starten Sie den PC mithilfe der 32-Bit-Version von Windows PE.

2.  Verwenden Sie eine der folgenden Verfahren, um einer 64-Bit-Version von Windows installieren:

    -   Führen Sie eine 32-Bit-Version von Windows Setup, und verwenden Sie die **Befehlszeilenoption/installFrom** ein 64-Bit-Windows-Abbild auswählen:

        ``` syntax
        X:\windows\system32> D:\setup /InstallFrom:"N:\Windows_64-bit\sources\install.wim"
        ```

        \endash oder \endash

    -   Führen Sie eine 32-Bit-Version von Windows Setup, und verwenden Sie die `Microsoft-Windows-Setup\ImageInstall\OSImage\` [InstallFrom](http://go.microsoft.com/fwlink/?LinkId=275617) unbeaufsichtigten Einstellung, um ein 64-Bit-Windows-Abbild auszuwählen.

        ``` syntax
        X:\windows\system32> D:\setup /unattend:"D:\unattend_install_64-bit.xml"
        ```

        \endash oder \endash

    -   Verwenden Sie Tools zum Aufzeichnen von Bild, um eine 64-Bit-Version von Windows auf den PC anzuwenden.

        ``` syntax
        Dism /Apply-Image /ImageFile:"Fabrikam_64-bit_image.wim" /Index:1 /ApplyDir:D:\
        ```

        Weitere Informationen finden Sie unter [Anwenden von Bildern mithilfe von DISM](apply-images-using-dism.md).

**Warnung**  
Bereitstellen von Windows 7 unterstützt dieses Verfahren nicht.

 

## <a name="span-idusingwindowssetuptoinstallpreviousversionsofwindowsspanspan-idusingwindowssetuptoinstallpreviousversionsofwindowsspanspan-idusingwindowssetuptoinstallpreviousversionsofwindowsspanusing-windows-setup-to-install-previous-versions-of-windows"></a><span id="Using_Windows_Setup_to_Install_Previous_Versions_of_Windows"></span><span id="using_windows_setup_to_install_previous_versions_of_windows"></span><span id="USING_WINDOWS_SETUP_TO_INSTALL_PREVIOUS_VERSIONS_OF_WINDOWS"></span>Mithilfe von Windows Setup zum Installieren von früheren Versionen von Windows


Windows 8.1 und Windows Server 2012 R2-Versionen der Windows-Installation können Sie die frühere Versionen von Windows installieren:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Host-Betriebssystem</th>
<th align="left">Windows 8.1 Setup-Unterstützung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8.1</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012 R2</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>WindowsServer 2012</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2008 R2</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows Vista</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>WindowsServer 2008</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows XP mit SP3</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2003 R2 und früheren Versionen</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows XP mit SP2 und früheren Versionen</p></td>
<td align="left"><p>Nein</p></td>
</tr>
</tbody>
</table>

 

Sie können auch aus der Windows-Vorinstallation Environment (Windows PE) Windows Setup ausführen. In der folgenden Tabelle werden die unterstützten Windows PE Umgebungen aufgelistet:

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Version von Windows Setup</th>
<th align="left">Windows PE 5.0 (Windows 8.1)</th>
<th align="left">Windows PE 4.0 (Windows 8)</th>
<th align="left">Windows PE 3.0 (Windows 7)</th>
<th align="left">Windows PE 2.0 (Windows Vista)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 8.1-Setup</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows 8-Setup</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7-Setup</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Vista-Setupprogramm</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmkunsupportedspanspan-idbkmkunsupportedspancross-platform-deployment"></a><span id="bkmk_unsupported"></span><span id="BKMK_UNSUPPORTED"></span>Plattformübergreifende-Bereitstellung


Plattformübergreifende Bereitstellung bezeichnet den Vorgang der Installation von einer bestimmten Architektur von Windows in einer Umgebung von einer anderen Architektur. Beispielsweise können Sie eine 64-Bit-Edition von Windows 8.1 oder Windows 8 von einer 32-Bit-Edition von Windows PE bereitstellen. Die Vorteile der Verwendung einer Lösung Plattformübergreifende-Bereitstellung ist, dass Sie nicht mehrere Versionen von Windows PE verwalten für die Installation von anderen Architektur-Editionen von Windows. Sie können einen einzelnen Windows PE-Abbild erstellen, die Sie zum Installieren von 32-Bit- und 64-Bit-Editionen von Windows verwenden können.

Wenn Sie eine 64-Bit-Edition von Windows von einer 32-Bit-Version von Windows PE installieren, müssen Sie Windows PE 2.0 oder höher verwenden. Weitere Informationen zu Windows PE-Versionen finden Sie unter [Windows PE für Windows 10](winpe-intro.md).

In der folgenden Tabelle sind die verschiedenen Architekturen Windows Bilder (32-Bit- oder 64-Bit), die eine bestimmte Version von Windows 8.1 Setup installieren kann.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left">64-Bit-Windows 8.1-Bild</th>
<th align="left">32-Bit-Windows 8.1-Bild</th>
<th align="left">64-Bit-Windows 8-Bild</th>
<th align="left">32-Bit-Windows 8-Bild</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>64-Bit-Windows 8.1-Setup</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>32-Bit-Windows 8.1-Setup</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idlimitationsofcross-platformdeploymentspanspan-idlimitationsofcross-platformdeploymentspanspan-idlimitationsofcross-platformdeploymentspanlimitations-of-cross-platform-deployment"></a><span id="Limitations_of_cross-platform_deployment"></span><span id="limitations_of_cross-platform_deployment"></span><span id="LIMITATIONS_OF_CROSS-PLATFORM_DEPLOYMENT"></span>Einschränkungen von Plattformübergreifende-Bereitstellung

Diese plattformübergreifende Bereitstellungsszenarien werden nicht unterstützt:

-   Ein 64-Bit-Windows-Abbild installieren auf einem 32-Bit-Computer.

-   Bereitstellen von einem 32-Bit-Windows-Abbild von einer Vorinstallation 64-Bit-Umgebung.

-   Verwenden eine 32-Bit-Version von Windows Setup auf um einem 64-Bit-Betriebssystem zu aktualisieren.

-   Verwenden eine 32-Bit-Version von Windows 8-Setup zum Bereitstellen von 64-Bit-Version des Betriebssystems Windows 7.

    Beispielsweise müssen Sie eine 64-Bit-Version von Windows 8 Setup zum Bereitstellen von 64-Bit-Version von Windows 7 verwenden. In früheren Versionen musste die Version des Windows-Setup-Version des Betriebssystems übereinstimmen, die Sie bereitstellen möchten. Beispielsweise musste Setup.exe Windows 7, Windows 7 installieren verwendet werden.

-   Verwenden von Startdatenträger Microsoft Internet SCSI (iSCSI) in einem Szenario zur Bereitstellung plattformübergreifende.

    Installieren von Windows (64-Bit-Version) von plattformübergreifende Medien, wie beispielsweise Windows PE (32-Bit-Version) an ein iSCSI-Startdatenträger wird beispielsweise nicht unterstützt. Sie müssen die gleiche Architektur für Windows PE als das Ziel Bereitstellungsarchitektur verwenden, bei der Bereitstellung von Windows auf eine iSCSI-Startdatenträger.

-   Klicken Sie auf Unified Extensible Firmware Interface (UEFI), eine 64-Bit-Edition von Windows von einer 32-Bit-Version von Windows PE bereitstellen. Auf einigen Computern UEFI Installieren von Windows in BIOS-Kompatibilitätsmodus und müssen in UEFI-Kompatibilitätsmodus wechseln. Weitere Informationen finden Sie unter [Starten UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md).

-   Klicken Sie auf BIOS:

    -   Ausführen von plattformübergreifende Bereitstellungen, außer als Teil einer Neuinstallation oder zum Ausführen einer Windows-Bereitstellungsdienst-bereitstellungs.

    -   Bereitstellen von plattformübergreifende-Installationsmedien für Benutzer für die Wiederherstellung.

        Um zu verhindern, dass Benutzer die falsche-Edition von Windows für die Architektur von ihrem Computer installieren, bieten Sie nicht plattformübergreifende Installationsdatenträger zu Benutzer für die Wiederherstellung oder Neuinstallation. Darüber hinaus gilt das Windows Recovery Environment (Windows RE)-Feature, das auf dem Datenträger enthalten ist nur für 32-Bit-Windows-Installationen ein.

### <a name="span-idcreatingwimfilespanspan-idcreatingwimfilespanspan-idcreatingwimfilespancreating-a-wim-file-for-multiple-architecture-types"></a><span id="Creating_WIMFile"></span><span id="creating_wimfile"></span><span id="CREATING_WIMFILE"></span>Erstellen einer WIM-Datei für mehrere Architekturen

Wenn eine WIM-Datei 32-Bit- und 64-Bit-Windows-Editionen enthält, müssen Sie das Windows-Abbild auswählen, das Sie installieren möchten. Windows-Setup verwendet normalerweise den Product Key ein, die Sie in angeben der `ProductKey` Einstellung, um zu bestimmen, welches Windows-Abbild installiert. Enthält die Datei 2 Editionen der gleichen Windows-Version, wie Windows 8.1 Pro, Sie müssen jedoch die `MetaData` festlegen, die in einer Antwortdatei an die Edition zu installieren.

Geben Sie zum Auswählen eines Bildes Metadaten, die den Index, Name, Beschreibung oder Architektur Bildtyp entspricht. Verwenden Sie für die Metadaten für den Architekturtyp 0 für 32-Bit-Editionen und 9 für 64-Bit-Editionen. Weitere Informationen finden Sie unter der `MetaData` [Schlüssel](http://go.microsoft.com/fwlink/?LinkId=320263) -Einstellung.

Die Antwortdatei muss Prozessor-spezifische Komponenten enthalten. Die Antwortdatei Einstellungen im Durchgang [WindowsPE](windowspe.md) Konfiguration müssen den Architekturtyp der Vorinstallation Umgebung übereinstimmen. Die Einstellungen, die auf dem Windows-Abbild anwenden müssen die-Typ Architektur des Bilds übereinstimmen. Wenn Sie eine Antwortdatei, die 64-Bit-Bilder aus einer Vorinstallation 32-Bit-Umgebung bereitgestellt wird erstellen, müssen alle Komponenten in die Antwortdatei für den WindowsPE Konfigurationsdurchlauf beispielsweise den Typ des Prozessors-Attribut von **X86**enthalten. Einstellungen angewendet werden in der [specialize](specialize.md), [OobeSystem](oobesystem.md)oder andere Konfiguration müssen übergibt den Typ des Prozessors-Attribut von **amd64**enthalten.

### <a name="span-idbkmk5spanspan-idbkmk5spaninstalling-64-bit-drivers"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>Installieren von 64-Bit-Treiber

Alle Treiber, die in Windows enthaltenen angemeldet sind. Im Cross-Architektur-Bereitstellungen können Sie einen Out-of-Box-Gerätetreiber verwenden. Aber wenn Sie einen nicht signierten Out-of-Box-Gerätetreiber verwenden, der Start in einer 64-Bit-Installation erforderlich ist, kann die Installation nicht verwendet werden.

Sie können während der Installation von Windows 64-Bit-Treiber für ein Windows-Abbild in einem der folgenden Verfahren installieren:

-   In Benutzer-Installationen können Sie drücken Sie F6, oder klicken Sie auf die Schaltfläche **Load-Treiber** auf der Seite **Konfiguration** der Windows-Installation.

-   Unbeaufsichtigte Installationen können der Microsoft-Windows-PnpCustomizationsWinPE oder Microsoft-Windows-PnpCustomizationsNonWinPE Komponente in einer Antwortdatei Sie einen Pfad angeben. Weitere Informationen zum Automatisieren der Installations, finden Sie unter [Windows-Setup zu automatisieren](automate-windows-setup.md).

## <a name="span-idhardwareconsiderationsencryptedharddrivese-drivesspanspan-idhardwareconsiderationsencryptedharddrivese-drivesspanspan-idhardwareconsiderationsencryptedharddrivese-drivesspanhardware-considerations-encrypted-hard-drives-e-drives"></a><span id="Hardware_considerations__Encrypted_Hard_Drives__e-Drives_"></span><span id="hardware_considerations__encrypted_hard_drives__e-drives_"></span><span id="HARDWARE_CONSIDERATIONS__ENCRYPTED_HARD_DRIVES__E-DRIVES_"></span>Hardwareüberlegungen: verschlüsselt Festplatten (e-Laufwerke)


Unterstützung für verschlüsselt Hard Drive-Geräte (auch bekannt als E-Laufwerke) in Windows 8, Windows Server 2012 und Windows PE 4.0 wurde hinzugefügt.

Installieren eine vorherige Version von Windows (Beispiele: Windows 7 oder Windows Vista) auf eine verschlüsselt Hard Drive-Gerät verwenden Sie Windows PE 4.0 oder höher.

Weitere Informationen finden Sie unter [Verschlüsselt Hard Drive Gerät Guide](http://go.microsoft.com/fwlink/?LinkId=290954).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows-Setup-Szenarien und bewährte Methoden](windows-setup-scenarios-and-best-practices.md)

[Windows-Installation Setupvorgang](windows-setup-installation-process.md)

[Übersicht über die Automatisierung von Windows-Setup](windows-setup-automation-overview.md)

[Übersicht über Audit-Modus](audit-mode-overview.md)

[Windows Setup-Konfigurationsphasen](windows-setup-configuration-passes.md)

 

 






