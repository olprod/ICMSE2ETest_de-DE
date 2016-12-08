---
author: kpacquer
Description: "Definiert die möglichen Boot-Modi, die das Betriebssystem verwenden können, wenn er beginnt."
ms.assetid: cb78662f-8ce0-4adb-97ad-e8520c8513fd
MSHAttr: PreferredLib:/library/windows/hardware
title: "EFI\\_BOOT\\_MODUS\\_INFO-Aufzählung"
ms.openlocfilehash: a049094786b7ad4767391ec4b25b9bba871f75ef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="efibootmodeinfo-enumeration"></a>EFI\_BOOT\_MODUS\_INFO-Aufzählung


Definiert die mögliche Boot-Modi, die das Betriebssystem beim Start verwenden kann.

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>Die Syntax


``` syntax
typedef enum _EFI_OS_BOOT_MODE {
    EfiOsBootModeFullOs = 0,
    EfiOsBootModeManufacturingOs = 1
    EfiOsBootModeMax
} EFI_OS_BOOT_MODE, *PEFI_OS_BOOT_MODE;
```

## <a name="span-idconstantsspanspan-idconstantsspanspan-idconstantsspanconstants"></a><span id="Constants"></span><span id="constants"></span><span id="CONSTANTS"></span>Konstanten


<span id="EfiOsBootModeFullOs"></span><span id="efiosbootmodefullos"></span><span id="EFIOSBOOTMODEFULLOS"></span>**EfiOsBootModeFullOs**  
Das Gerät sollte normalerweise in das Betriebssystem starten.

<span id="EfiOsBootModeManufacturingOs"></span><span id="efiosbootmodemanufacturingos"></span><span id="EFIOSBOOTMODEMANUFACTURINGOS"></span>**EfiOsBootModeManufacturingOs**  
Das Gerät ist in der Fertigung Modus.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Boot Modus Management UEFI-Protokoll](boot-mode-management-uefi-protocol.md)

 

 






