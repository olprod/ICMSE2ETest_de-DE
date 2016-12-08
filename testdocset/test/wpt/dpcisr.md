---
title: dpcisr
description: dpcisr
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8bab6760-0aa9-403b-b552-eabe21f780dd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c75dfb97509785e1676afd7927b1b51421b58885
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dpcisr"></a>dpcisr


Diese Aktion erzeugt einen Bericht, der die verschiedenen Metriken in Bezug auf verzögerte Verfahren zusammenfasst Anrufe (DPCs) und Interrupt-Routinen (ISRs).

``` syntax
-a dpcisr [-dpc | -isr] [-summary] [-interval [n]] [-bucket [n]] [-range T1 T2 ]
```

## <a name="options"></a>Options


<a href="" id="-dpc"></a>**Dpc-**  
Werden die Statistiken für DPCs nur.

<a href="" id="-isr"></a>**Isr-**  
Werden die Statistiken für ISRs nur.

<a href="" id="-summary"></a>**-Zusammenfassung**  
Zeigt eine Übersicht über.

<a href="" id="-interval-dt-"></a>**-Intervall***\[dt\]*  
Zeigt Verwendungsbericht für Intervalle *dt* Sekunden. Der Standardwert ist 1.

<a href="" id="-bucket-dt-"></a>**-Bucket***\[dt\]*  
Histogramm für Intervalle *dt* Sekunden anzeigen. Der Standardwert ist 2.

<a href="" id="-ranget1-t2"></a>**-Bereich** *T1 T2*  
Verzögerung zwischen *T1* und *T2*anzeigen.

## <a name="remarks"></a>Hinweise


Wenn kein Datentyp angegeben ist, wird die Aktion einen Bericht der DPCs und ISRs. Wenn kein Berichtstyp angegeben wird, wird standardmäßig alle drei Berichte zu drucken: DCPs, ISRs und Zusammenfassung.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







