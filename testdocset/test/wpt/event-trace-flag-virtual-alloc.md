---
title: EREIGNIS\_TRACE\_FLAG\_VIRTUELLEN\_ZUORDNEN
description: EREIGNIS\_TRACE\_FLAG\_VIRTUELLEN\_ZUORDNEN
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 01bbdf2d-20e2-4588-a90b-4c962e69cbc1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1870a8563d20cefe4aa5def802319af3d5ce23e6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtraceflagvirtualalloc"></a>EREIGNIS\_TRACE\_FLAG\_VIRTUELLEN\_ZUORDNEN


Dieses Kennzeichen ermöglicht das Erfassen von virtuellen Zuweisungen und kostenlose Ereignissen.

``` syntax
#define EVENT_TRACE_FLAG_VIRTUAL_ALLOC 0x00004000
```

## <a name="remarks"></a>Hinweise


Ein einzelnes Kernel-Steuerelement Ablaufverfolgungsflag aktiviert oder deaktiviert die Protokollierung von einen Kernel-Ereignistyp. Weitere Informationen zu Kernel Flags und die zugehörigen Kernelereignisse, finden Sie unter [EREIGNIS\_TRACE\_EIGENSCHAFTEN Struktur](http://go.microsoft.com/fwlink/p/?linkid=212231&clcid=0x409).

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Ablaufverfolgungsflags-Steuerelement](trace-control-flags.md)

 

 







