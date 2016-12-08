---
title: cpudisk
description: cpudisk
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2332140d-cc89-4896-b877-d0478af890a8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6ca386a9e5f8b9e654b9686763a7f0852ec16656
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cpudisk"></a>cpudisk


Diese Aktion erzeugt einen Bericht, der die verschiedenen Metriken in Bezug auf die CPU und die Datenträgertypen zusammenfasst.

``` syntax
-a cpudisk [-thread] [-exc_dpcisr] [-pids ...] [-exes ..] [-marks ..] [-times ..]
```

## <a name="options"></a>Options


<a href="" id="-thread"></a>**-Thread**  
Thread-Level-Bericht.

<a href="" id="-exc-dpcisr"></a>**-Exc\_Dpcisr**  
Schließt DPC/ISR Zeit von Prozess-Thread Zeit an, wenn DPC/ISR Ereignisse in der Verfolgung vorhanden sind.

<a href="" id="-pids-pid-"></a>**PID -***&lt;pid&gt;*  
Process-IDs werden in den Bericht aufgenommen.

<a href="" id="-exes-name-"></a>**-EXE-Dateien***&lt;Namen&gt;*  
Process Namen, die in den Bericht einbezogen.

<a href="" id="-marks-mark-"></a>**-markiert***&lt;markieren&gt;*  
Markiert, die die Zeitintervalle im Bericht festzulegen.

<a href="" id="-timest1-t2"></a>**-Zeiten** *T1 T2*  
Zeitstempel, die die Zeitintervalle in den Bericht festzulegen.

## <a name="remarks"></a>Hinweise


Wenn keine **PID -** oder **-exe-Dateien** angegeben sind, werden alle Prozesse in den Bericht einbezogen werden.

Wenn keine **-markiert** oder **-Zeiten** werden angegeben, in die Spuren markiert oder Trace Start- und Endzeit aus, wenn weniger als zwei verwenden in der Verfolgung vorhanden sind werden verwendet, um den Bericht Zeitintervalle festzulegen.

Um Absatzmarken in die Ablaufverfolgung zu deaktivieren, geben Sie ein leeres **– markiert** Option.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







