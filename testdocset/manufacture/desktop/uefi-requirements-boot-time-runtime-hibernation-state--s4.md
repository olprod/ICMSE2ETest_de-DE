---
author: Justinha
Description: 'UEFI Anforderungen: Boot Zeit-Laufzeitprozess Ruhezustand (S4)'
ms.assetid: 8fad2f32-6ff5-49db-9d34-041485a34a4c
MSHAttr: PreferredLib:/library/windows/hardware
title: 'UEFI Anforderungen: Boot Zeit-Laufzeitprozess Ruhezustand (S4)'
ms.openlocfilehash: cb32653975fd2567f5642068703d453921c19d27
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-requirements-boot-time-runtime-hibernation-state-s4"></a>UEFI Anforderungen: Boot Zeit-Laufzeitprozess Ruhezustand (S4)


In diesem Abschnitt werden die UEFI und Firmware Anforderungen, einschließlich beschrieben:

-   Boot-Ausführungsdauer

-   Common Language Runtime Anforderungen

-   Ruhezustand (S4) Anforderungen

-   So aktivieren Sie UEFI Plattformen ohne CSM Anforderungen

## <a name="span-idboottimerequirementsspanspan-idboottimerequirementsspanspan-idboottimerequirementsspanboot-time-requirements"></a><span id="Boot_time_requirements"></span><span id="boot_time_requirements"></span><span id="BOOT_TIME_REQUIREMENTS"></span>Boot-Ausführungsdauer


Dieser Abschnitt beschreibt UEFI Boot Ausführungsdauer.

### <a name="span-iddisplayatboottimespanspan-iddisplayatboottimespanspan-iddisplayatboottimespandisplay-at-boot-time"></a><span id="Display_at_Boot_Time"></span><span id="display_at_boot_time"></span><span id="DISPLAY_AT_BOOT_TIME"></span>Anzeige beim Starten

Für eine Plattform, die ein Gerät Konsole verfügt, benötigt die UEFI 2.0-Spezifikation die Firmware auf den einfachen Text Ausgabe Protokoll implementieren. Optional kann die Firmware auch ein grafische Protokoll unterstützen. UEFI 2.0 definiert die Grafik Ausgabe Protocol (GOP) und EFI 1.1 definiert das Protokoll universelle Graphics Adapter (UGA). Windows unterstützt alle drei Protokolle, aber die Benutzeroberfläche mit den Protokollen unterscheidet. Für optimale Ergebnisse Wenn die Firmware ein grafische Protokoll, implementiert Windows empfiehlt und GOP bevorzugt.

Windows erfordert ein Protokoll grafische Symbole für nicht-englischen Nachricht Ressourcen zu rendern. Hierzu muss die Firmware Folgendes unterstützen:

1.  Ein grafische Protokoll – GOP oder UGA.

2.  Entweder Auflösung von 1024 x 768 Anzeige mit 32-Bit-Pixelfarbe oder Auflösung von 800 x 600 Pixel 24-Bit-Farbe.

Firmware diese Modi Grafiken nicht unterstützt werden, Windows weiterhin Funktionen, aber alle Boot Anzeige wird Text-Modus und Englisch wiederhergestellt.

Windows 8.1, Windows Server 2012 R2, Windows 7, Windows Server 2008 R2 und Windows Server 2008 erfordern GOP ein Bild mit hoher Auflösung und animierte während des Startvorgangs angezeigt. Wenn GOP nicht verfügbar ist, verwendet Windows den video Graphics Array (VGA) Standard, um eine niedrigere Auflösung und eine einfache Statusanzeige anzuzeigen. Für eine optimale Boot Erfahrung mit diesen Versionen von Windows versiegelte Plattformen ohne die Erweiterung von Karten sicher Graphics-Cache-Modus zu starten und beseitigen Übergänge, die Text-Modus.

Bei jeder Ausführung einer Anwendung Windows EFI die Start-Managers Firmware weitergibt, müssen Plattform Firmware und die Start-Managers Firmware nicht den Framepuffer zu Zwecken verwenden.

### <a name="span-idinputatboottimespanspan-idinputatboottimespanspan-idinputatboottimespaninput-at-boot-time"></a><span id="Input_at_Boot_Time"></span><span id="input_at_boot_time"></span><span id="INPUT_AT_BOOT_TIME"></span>Geben Sie beim Starten

