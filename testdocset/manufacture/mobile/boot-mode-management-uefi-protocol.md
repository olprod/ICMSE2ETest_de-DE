---
author: kpacquer
Description: Die Boot-Modus Management Protocol wird der Startmodus bestimmt das Betriebssystem verwenden soll, wenn er beginnt.
ms.assetid: 9782c51d-8915-43ef-8a64-9c8be9dc228d
MSHAttr: PreferredLib:/library/windows/hardware
title: Boot-Modus Management UEFI-Protokoll
ms.openlocfilehash: 6d572f877c2c6e8d2ac89d420588151d6621c407
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-mode-management-uefi-protocol"></a>Boot Modus Management UEFI-Protokoll


Boot-Modus-Management-Protokoll wird der Startmodus bestimmt das Betriebssystem verwenden soll, wenn er beginnt.

## <a name="span-idefibootmodemgmtprotocolspanspan-idefibootmodemgmtprotocolspanefibootmodemgmtprotocol"></a><span id="EFI_BOOT_MODE_MGMT_PROTOCOL"></span><span id="efi_boot_mode_mgmt_protocol"></span>EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL


Dieser Abschnitt enthält eine ausführliche Beschreibung der **EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL**.

**GUID**

``` syntax
#define EFI_BOOT_MODE_MGMT_PROTOCOL_GUID \
   { 0xBE464946, 0x9787, 0x4FEB, { 0xBD, 0x71, 0x14, 0xC1, 0xC5, 0x2D, 0x69, 0xD1 } }
```

**Revisionsnummer**

``` syntax
#define EFI_BOOT_MODE_MGMT_PROTOCOL_REVISION 0x00010000
```

**Struktur der Protokoll-Schnittstelle**

``` syntax
typedef struct _EFI_BOOT_MODE_MGMT_PROTOCOL {
    UINT32                 Revision;
    EFI_SET_BOOT_MODE_INFO SetBootModeInfo;
    EFI_GET_BOOT_MODE_INFO GetBootModeInfo;
} EFI_BOOT_MODE_MGMT_PROTOCOL;
```

**Elemente des Objekts**

<span id="Revision"></span><span id="revision"></span><span id="REVISION"></span>**Revision**  
Die Überarbeitung der **EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL** entspricht. Alle zukünftige Überarbeitungen müssen abwärts kompatibel sein. Wenn eine zukünftige Version nicht abwärts kompatibel ist, muss eine andere GUID verwendet werden.

<span id="GetBootModeInfo"></span><span id="getbootmodeinfo"></span><span id="GETBOOTMODEINFO"></span>**GetBootModeInfo**  
Bestimmt den Startmodus der beim Start des Betriebssystems verwendet werden sollte. Finden Sie unter [EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. GetBootModeInfo](efi-boot-mode-mgmt-protocol-getbootmodeinfo.md)

<span id="SetBootModeInfo"></span><span id="setbootmodeinfo"></span><span id="SETBOOTMODEINFO"></span>**SetBootModeInfo**  
Gibt den verwendeten Betriebssystems sollten beim Start einer optionalen Profilname, Boot-Modus. Finden Sie unter [EFI\_BOOT\_MODUS\_MGMT\_PROTOKOLL. SetBootModeInfo](efi-boot-mode-mgmt-protocol-setbootmodeinfo.md)

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


**Kopfzeile:** Vom Benutzer generiert

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Fertigung-Modus](manufacturing-mode.md)

 

 






