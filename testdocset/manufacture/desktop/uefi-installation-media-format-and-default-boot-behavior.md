---
author: Justinha
Description: UEFI Installation Media-Format und Standardverhalten boot
ms.assetid: 983e25d4-ce72-463e-ad59-02467f19f4a4
MSHAttr: PreferredLib:/library/windows/hardware
title: UEFI Installation Media-Format und Standardverhalten boot
ms.openlocfilehash: 4dd4e79f8dbeda7c300b3dfc0d4262da7770b487
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-installation-media-format-and-default-boot-behavior"></a>UEFI Installation Media-Format und Standardverhalten boot


Dieser Abschnitt beschreibt die Installation Medienformate, Boot Standardverhalten für UEFI Plattformen.

## <a name="span-idinstallationmediaguidelinesspanspan-idinstallationmediaguidelinesspanspan-idinstallationmediaguidelinesspaninstallation-media-guidelines"></a><span id="Installation_media_guidelines"></span><span id="installation_media_guidelines"></span><span id="INSTALLATION_MEDIA_GUIDELINES"></span>Installationsrichtlinien für Medien


-   Windows-Installationsmedium unterstützt Boot auf beide BIOS und UEFI Plattformen von Nutzen der Vorteile von mehreren Eintrag El Torito Boot Katalog unterstützt.
-   Der Standardwert El Torito Boot-Eintrag ist ein BIOS-Eintrag, der die ID der 80 x 86-Plattform enthält, die als "0 x 00" hexadezimal definiert ist.
-   Der zweite El Torito Boot-Eintrag ist ein EFI-Eintrags, der die Plattform-ID als "0xEF" enthält in Hexadezimalzahl. Der Eintrag verweist auf einer FAT-Partition mit der startbaren EFI Anwendung am \\EFI\\BOOT\\BOOTX64. EFI.

## <a name="span-iddefaultbootbehaviorspanspan-iddefaultbootbehaviorspanspan-iddefaultbootbehaviorspandefault-boot-behavior"></a><span id="Default_boot_behavior"></span><span id="default_boot_behavior"></span><span id="DEFAULT_BOOT_BEHAVIOR"></span>Standardverhalten boot


Firmware Herstellern müssen sicher, dass Folgendes vorhanden sein:

-   BIOS ignoriert Boot Einträge, die nicht über die ID der 80 x 86-Plattform verfügen das als "0 x 00" hexadezimal definiert ist. Ausfall anderen Boot Einträge ignoriert führt die Anzeige von ein etwas verwirrend Startmenü für den Endbenutzer.
-   Der BIOS-startet basierend auf den Eintrag BIOS ohne Aufforderung.
-   UEFI-Start-Manager ignoriert Start-Einträge, die nicht über die "0xEF" Plattform-ID verfügen
-   Der UEFI Boot-Manager startet basierend auf den Eintrag EFI ohne Aufforderung.

Um die Möglichkeit zum Starten von DVD-Medien zu unterstützen, enthält die Windows-Installations-DVD viele El Torito Boot Einträge, die beim Starten von BIOS oder UEFI ermöglichen. Der Standardwert El Torito Boot-Eintrag ist für BIOS auf.

Windows unterstützt den Abschnitt "nicht austauschbaren Medien Boot-Verhalten" aus der Spezifikation UEFI 2.3. Während der Installation von Windows und wenn Updates für bootmgfw.efi erforderlich sind, kopiert Windows die Windows-Boot-Anwendung aus \\Efi\\Microsoft \\Boot\\bootmgfw.efi auf \\Efi\\Boot\\*{Bogen}*.efi auf der Systempartition EFI starten. Diese Kopie ermöglicht eine Standardoption Boot für Windows, wenn ein permanenten RAM (NVRAM) Boot-Eintrag nicht verfügbar ist, wie beispielsweise bei eine Festplatte von einer Plattform an eine andere verschoben wird.

Bei der Aktualisierung von Windows bewahrt Windows die vorhandenen Startreihenfolge. Wenn Sie eine Neuinstallation von Windows ausführen, aktualisiert Windows die Startreihenfolge, damit sie den ersten Boot-Eintrag in der Liste ist.

## <a name="span-idothermediainformationspanspan-idothermediainformationspanspan-idothermediainformationspanother-media-information"></a><span id="Other_media_information"></span><span id="other_media_information"></span><span id="OTHER_MEDIA_INFORMATION"></span>Andere Media-Informationen


Die folgenden zusätzlichen Richtlinien gelten für Startmedien:

-   Windows unterstützt CD und DVD Boot aus dem Dateisystem Universal Disk Format (UDF). Windows-Installationsmedium auch El Torito verwendet und die UDF-Brücke Format zur Unterstützung von ISO 9660 und UDF Version 1.02 Dateisysteme mit erstellt wird.
-   Das Windows Assessment and Deployment Kit (Windows ADK) enthält eine aktualisierte Version von Oscdimg.exe, die die Erstellung eines Katalogs Boot El Torito Multi-Eintrag unterstützt.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[UEFI-Firmware](uefi-firmware.md)

[BCDBoot Befehlszeilenoptionen](bcdboot-command-line-options-techref-di.md)

[Starten Sie UEFI-Modus oder Legacy-BIOS-Modus](boot-to-uefi-mode-or-legacy-bios-mode.md)

[Windows PE: Boot in UEFI oder BIOS-Legacymodus](winpe-boot-in-uefi-or-legacy-bios-mode.md)

 

 