Für eine Plattform, die ein Gerät Konsole hat, erfordert die UEFI 2.0-Spezifikation die Firmware auf die einfache Eingabe Protokoll implementieren. Windows unterstützt dieses Protokoll für die lokale Tastatureingabe während des Startvorgangs.

### <a name="span-idnetworkbootspanspan-idnetworkbootspanspan-idnetworkbootspannetwork-boot"></a><span id="Network_Boot"></span><span id="network_boot"></span><span id="NETWORK_BOOT"></span>Netzwerkstart

Windows implementiert die Unterstützung für die Ausführung EFI Systemanalyse vor dem Start Environment (PXE) Base Code Protokoll. Windows wird dieses Protokoll verwendet, um über das Netzwerk starten und Windows Deployment Services (WDS) unterstützen.

### <a name="span-iddiskbootspanspan-iddiskbootspanspan-iddiskbootspandisk-boot"></a><span id="Disk_Boot"></span><span id="disk_boot"></span><span id="DISK_BOOT"></span>Datenträger Boot

Windows erfordert, dass Block e/a-Protokoll und Gerät Pfad-Protokoll für den Datenträger unterstützen, die die EFI-Systempartition und die Windows-Betriebssystem Partition enthält.

### <a name="span-idotherfirmwarebootrequirementsspanspan-idotherfirmwarebootrequirementsspanspan-idotherfirmwarebootrequirementsspanother-firmware-boot-requirements"></a><span id="Other_Firmware_Boot_Requirements"></span><span id="other_firmware_boot_requirements"></span><span id="OTHER_FIRMWARE_BOOT_REQUIREMENTS"></span>Sonstige Firmware Boot-Anforderungen

Damit ordnungsgemäßen Betrieb sichergestellt ist, erfordert Windows EFI-Firmware zur Einhaltung der angegebenen Spezifikation, Version. EFI-Firmware muss die entsprechende Version des EFI-Systemtabelle, EFI Boot Dienste und EFI Runtime Services vollständig implementieren. Andere bestimmte erforderlichen Protokolle und Spezifikationen zählen folgende:

-   **Vertrauenswürdige Netzwerke Group (TCG) EFI Spezifikationen**. Alle UEFI Plattformen, die ein Modul TPM (Trusted Platform) müssen die TCG EFI Plattform und Spezifikationen Protokollen implementieren.

-   **EFI\_PCI\_ROOT\_BRIDGE\_e/a\_PROTOKOLL**. Windows verwendet dieses Protokoll Wenn IEEE 1394 Boot Debuggen Windows Boot Configuration Data (BCD) angibt.

## <a name="span-idruntimerequirementsspanspan-idruntimerequirementsspanspan-idruntimerequirementsspanruntime-requirements"></a><span id="Runtime_Requirements"></span><span id="runtime_requirements"></span><span id="RUNTIME_REQUIREMENTS"></span>Common Language Runtime-Anforderungen


Windows minimiert Dienstabonnements UEFI Dienste während der Ausführung von Betriebssystem und möglichst nutzt die Laufzeit Firmware beispielsweise ACPI und Windows-Treiber. Windows verwendet die folgenden UEFI Runtime Dienste verwalten von NVRAM Starteinträge und Hardware Fehlerdatensätze nach ExitBootServices() aufgerufen wird.

-   GetVariable

-   GetNextVariableName

-   Funktionen ' SetVariable '

-   QueryVariableInfo

## <a name="span-idhibernationstates4transitionrequirementsspanspan-idhibernationstates4transitionrequirementsspanspan-idhibernationstates4transitionrequirementsspanhibernation-state-s4-transition-requirements"></a><span id="Hibernation_State__S4__Transition_Requirements"></span><span id="hibernation_state__s4__transition_requirements"></span><span id="HIBERNATION_STATE__S4__TRANSITION_REQUIREMENTS"></span>Anforderungen für den Umstieg von Ruhezustand (S4)


Dieser Abschnitt beschreibt die Anforderungen für die System- und Firmware Arbeitsspeicher, die im Zusammenhang mit Übergänge zu der Power Ruhezustand (S4).

### <a name="span-idsystemmemoryrequirementsspanspan-idsystemmemoryrequirementsspanspan-idsystemmemoryrequirementsspansystem-memory-requirements"></a><span id="System_Memory_Requirements"></span><span id="system_memory_requirements"></span><span id="SYSTEM_MEMORY_REQUIREMENTS"></span>Basisarbeitsspeicheranforderungen des Systems

