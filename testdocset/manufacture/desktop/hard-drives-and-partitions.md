---
author: Justinha
Description: Festplatten und Partitionen
ms.assetid: bb453d9d-e819-4301-834d-09486d3e64e9
MSHAttr: PreferredLib:/library/windows/hardware
title: Festplatten und Partitionen
ms.openlocfilehash: 08575f3be7ef4edc973a368e7b7e64ea315fbbfc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hard-drives-and-partitions"></a>Festplatten und Partitionen


In diesem Abschnitt erfahren Sie Methoden zum Bereitstellen von Windows auf verschiedenen Laufwerken, einschließlich Festplatten, Solid-State-Laufwerke (SSDs) oder virtuelle Festplatten (VHDs). Sie erfahren auch über Faktoren, die Sie bei der Bereitstellung von Windows berücksichtigen müssen.

## <a name="span-idwhatsnewinwindows10spanspan-idwhatsnewinwindows10spanspan-idwhatsnewinwindows10spanwhats-new-in-windows-10"></a><span id="What_s_new_in_Windows_10"></span><span id="what_s_new_in_windows_10"></span><span id="WHAT_S_NEW_IN_WINDOWS_10"></span>Was ist neu in Windows 10


-   Verwenden Sie Compact OS und Single-sourcing mehr Speicherplatz auf der Festplatte speichern: [Compact OS Single-sourcing- und Bild-Optimierung](compact-os.md).
-   Verwenden Sie das Bildformat FFU Bilder schneller auf Ihre Geräte anwenden: [Bereitstellen von Windows verwenden vollständige Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md)
-   In Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) haben wir das Partitionslayout geändert. Während wir noch Image-Tools separate Wiederherstellung verwenden, benötigt Windows nicht mehr einer separaten Wiederherstellung des gesamten Systems Drucktaste zurücksetzen Features zu verwendende Bild zu. Dies kann mehrere GB Speicherplatz sparen.

    Nun wird empfohlen, dass Sie die Windows-Wiederherstellung Tools Partition unmittelbar nach der Windows-Partition platzieren. Dadurch wird Windows ändern und neu erstellen der Partition später, wenn zukünftige Updates vergrößern Wiederherstellung benötigen.

    Wenn Sie Skripts zum Bereitstellen von Windows verwenden, checken Sie die neue Beispielskripts, den, die wir für verschiedene Firmware Gerätetypen (die neuere UEFI-basierten, oder der Vorversion BIOS) erstellt haben. Finden Sie weitere Informationen finden Sie [UEFI/GPT-basierten Festplattenpartitionen](configure-uefigpt-based-hard-drive-partitions.md) und [BIOS/MBR-basierte-Partitionen](configure-biosmbr-based-hard-drive-partitions.md).

-   Es ist nicht mehr erforderlich, auf SSD-Laufwerke Windows Assessment Systemtests (WinSAT) auszuführen. Windows erkennt SSD-Laufwerke und selbst entsprechend optimiert.
-   Auf [UEFI, GPT-basierte Laufwerke](configure-uefigpt-based-hard-drive-partitions.md)haben wir die empfohlene Größe von GPT von 128 MB auf 16 MB reduziert.

## <a name="span-idharddisksspanspan-idharddisksspanspan-idharddisksspandrive-types"></a><span id="HardDisks"></span><span id="harddisks"></span><span id="HARDDISKS"></span>Laufwerkstypen


Sie können Windows auf einer Festplatte, wie eine Festplatte oder ein Flashlaufwerk installieren. Aus Sicherheitsgründen können Sie Festplatten, die die Factory vorab verschlüsselt wurde. Ein einzelner Computer kann mehrere Laufwerke enthalten.

### <a name="span-idssdsspanspan-idssdsspanspan-idssdsspansolid-state-drives"></a><span id="SSDs"></span><span id="ssds"></span><span id="SSDS"></span>Solid-State-Laufwerke

Ein Solid-State Drive (SSD) ist eine Festplatte, die Solid-State Arbeitsspeicher werden permanente Daten gespeichert. Ein SSD benötigen mindestens 16 Gigabyte (GB) Speicherplatz, Windows zu installieren. Weitere Informationen zu Speicherplatz und RAM-Aspekten finden Sie unter [Compact OS Single-sourcing- und Bild-Optimierung](compact-os.md).

**Hinweis**   Es ist nicht mehr erforderlich, die Windows System Assessment Tests (WinSAT) auf SSD-Laufwerke auszuführen. Windows jetzt SSD-Laufwerke erkennt und wird selbst entsprechend optimieren.

 

