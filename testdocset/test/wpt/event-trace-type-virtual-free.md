---
title: EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_FREI
description: EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_FREI
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1c547a82-5e5e-4c0e-b3b5-5830f5a52bab
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 140c5a5bb2d1e789a359f5c3bf107dae29de9e0a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypevirtualfree"></a>EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_FREI


Dieses Kennzeichen ermöglicht stapelablaufverfolgung für kostenlose Ereignisse virtueller Arbeitsspeicher.

``` syntax
#define EVENT_TRACE_TYPE_VIRTUAL_FREE 0x63
```

## <a name="remarks"></a>Hinweise


Dieser Ereignistyp ähnelt der Ereignistypen in der **-EREIGNIS verwendet\_TRACE\_EIGENSCHAFTEN. EnableFlags** Member ist aber speziell für die Kernel Trace-Steuerelement-API.

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Verfolgen von Steuerelement Ereignistypen](trace-control-event-types.md)

 

 







