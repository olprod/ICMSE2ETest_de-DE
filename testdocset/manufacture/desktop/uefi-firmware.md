---
author: Justinha
Description: UEFI-Firmware
ms.assetid: 63cab521-9f35-4428-85b6-5561889243fd
MSHAttr: PreferredLib:/library/windows/hardware
title: UEFI-Firmware
ms.openlocfilehash: 73560ed69bb28b1297ab8b4fca7ce6a3e13a708f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-firmware"></a>UEFI-Firmware


Nachfolgend einige Aspekte bei der Bereitstellung von Windows auf Unified Extensible Firmware Interface UEFI-basierten Geräten.

## <a name="span-idwhatisuefispanspan-idwhatisuefispanspan-idwhatisuefispanwhat-is-uefi"></a><span id="What_is_UEFI_"></span><span id="what_is_uefi_"></span><span id="WHAT_IS_UEFI_"></span>Was ist UEFI?


Die Geräte gestartet wird, die Firmware-Schnittstelle steuert den Bootvorgang des PCs, und klicken Sie dann auf Windows oder ein anderes Betriebssystem Steuerung übergeben.

UEFI ist als Ersatz für die älteren BIOS-Firmware-Schnittstelle und die Schnittstelle EFI (Extensible Firmware) 1.10 Spezifikationen.

Mehr als 140 führenden Technologieunternehmen nutzen Sie das Unified EFI Forum, einschließlich AMD, AMI, Apple, Dell, HP, IBM, Insyde, Intel, Lenovo, Microsoft und Phoenix Technologies.

## <a name="span-idbenefitsspanspan-idbenefitsspanspan-idbenefitsspanbenefits-of-uefi"></a><span id="Benefits"></span><span id="benefits"></span><span id="BENEFITS"></span>Vorteile von UEFI


Firmware, die die UEFI 2.3.1 erfüllt Spezifikationen bietet die folgenden Vorteile:

-   Schneller starten und Mal fortsetzen.

-   Die Möglichkeit, Sicherheitsfeatures wie Secure Boot und Factory verwenden verschlüsselt Laufwerke, die verhindern, dass nicht vertrauenswürdigen Code ausgeführt, bevor das Betriebssystem geladen wird. Weitere Informationen finden Sie unter [Secure Boot – Übersicht](secure-boot-overview.md) und [Factory Laufwerke verschlüsselt](factory-encrypted-drives.md).

-   Die Möglichkeit, große Festplatten (mehr als 2 TB) und Laufwerke mit mehr als vier Partitionen leichter zu unterstützen.

-   Kompatibilität mit älteren BIOS. Einige UEFI-basierten PCs enthalten ein Kompatibilität Support Modul (CSM), die emuliert früheren BIOS Maß an Flexibilität und Kompatibilität für Endbenutzer bereitstellen. Für die Verwendung der CSM muss Secure Boot deaktiviert werden.

-   Unterstützung für multicast-Bereitstellung, wodurch PC-Hersteller, um ein PC-Abbild übertragen, die von mehreren PCs ohne einer Überlastung des Netzwerk- oder Bild-Servers empfangen werden können.

-   Unterstützung für UEFI Firmwaretreiber, Anwendungen und einige Option.

Zusätzliche Vorteile sind in der [Intel EFI und UEFI Übersicht und Spezifikationen](http://www.intel.com/technology/efi/)beschrieben.

## <a name="span-idwindowssupportofuefispanspan-idwindowssupportofuefispanspan-idwindowssupportofuefispanwindows-support-of-uefi"></a><span id="Windows_support_of_UEFI"></span><span id="windows_support_of_uefi"></span><span id="WINDOWS_SUPPORT_OF_UEFI"></span>Unterstützung für Windows UEFI


Unterstützung für UEFI in folgenden Windows Editionen enthalten:

-   Windows 10 desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen), Windows Server 2016 – Technische Vorschau, Windows 8 und Windows 8.1 Unterstützung für systemeigene UEFI 2.0 oder höher auf 32-Bit-(x86), 64-Bit-(x64) und ARM-basierte PCs. Sie unterstützen auch BIOS-basierten PCs und UEFI-basierte PCs, die in älteren BIOS-Kompatibilitätsmodus ausgeführt.

    Einige Features wie etwa Secure Boot erfordern UEFI 2.3.1 Fehlerverzeichnis C oder höher.