### <a name="span-idadvancedformatspanspan-idadvancedformatspanspan-idadvancedformatspanadvanced-format-drives"></a><span id="AdvancedFormat"></span><span id="advancedformat"></span><span id="ADVANCEDFORMAT"></span>Advanced Format-Laufwerke

Einige erweiterte Format Laufwerke können Sie zusätzliche Speicherplatz bereitstellen.

Erweiterte Format 512 Emulation (512e) Laufwerke werden auf BIOS-basierten oder UEFI-basierten Computer unterstützt.

Erweiterte Format 4K Native (4Kn) Laufwerke werden auf nur UEFI-basierte Computer unterstützt.

**Warnung**  
Für Advanced Format 4K Native-Laufwerke (4-KB-pro Sektor) Laufwerke ist Partition mit mindestens so groß 260 MB aufgrund einer Einschränkung des Dateiformats FAT32. Die Größe der Partition mit mindestens der FAT32-Laufwerken wird als Sektorgröße (4 KB) x 65527 = 256 MB berechnet. Weitere Informationen finden Sie unter [Configure UEFI/GPT-Based Hard Drive-Partitionen](configure-uefigpt-based-hard-drive-partitions.md).

 

### <a name="span-idencrypteddisksandpartitionsspanspan-idencrypteddisksandpartitionsspanspan-idencrypteddisksandpartitionsspanfactory-encrypted-hard-drives"></a><span id="EncryptedDisksAndPartitions"></span><span id="encrypteddisksandpartitions"></span><span id="ENCRYPTEDDISKSANDPARTITIONS"></span>Factory verschlüsselt Festplatten

Eine Factory vor der Verschlüsselung Festplatte können Sie zum Schutz Ihrer Deployment-Umgebung nicht autorisierten Zugriff zu verhindern, dass vor der Installation von Windows oder andere Software. Weitere Informationen finden Sie unter [Factory verschlüsselt Laufwerke](factory-encrypted-drives.md).

### <a name="span-idmultipleharddisksspanspan-idmultipleharddisksspanspan-idmultipleharddisksspanmultiple-hard-drives"></a><span id="MultipleHardDisks"></span><span id="multipleharddisks"></span><span id="MULTIPLEHARDDISKS"></span>Mehrere Festplatten

Wenn Sie Windows auf einem Gerät, die über mehrere Festplatten verfügt installieren, können Sie den Pfad zum Speicherort Datenträger verwenden, um sicherzustellen, dass die Bilder auf die beabsichtigte Laufwerke angewendet werden.

Verwenden Sie dazu die `diskpart SELECT DISK=<disk location path>` Befehl aus, um jedes Laufwerk auszuwählen. Beispiel:

`SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)`

**Hinweis**  
Das Systemlaufwerk möglicherweise als Datenträger 0 in der DiskPart-Tool nicht angezeigt. Das System möglicherweise unterschiedlich viele auf Laufwerken zuweisen, wenn Sie neu starten. Andere Computer mit der gleichen Laufwerkskonfiguration können verschiedene Datenträger Zahlen haben.

Finden Sie weitere Informationen finden Sie unter [Konfigurieren mehrerer Festplatten](configure-multiple-hard-drives.md) und [Festplatte Speicherort Pfadformat](hard-disk-location-path-format.md).

 

## <a name="span-idpartitionsspanspan-idpartitionsspanspan-idpartitionsspanpartitions"></a><span id="Partitions"></span><span id="partitions"></span><span id="PARTITIONS"></span>Partitionen


Sie können die Festplatte in mehrere Partitionen unterteilen. Sie können separate System, Wiederherstellung, Windows oder Daten Partitionen erstellen.

Zur Verbesserung der Sicherheits der Partition mit Windows oder Daten können Sie BitLocker zum Verschlüsseln der Partition. Weitere Informationen finden Sie unter [BitLocker Drive Encryption](bitlocker-drive-encryption.md).

Die Partitionstypen müssen die Firmware des Computers überein. Sie können Windows auf Festplatten installieren, die auf eine der folgenden Arten von Firmware basieren:

