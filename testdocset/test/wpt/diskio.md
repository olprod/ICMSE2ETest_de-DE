---
title: diskio
description: diskio
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7df30160-5a77-40f9-a03f-f21fec9cbafb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 89f6722a7631b92b2377e582032158fa6c52cdbf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diskio"></a>diskio


Diese Aktion erzeugt einen Bericht, der die Metriken für den Datenträger-e/a zusammenfasst.

``` syntax
-a diskio [-util <n>] [-summary] [-counts] [-detail] [-overlap] [-range T1 T2]
```

## <a name="options"></a>Options


<a href="" id="-util-n-"></a>**-zur bandbreitenauslastung durch***\[n\]*  
Zeigt die festplattenauslastung für n-Sekunden-Intervallen. Der Standardwert ist 1 Sekunde.

<a href="" id="-summary"></a>**-Zusammenfassung**  
Zeigt ein e/a-Zusammenfassungsbericht für jede Datei.

<a href="" id="-detail"></a>**-Details**  
Zeigt Details der einzelnen e/a-Ereignisse.

<a href="" id="-overlap"></a>**-überlappen**  
Zeigt überlappende e/a-Ereignisse.

<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Zeigt Daten zwischen Zeit *T1* und *T2*, beide in Mikrosekunden.

## <a name="remarks"></a>Hinweise


Wenn kein Berichtstyp ausgewählt ist, werden standardmäßig Datenträger Auslastung Bericht angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