-   Windows Server 2012 R2 und Windows Server® 2012 unterstützt systemeigene UEFI 2.0 oder höher auf 64-Bit-Systemen. Einige Features wie etwa Secure Boot erfordern UEFI 2.3.1 (engl.).

-   Windows 7 und Windows Server 2008 R2:

    -   UEFI 2.0 oder höher auf 64-Bit-Systemen unterstützt. Sie unterstützen auch BIOS-basierten PCs und UEFI-basierte PCs, die in älteren BIOS-Kompatibilitätsmodus ausgeführt.

    -   Unterstützung von Klasse 2 Computern im legacy BIOS-Kompatibilitätsmodus mithilfe einer CSM, sodass diese die ältere INT10 BIOS-Features verwenden können.

    -   Werden nicht auf Klasse 3-Systemen unterstützt, da diese Betriebssysteme übernehmen das Vorhandensein von legacy INT10 BIOS-Unterstützung in der Firmware der nicht in einer Klasse 3 UEFI Implementierung verfügbar ist.

    -   Windows Server 2008 R2 unterstützt auch EFI 1.10 Itanium-basierte Systeme.

**Hinweis**  
-   In UEFI Modus muss die Windows-Version die PC-Architektur übereinstimmen. Eine 64-Bit-UEFI PC können nur 64-Bit-Versionen von Windows starten. Ein 32-Bit-PC kann nur 32-Bit-Versionen von Windows starten. In einigen Fällen können in älteren BIOS-Modus Sie möglicherweise zum Ausführen der 32-Bit-Windows auf einem 64-Bit-PC, vorausgesetzt, dass der Hersteller unterstützt die 32-Bit-legacy-BIOS-Modus auf dem PC.

-   Windows unterstützt eine Teilmenge der Funktionen, die in der Spezifikation für UEFI definiert ist. Windows-Implementierungen prüfen nicht explizit mit einer höheren Versionen der firmware

-   Zusätzliche UEFI Anforderungen finden Sie unter [UEFI Installation Media-Format und Boot Standardverhalten](uefi-installation-media-format-and-default-boot-behavior.md) und [UEFI Anforderungen: Zeit-Laufzeitprozess Ruhezustand (S4) starten](uefi-requirements-boot-time-runtime-hibernation-state--s4.md).

 

## <a name="span-idconsiderationsspanspan-idconsiderationsspanspan-idconsiderationsspanbefore-you-begin"></a><span id="Considerations"></span><span id="considerations"></span><span id="CONSIDERATIONS"></span>Bevor Sie beginnen


Beachten Sie vor der Installation von Windows auf einem PC UEFI-basierten Folgendes:

-   Bei einigen Plattformen oder Hardwarekonfigurationen müssen Sie möglicherweise zusätzliche Schritte zum sicherstellen, dass Windows im UEFI Modus oder im legacy BIOS-Kompatibilitätsmodus installiert ist. Weitere Informationen finden Sie unter [Starten Sie UEFI oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md).

-   UEFI Festplatten erfordern die GUID Partition (GPT) Partition Tabellenstruktur, anstatt die master Boot Record (MBR) Partitionsstruktur, die in BIOS verwendet wird.

    Wenn Sie Windows mithilfe der Windows-Produkts-DVD installieren, erkennt Windows Setup an, ob Windows basierend auf Auswahl dieser Option wird konfiguriert und der PC in UEFI-Modus oder BIOS-Kompatibilitätsmodus gestartet wurde.