-   **Basic Input/Output System (BIOS)**. Verwendet die Partitionsstruktur der Master Boot Record (MBR.

-   **Extensible Firmware Interface (EFI) (Klasse 1)**: die GUID-Partitionstabelle (GPT) Partitionsstruktur verwendet.

-   **Unified Extensible Firmware Interface (UEFI) Klasse 2**: verwendet die Struktur der GPT-Partition. Enthält außerdem ein Kompatibilität Support-Modul (CSM), das Sie BIOS-Funktionen, einschließlich der MBR Partitionsstruktur verwenden kann. In diesem Modul möglich aktiviert oder deaktiviert in der Firmware.

-   **Unified Extensible Firmware Interface (UEFI) Klasse 3**: verwendet die Struktur der GPT-Partition.

Um den Typ Ihres Systems zu bestimmen, wenden Sie sich an die vom Hardwarehersteller Ihrer.

### <a name="span-idsystempartitionspanspan-idsystempartitionspanspan-idsystempartitionspansystem-and-utility-partitions"></a><span id="SystemPartition"></span><span id="systempartition"></span><span id="SYSTEMPARTITION"></span>System-und Dienstprogramm

Eine *Systempartition* ist eine Partition, die Hardware-spezifischen Dateien enthält, die zum Laden von Windows benötigt werden.

Speichert standardmäßig während der Installation von Windows, Windows diese Hardware-spezifischen Dateien in einer separaten Partition. Auf diese Weise können den Computer der folgenden:

-   **Sicherheits-Tools**. Einige Sicherheitstools wie BitLocker, ist eine separate Systempartition erforderlich.

-   **Wiederherstellungstools**. Einige Wiederherstellungstools, wie beispielsweise Windows Recovery Environment (Windows RE), ist eine separate Systempartition erforderlich.

-   **Mehrere Betriebssysteme**. Verfügt ein Computer mehrere Betriebssysteme, wie Windows-10 für desktop-Editionen und Windows 7, zeigt der Computer eine Liste der Betriebssysteme. Der Benutzer kann dann zum Starten des Betriebssystems auswählen. Wenn die Boot-Systemdateien auf einer separaten Partition haben, ist es einfacher, eine Windows-Partition entfernen oder Ersetzen Sie die Partition durch eine neue Kopie von Windows.

Wir empfehlen hinzufügen System Dienstprogrammpartitionen, bevor Sie die Windows-Partition, da den Fall, dass eine Wiederherstellung des gesamten Systems erforderlich ist, wird dieser Partition Reihenfolge verhindert, dass die Wiederherstellungstools und überschreiben Sie die System- und Dienstprogramm-Partitionen.

Informationen zur Konfiguration von Partitionen, während Sie Bilder anwenden finden Sie unter [Erfassung und Anwenden von Windows, System, und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md).

### <a name="span-idmicrosoftrecoverypartitionsspanspan-idmicrosoftrecoverypartitionsspanspan-idmicrosoftrecoverypartitionsspanmicrosoft-reserved-partition-msr"></a><span id="MicrosoftRecoveryPartitions"></span><span id="microsoftrecoverypartitions"></span><span id="MICROSOFTRECOVERYPARTITIONS"></span>Microsoft reservierte Partition (MSR)

Die Größe der MSR wird auf UEFI/GPT-Systemen verwendet, um Softwarekomponenten unterstützen, die früher ausgeblendete Bereiche verwendet.

Weitere Informationen zur Konfiguration von MSR-Partitionen finden Sie unter [Configure UEFI/GPT-Based Hard Drive Partitionen](configure-uefigpt-based-hard-drive-partitions.md).

Weitere Informationen zu MSR-Partitionen finden Sie unter [Windows und GPT-häufig gestellte Fragen](http://go.microsoft.com/fwlink/?LinkId=267523)

### <a name="span-idrecoverypartitionspanspan-idrecoverypartitionspanspan-idrecoverypartitionspanrecovery-partitions"></a><span id="RecoveryPartition"></span><span id="recoverypartition"></span><span id="RECOVERYPARTITION"></span>Recovery-Partitionen

Es wird empfohlen Hinzufügen einer separaten Partition für Windows Recovery Environment (Windows RE) am Ende der Festplatte. Mit diesen Auftrag Partition zukünftige Updates erforderlich zum Hinzufügen oder ersetzen die Windows RE-Tools Partition wird Windows automatisch die Größe der Partition verwalten können.

BIOS/MBR-basierte Systeme ist es immer noch möglich, die Windows RE-Tools Partition mit der Systempartition zu kombinieren. Um Speicherplatz zu speichern, sollten Sie logische Partitionen umgehen der Grenzwert vier Partitionen erstellen. Weitere Informationen finden Sie unter [Configure mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md).

Für Windows-10 für desktop-Editionen ist es nicht mehr erforderlich, erstellen und Verwalten einer separaten Wiederherstellung des gesamten Systems Bild. Windows kann eine Aktualisierung durchführen oder Zurücksetzen von integrierten Tools.

### <a name="span-iddatapartitionspanspan-iddatapartitionspanspan-iddatapartitionspandata-partitions"></a><span id="DataPartition"></span><span id="datapartition"></span><span id="DATAPARTITION"></span>Datenpartitionen

Eine Datenpartition ist eine Partition, die Benutzerdaten gespeichert werden. Eine separate Datenpartition können einfacher Wartung für Situationen, das primäre Betriebssystem wahrscheinlich ersetzt werden, oder wenn mehrere Betriebssysteme auf demselben Gerät, beispielsweise Windows 10 und Windows 7 vorhanden sind. Wenn ein Gerät über mehrere Festplatten verfügt, kann eine Datenpartition auf einem anderen Laufwerk gespeichert werden.

**Warnung**  
Für typische Laufwerk-Konfigurationen empfohlen nicht, eine separate Datenpartition zu verwenden. Es gibt zwei Hauptgründe:

-   Die Partition möglicherweise nicht automatisch Daten zu schützen, die außerhalb der Ordner gespeichert ist. Beispielsweise haben Gast Zugriff auf Dateien in einer ungeschützten Datenpartition.
-   Wenn Sie alle anderen Volume als dem Systemvolume den Standardspeicherort der Benutzerprofil ändern, können Sie Ihr Bild nicht bedienen. Der Computer gelten möglicherweise nicht Updates, Patches, oder Service packs für die Installation. Eine Liste bekannter Probleme im Zusammenhang mit der Standard-Ordnerspeicherorte ändern finden Sie unter [Beschreibung der bekannten Probleme mit den Einstellungen FolderLocation](http://go.microsoft.com/fwlink/?LinkId=142275).

 

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
<td align="left"><p><strong>Bereitstellung</strong></p></td>
<td align="left"><p>[Festplatte UEFI, GPT-basierte Partitionen konfigurieren](configure-uefigpt-based-hard-drive-partitions.md) | [Festplatte BIOS/MBR-basierte Partitionen konfigurieren](configure-biosmbr-based-hard-drive-partitions.md) | [mehr als vier Partitionen auf einer Festplatte BIOS/MBR-basierte konfigurieren](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Mehrere Laufwerke</strong></p></td>
<td align="left"><p>[Konfigurieren mehrerer Festplatten](configure-multiple-hard-drives.md) | [Festplatte Speicherort Pfadformat](hard-disk-location-path-format.md) | [Portkonfiguration für interne und externe SATA-](http://go.microsoft.com/fwlink/p/?LinkId=321830) | [Spiegelung konfigurieren](http://go.microsoft.com/fwlink/?LinkId=733824)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Verwenden kleinere Laufwerke</strong></p></td>
<td align="left"><p>[Kompakte OS, Single sourcing und Bild-Optimierung](compact-os.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Vorgänge</strong></p></td>
<td align="left"><p>[Erfassung und Anwenden von Windows, System und Recovery Partitionen](capture-and-apply-windows-system-and-recovery-partitions.md) | [Bereitstellen von Windows verwenden, vollständige Flash Update (FFU)](deploy-windows-using-full-flash-update--ffu.md) | [Bereitstellen von Windows auf einer virtuellen Festplatte (systemeigenen Start)](deploy-windows-on-a-vhd--native-boot.md) | [Factory verschlüsselt Laufwerke](factory-encrypted-drives.md) | [BitLocker Drive Encryption](bitlocker-drive-encryption.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Problembehandlung</strong></p></td>
<td align="left"><p>[Reparieren Sie im Startmenü auf einem PC Dual-boot](repair-the-boot-menu-on-a-dual-boot-pc.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Tools und Einstellungen</strong></p></td>
<td align="left"><p>[UEFI Firmware](uefi-firmware.md) | [das Windows und GPT-häufig gestellte Fragen](http://go.microsoft.com/fwlink/?LinkId=88211) | [BCDboot Command-Line Options](bcdboot-command-line-options-techref-di.md) | [Befehl DiskPart Zeilensyntax](http://go.microsoft.com/fwlink/?LinkId=128458) | [WIM im Vergleich zu VHD im Vergleich zu FFU: Vergleichen Bilddateiformate](wim-vs-ffu-image-file-formats.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






