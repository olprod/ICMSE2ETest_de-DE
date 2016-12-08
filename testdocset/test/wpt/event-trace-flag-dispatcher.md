---
title: EREIGNIS\_TRACE\_FLAG\_VERTEILER
description: EREIGNIS\_TRACE\_FLAG\_VERTEILER
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 939bd14d-06f4-4109-9e7c-95e35815c2e3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2d62e9b6b16e378584f959f1ebb5cab35f198e8c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtraceflagdispatcher"></a>EREIGNIS\_TRACE\_FLAG\_VERTEILER


Dieses Kennzeichen ermöglicht das Erfassen von Ereignissen Thread bereit.

``` syntax
#define EVENT_TRACE_FLAG_DISPATCHER 0x00000800
```

## <a name="remarks"></a>Hinweise


Ein einzelnes Kernel-Steuerelement Ablaufverfolgungsflag aktiviert oder deaktiviert die Protokollierung von einen Kernel-Ereignistyp. Weitere Informationen zu Kernel Flags und die zugehörigen Kernelereignisse, finden Sie unter [EREIGNIS\_TRACE\_EIGENSCHAFTEN Struktur](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409).

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Ablaufverfolgungsflags-Steuerelement](trace-control-flags.md)

 

 







