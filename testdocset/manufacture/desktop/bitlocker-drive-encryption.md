---
author: Justinha
Description: BitLocker Drive Encryption
ms.assetid: 47d6aadf-0496-4a8a-b0a5-dfb6fa9f5748
MSHAttr: PreferredLib:/library/windows/hardware
title: BitLocker Drive Encryption
ms.openlocfilehash: 25fed58132322a1c114e031978dd7a4d2579b831
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bitlocker-drive-encryption"></a>BitLocker Drive Encryption


In diesem Thema werden die Anforderungen für die Bereitstellung einer Windows BitLocker Drive Encryption Lösung behandelt. Weitere Informationen zu BitLocker finden Sie unter [BitLocker Drive Encryption](http://go.microsoft.com/fwlink/?LinkId=116601) auf der TechNet-Website.

## <a name="span-idwhatisbitlockerdriveencryptionspanspan-idwhatisbitlockerdriveencryptionspanspan-idwhatisbitlockerdriveencryptionspanwhat-is-bitlocker-drive-encryption"></a><span id="What_Is_BitLocker_Drive_Encryption_"></span><span id="what_is_bitlocker_drive_encryption_"></span><span id="WHAT_IS_BITLOCKER_DRIVE_ENCRYPTION_"></span>Was ist BitLocker Drive Encryption?


BitLocker bietet offline-Daten und Betriebssystem-Schutz für Ihren Computer. BitLocker wird sichergestellt, dass Daten, die auf einem Computer gespeichert ist, für die Windows® ausgeführt wird, nicht preisgegeben werden, wenn der Computer manipuliert wird, wenn das installierte Betriebssystem offline ist. BitLocker verwendet einen Mikrochip, der ein Modul TPM (Trusted Platform) bereitstellen erweiterten Schutz für Ihre Daten und frühe Boot-Komponente Integrität zu wahren aufgerufen wird. Das TPM helfen, Ihre Daten vor Diebstahl oder unberechtigter schützen, indem das gesamte Windows-Volume verschlüsselt.

BitLocker ist darauf ausgelegt, den besten Endbenutzer mit Computern anzubieten, die über einen kompatiblen TPM-Mikrochip und BIOS verfügen. Ein kompatibles TPM ist als Version 1.2 definiert TPM mit der BIOS-Änderungen, die zur Unterstützung der statische Stamm der vertrauen Messung erforderlich sind, wie von der Trusted Computing Group definiert. Das TPM interagiert mit BitLocker an nahtlosen Schutz bereitzustellen beim Neustart des Computers.

Der Pfad zur Datei TPM-Treiber ist %windir%\\Inf\\Tpm.inf. Informationen zum Hinzufügen des TPM-Treibers zu Windows Vorinstallation Environment (Windows PE) finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

## <a name="span-idbitlockerdriveencryptionpartitioningrequirementsspanspan-idbitlockerdriveencryptionpartitioningrequirementsspanspan-idbitlockerdriveencryptionpartitioningrequirementsspanbitlocker-drive-encryption-partitioning-requirements"></a><span id="BitLocker_Drive_Encryption_Partitioning_Requirements"></span><span id="bitlocker_drive_encryption_partitioning_requirements"></span><span id="BITLOCKER_DRIVE_ENCRYPTION_PARTITIONING_REQUIREMENTS"></span>BitLocker Drive Encryption Partitionierung erforderlich


BitLocker muss eine Systempartition verwenden, die von der Windows-Partition getrennt ist. Der Systempartition:

-   Muss als aktive Partition konfiguriert werden.

-   Nicht muss verschlüsselte oder mit Speicher Benutzerdateien.

-   Sie benötigen mindestens 100 Megabyte (MB) Speicherplatz.

-   Sie benötigen mindestens 50 MB freiem Speicherplatz.

-   Kann mit einer Wiederherstellungspartition gemeinsam genutzt werden.

Weitere Informationen zu BitLocker Partitionierung Anforderungen finden Sie unter [Festplatten und Partitionen (Übersicht)](hard-drives-and-partitions.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Schwerer Laufwerke und Partitionen (Übersicht)](hard-drives-and-partitions.md)

 

 