Plattform-Firmware muss sicherstellen, dass physische Speicher des Betriebssystems konsistente über S4 Standbymodus Statusübergänge in Größe und Position.

Physische Speicher des Betriebssystems definiert ist, gemäß der Spezifikation ACPI 3.0 als Speicher, der von der Firmware System Adresse Map-Schnittstelle mit der ein Speicher als **AddressRangeReserved** beschrieben wird \[2\], **AddressRangeUnusable** \[5\], oder **undefiniert** \[einen beliebigen Wert größer als 5\].

### <a name="span-idfirmwarememoryrequirementsspanspan-idfirmwarememoryrequirementsspanspan-idfirmwarememoryrequirementsspanfirmware-memory-requirements"></a><span id="Firmware_Memory_Requirements"></span><span id="firmware_memory_requirements"></span><span id="FIRMWARE_MEMORY_REQUIREMENTS"></span>Firmware Arbeitsspeicheranforderungen

Auf einer Plattform UEFI muss Firmware Runtime Arbeitsspeicher über S4 Standbymodus Statusübergänge in Größe und Position konsistent sein. Common Language Runtime Arbeitsspeicher wird gemäß der Spezifikation UEFI als Speicher, der durch den Startdienst GetMemoryMap() mit dem Attribut beschrieben wird definiert **EFI\_SPEICHER\_RUNTIME**.

## <a name="span-idrequirementstoenableuefiplatformswithoutcsmspanspan-idrequirementstoenableuefiplatformswithoutcsmspanspan-idrequirementstoenableuefiplatformswithoutcsmspanrequirements-to-enable-uefi-platforms-without-csm"></a><span id="Requirements_to_Enable_UEFI_Platforms_without_CSM"></span><span id="requirements_to_enable_uefi_platforms_without_csm"></span><span id="REQUIREMENTS_TO_ENABLE_UEFI_PLATFORMS_WITHOUT_CSM"></span>So aktivieren Sie UEFI Plattformen ohne CSM Anforderungen


Erste Generation 64-Bit-UEFI Plattformen enthalten normalerweise eine Form von begrenzten BIOS Emulation wie etwa eine CSM die Möglichkeit zum Ausführen der 32-Bit-Betriebssystemen und Betriebssystemen, die keine für UEFI Unterstützung beibehalten. Vorhandene Windows Abhängigkeiten von INT 10 video BIOS-Funktionen sind ebenfalls eine CSM erforderlich.

Zur Reduzierung der Notwendigkeit einer CSM, und Start des Servers in der Zukunft zu verbessern, sind wir Zusammenarbeit mit der Branche zur Vermeidung von diese Abhängigkeit und Änderungen an Systemfirmware zu fördern.

Firmware Anforderungen:

**GOP**. Windows wird mit der GOP einen Frame-Puffer-Zeiger zur Startzeit für die Verwendung während der Laufzeit Betriebssystem abgerufen. GOP-Unterstützung ist unerlässlich ersetzen-VGA-Unterstützung und vermeiden Sie die Anforderung für eine CSM in zukünftigen Versionen von Windows.

**EFI ' Kapseln ' Dienste**. Windows kann mit dem Dienst EFI UpdateCapsule() zum Beibehalten von Informationen über einen Neustart des Systems und übergeben Sie diese Informationen an die Firmware. Dies würde potenziell lassen den Systembericht und/oder Antworten auf bestimmte Fehler auftreten, wenn das Boot-Gerät oder das Betriebssystem beschädigt oder anderweitig nicht verfügbar waren.

### <a name="span-idfirmwarerecommendationsspanspan-idfirmwarerecommendationsspanspan-idfirmwarerecommendationsspanfirmware-recommendations"></a><span id="Firmware_recommendations"></span><span id="firmware_recommendations"></span><span id="FIRMWARE_RECOMMENDATIONS"></span>Firmware Empfehlungen

Hinweis zu Herstellern Firmware: Es wird empfohlen, wenn Secure Boot deaktiviert ist, klicken Sie dann die Firmware die folgenden Aktionen aus, um Support optimal für frühere Versionen von Windows bereitstellen auslösen soll:

-   Aktivieren der für die Unterstützung von VGA CSM, obwohl nicht BIOS-Modus Emulation.

-   Aktivieren von Nachrichten während des POST-Vorgangs angezeigt, welche Tasten die Menüs Boot öffnen.

 

 





