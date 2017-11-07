---
author: Justinha
Description: Windows PE (Windows PE)
ms.assetid: f20056af-adab-4d7a-83a0-f44c5a91e0d2
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows PE (Windows PE)
ms.openlocfilehash: 336648b4147e3b42651102122643dce0ebf0bb21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-pe-winpe"></a>Windows PE (Windows PE)


Windows PE (Windows PE) für Windows 10 ist eine kleine zum Installieren, bereitstellen und reparieren Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) verwendetes Betriebssystem Windows Server 2016 und andere Windows-Betriebssysteme. Windows PE können Sie folgende Aktionen ausführen:

-   Einrichten der Festplatte vor der Installation von Windows.
-   Installieren Sie Windows mithilfe von apps oder Skripts aus einem Netzwerk oder einem lokalen Laufwerk.
-   Erfassen und Windows-Abbilder anwenden.
-   Ändern Sie das Betriebssystem Windows, während er nicht ausgeführt wird.
-   Richten Sie die automatische Wiederherstellungstools.
-   Wiederherstellen von Daten von nicht startbaren Geräte.
-   Fügen Sie Ihre eigenen benutzerdefinierten Shell oder GUI diese Arten von Aufgaben automatisieren.

![Windows Pe Command-Line](images/dep-blue-winpe-overview.png)

## <a name="span-idwheredoidownloaditspanspan-idwheredoidownloaditspanspan-idwheredoidownloaditspanwhere-do-i-download-it"></a><span id="Where_do_I_download_it_"></span><span id="where_do_i_download_it_"></span><span id="WHERE_DO_I_DOWNLOAD_IT_"></span>Wo herunterladen ich es?


