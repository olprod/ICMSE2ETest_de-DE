---
title: EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_ZUORDNEN
description: EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_ZUORDNEN
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 91ba3533-f652-4073-9dce-6511730a801e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: bcba130b65a8e84e9bee114ed947855536c8479b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventtracetypevirtualalloc"></a>EREIGNIS\_TRACE\_TYP\_VIRTUELLEN\_ZUORDNEN


Dieses Kennzeichen ermöglicht stapelablaufverfolgung für virtueller Arbeitsspeicher Zuweisung Ereignisse.

``` syntax
#define EVENT_TRACE_TYPE_VIRTUAL_ALLOC 0x62
```

## <a name="remarks"></a>Hinweise


Dieser Ereignistyp ähnelt der Ereignistypen, die in der **-EREIGNIS verwendet\_TRACE\_EIGENSCHAFTEN. EnableFlags** Member ist aber speziell für die Kernel Trace-Steuerelement-API.

**Anforderungen:**

**Versionen:** Verfügbar in Windows Vista beginnen. Diese Struktur ist mit Windows Performance Analyzer verteilt.

**Kopfzeilen:** In KernelTraceControl.h deklariert. Enthalten Sie KernelTraceControl.h.

**Bibliothek:** In KernelTraceControl.dll enthalten sind.

## <a name="related-topics"></a>Verwandte Themen


[Verfolgen von Steuerelement Ereignistypen](trace-control-event-types.md)

 

 