-   Windows-Vorinstallation Environment (Windows PE) kann zur Unterstützung von UEFI-Modus und BIOS-Kompatibilitätsmodus konfiguriert werden.

     **Hinweis**  
    Während der Computer im UEFI-Modus befindet, muss die Version von Windows PE die PC-Architektur übereinstimmen. 64-Bit-Versionen von Windows PE kann nur ein PC in 64-Bit-UEFI Firmware Modus gestartet ist. 32-Bit-Versionen von Windows PE kann nur mit ein PC im 32-Bit-UEFI Firmware Modus gestartet. Auf PCs, die UEFI-Modus und BIOS-Legacymodus unterstützen, können Sie möglicherweise zum Ausführen der 32-Bit-Windows PE auf einem 64-Bit-PC BIOS im Menü Einstellungen von "UEFI-Modus" in "BIOS-Modus" geändert vorausgesetzt, dass der Hersteller legacy-BIOS-Modus unterstützt.

    Anweisungen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md) oder [Windows PE: Installieren Sie auf einer Festplatte (flach Boot oder nicht-RAM)](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md).
    
-   Hinweis für Firmware Hersteller: Verwenden Sie nicht-Tools oder Anwendungen zum Windows-spezifische Startdateien, einschließlich der Dateien in das Laufwerk C: alter\\Start- und C:\\EFI Ordner. Ändern diese Dateien konnten dem PC starten, aus dem Ruhezustand fortsetzen oder System Wiederherstellungstools auszuführen beeinträchtigen. Verwenden Sie stattdessen Tools wie BCDboot, um die Startreihenfolge festzulegen. Weitere Informationen finden Sie unter [BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md).

## <a name="span-idresourcesspanspan-idresourcesspanspan-idresourcesspansee-also"></a><span id="Resources"></span><span id="resources"></span><span id="RESOURCES"></span>Siehe auch


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>UEFI-Anforderungen</p></td>
<td align="left"><p>[UEFI Installation Media-Format und standardmäßige boot-Verhalten](uefi-installation-media-format-and-default-boot-behavior.md) | [UEFI Anforderungen: Zeit-Laufzeitprozess Ruhezustand (S4) starten](uefi-requirements-boot-time-runtime-hibernation-state--s4.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p>UEFI-Features</p></td>
<td align="left"><p>[Microsoft-Hardware Developer Central: Firmware und Boot-Umgebung](http://go.microsoft.com/fwlink/?LinkId=244007) | [Secure Boot – Übersicht](secure-boot-overview.md) | [Factory verschlüsselt Laufwerke](factory-encrypted-drives.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Starten von einem PC UEFI oder BIOS-Legacymodus</p></td>
<td align="left"><p>[Starten Sie UEFI-Modus oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md) | [Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Verwalten von Festplatten UEFI und Konfigurationsdaten boot</p></td>
<td align="left"><p>[Schwerer Laufwerke und Partitionen](hard-drives-and-partitions.md) | [Festplatte UEFI/GPT-basierte Partitionen konfigurieren](configure-uefigpt-based-hard-drive-partitions.md) | [System Startkonfigurationsdaten Einstellungen für UEFI](bcd-system-store-settings-for-uefi.md) | [UEFI Validierung Option ROM Anleitungen](uefi-validation-option-rom-validation-guidance.md) | [Windows UEFI Firmware Update-Plattform](http://go.microsoft.com/fwlink/p/?linkid=523808) | [Überprüfung der Funktionalität von Windows UEFI Firmware Update-Plattform](validating-windows-uefi-firmware-update-platform-functionality.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Foren</p></td>
<td align="left"><p>[Unified Extensible Firmware Interface-Forum (UEFI Forum)](http://go.microsoft.com/fwlink/?LinkId=244009)</p></td>
</tr>
</tbody>
</table>

 

 

 