Wenn Windows PE erhalten möchten, verwenden Sie das Installationsprogramm in dem Windows Assessment and Deployment Kit (Windows ADK) integriert. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md), [Windows PE: Erstellen einer Start-CD, DVD, ISO oder VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md), oder finden Sie in der [Demo: Installieren von Windows PE auf einem USB-Laufwerk](http://go.microsoft.com/fwlink/?LinkId=279081).

## <a name="span-idbkmkoverspanspan-idbkmkoverspansupport-for-many-windows-features"></a><span id="BKMK_OVER"></span><span id="bkmk_over"></span>Unterstützung für viele Windows-features


Windows PE führt die Windows-Befehlszeile-Umgebung, und diese Windows-Features unterstützt:

-   **Batchdateien und Skripts**, einschließlich Unterstützung für Windows Script Host (WSH) und ActiveX Data Objects (ADO) und optionale Unterstützung für PowerShell.
-   **Anwendungen**, einschließlich Win32-Anwendungsprogrammierschnittstellen () und optionale Unterstützung für HTML Applications (HTA).
-   **Treiber**, einschließlich einer generischen Reihe von Treibern, die Netzwerke, Grafiken und Masse Speichergeräten ausgeführt werden können.
-   **Bild erfassen und Wartung**, einschließlich Deployment Image Servicing and Management (DISM).
-   **Netzwerk**, einschließlich der Verwendung von TCP/IP und NetBIOS über TCP/IP über LAN Dateiserver herstellen einer Verbindung mit.
-   **Speicherung**, NTFS DiskPart und BCDBoot einschließlich.
-   **Sicherheits-Tools**, einschließlich optional die Unterstützung für BitLocker und das Modul TPM (Trusted Platform), Secure Boot und andere Tools.
-   **Hyper-V**, einschließlich VHD-Dateien, Mausintegration, Massenspeichergerät und Netzwerktreibern, die Windows PE zur Ausführung in einer Hypervisor zulassen.

## <a name="span-idbkmkhardspanspan-idbkmkhardspanhardware-requirements"></a><span id="BKMK_HARD"></span><span id="bkmk_hard"></span>Hardwareanforderungen


Windows PE hat die gleichen Anforderungen als Windows mit folgenden Ausnahmen:

-   Es ist keine Festplatte erforderlich. Sie können Windows PE vollständig aus dem Speicher ausführen.
-   Die Basisversion erfordert nur 512MB Speicher. (Wenn Sie Treiber, Pakete oder apps hinzufügen, mehr Speicher benötigen Sie.)
-   Um Windows PE direkt aus dem Speicher (auch bekannt als RAM Datenträger Boot) starten, muss ein zusammenhängender Teil des physischen Arbeitsspeicher (RAM) kann das gesamte Windows PE (WIM) Bild enthalten verfügbar sein. Zum Optimieren der Speicherverwendung sollten Hersteller sicherstellen, dass ihre Firmware Speicherorte am Anfang oder am Ende des physischen Arbeitsspeichers-Adressraums reserviert.

Die 32-Bit-Version von Windows PE kann UEFI 32-Bit- und BIOS- und 64-Bit-BIOS PCs, gestartet werden.

Die 64-Bit-Version von Windows PE kann 64-Bit-UEFI und BIOS-PCs starten.

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Einschränkungen


Windows PE ist kein allgemeine Operating System. Es kann nicht zu anderen Zwecken als Bereitstellung und Wiederherstellung verwendet werden. Es sollte als einem thin-Client oder einem eingebetteten Betriebssystem nicht verwendet werden. Es sind andere Microsoft-Produkte, wie Windows Embedded CE, die für diese Zwecke verwendet werden können.

Um die Verwendung als Betriebssystem Produktion zu verhindern, wird Windows PE automatisch beendet die Shell, und nach einer continuous Verwendung 72 Stunden neu gestartet. In diesem Zeitraum ist nicht konfigurierbar.

Beim Neustart von Windows PE werden alle Änderungen verloren gehen, darunter Änderungen an der Treiber Laufwerkbuchstaben und der Windows PE-Registrierung. Zum dauerhaften ändern, finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

Die Standardinstallation von Windows PE wird verwendet, das Dateiformat FAT32, das was ihre eigenen Grenzen, einschließlich eines maximale Dateigröße von 4 GB und maximale Größe von 32 GB Laufwerk darstellt. Weitere Informationen finden Sie unter [Windows PE: Verwenden Sie einen einzelnen USB-Schlüssel für Windows PE und einer WIM-Datei (WIM)](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md).

Windows PE wird eines der folgenden nicht unterstützt:

-   Dateiserver oder Terminal Server verwenden.
-   Beitreten zu einer Netzwerkdomäne.
-   Herstellen einer Verbindung mit einem IPv4-Netzwerk von Windows PE in einem IPv6-Netzwerk.
-   Remotedesktop.
-   . MSI-Installationsdateien.
-   Starten von einem Pfad, der nicht englische Zeichen enthält.
-   64-Bit-apps auf 32-Bit-Version von Windows PE ausgeführt.
-   Hinzufügen von gebündelt app-Pakete über DISM (.appxbundle-Pakete).

**Hinweis**  Im Allgemeinen verwenden Sie die neueste Version von Windows PE zum Bereitstellen von Windows aus. Wenn Sie benutzerdefinierte Windows PE für Windows 10 Bilder verwenden, müssen Sie vielleicht weiterhin vorhandene Windows PE-Abbild verwenden, und führen die neueste Version von DISM aus einem Speicherort im Netzwerk. Finden Sie weitere Informationen finden Sie unter [DISM auf einen anderen Computer kopieren](copy-dism-to-another-computer.md).

 

**Hinweise zum Ausführen von Windows Setup in Windows PE:**

-   Die 32-Bit-Versionen von Windows PE und Windows-Setup können Sie 64-Bit-Versionen von Windows installieren. Weitere Informationen finden Sie unter [Windows Setup unterstützte Plattformen und plattformübergreifende Bereitstellungen](windows-setup-supported-platforms-and-cross-platform-deployments.md).
-   Obwohl Windows PE dynamische Datenträger unterstützt, ist dies nicht Windows Setup. Wenn Sie einen dynamischen Datenträger in Windows PE erstellte Windows installieren, werden nicht in Windows dynamische Datenträger verfügbar sein.
-   Für UEFI-basierte PCs, die UEFI und legacy BIOS-Modi zu unterstützen, muss Windows PE im richtigen Modus gestartet werden, um ordnungsgemäß Windows installieren zu können. Weitere Informationen finden Sie unter [Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md).

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>Siehe auch


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Inhaltstyp</th>
<th align="left">Verweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Produktbewertung</strong></p></td>
<td align="left"><p>[Was ist neu in Windows PE](whats-new-in-windows-pe-s14.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Bereitstellung</strong></p></td>
<td align="left"><p>[Windows PE: Erstellen von startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md) | [Demo: Installieren von Windows PE auf einem USB-Laufwerk](http://go.microsoft.com/fwlink/?LinkId=279081) | [Windows PE: Erstellen einer Start-CD, DVD, ISO oder VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md) | [Windows PE: Installieren Sie auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md) | [Windows PE: Boot UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md) | [Starten UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md) | [Windows PE: Verwenden Sie einen einzelnen USB-Schlüssel für Windows PE und einer WIM-Datei (WIM)](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md) | [Windows PE: Hinzufügen von Treibern](winpe-add-drivers.md) | [Windows PE: Storage Area Network (SAN) Richtlinie](winpe-storage-area-network--san--policy.md) | [Windows PE: Erstellen von Apps](winpe-create-apps.md) | [Windows PE: Optimieren der Leistung und das Bild zu reduzieren](winpe-optimize.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Problembehandlung</strong></p></td>
<td align="left"><p>[Windows PE-Netzwerk-Treiber: Initialisieren und Hinzufügen von Treibern](winpe-network-drivers-initializing-and-adding-drivers.md) | [Windows PE: Debuggen von Apps](winpe-debug-apps.md) |</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Tools und Einstellungen</strong></p></td>
<td align="left"><p>[Copype Command-Line Options](copype-command-line-options.md) | [Drvload Command-Line Options](drvload-command-line-options.md) | [Makewinpemedia Command-Line Options](makewinpemedia-command-line-options.md) | [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md) | [Windows PE: identifizieren, indem Sie ein Skript Laufwerkbuchstaben](winpe-identify-drive-letters.md) | [Wpeutil Command-Line Options](wpeutil-command-line-options.md) | [Windows PE: Hinzufügen von Paketen (optionalen Komponenten Verweis)](winpe-add-packages--optional-components-reference.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Technologien basierend auf Windows PE</strong></p></td>
<td align="left"><p>[Windows-Setup](windows-setup-technical-reference.md) | [Umgebung für Windows](windows-recovery-environment--windows-re--technical-reference.md) | [Diagnose und Wiederherstellung Toolset](http://go.microsoft.com/fwlink/?LinkId=294156)</p></td>
</tr>
</tbody>
</table>

 

 

 






