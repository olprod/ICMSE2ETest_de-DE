---
title: cswitch
description: cswitch
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bb976f48-b804-4de3-bbd1-108cbad6e922
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c174c46e5e0744f1cf5ccf89aace7cabe744dcf1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cswitch"></a>cswitch


Diese Aktion wird eine Berichtsdatei, die eine die Metriken für Kontextwechsel Zusammenfassung erzeugt.

``` syntax
-a cswitch [-avail [n]] [-util [n]] [-process] [-thread] [-exc_dpcisr] [-range T1 T2]
```

## <a name="options"></a>Options


<a href="" id="-avail-n-"></a>**-berufen***\[n\]*  
Zeigt die CPU-Verfügbarkeit für *n* -Sekunde-Intervallen. Der Standardwert ist 1.

<a href="" id="-util-n-"></a>**-zur bandbreitenauslastung durch***\[n\]*  
Zeigt die CPU-Auslastung für *n* -Sekunde-Intervallen. Der Standardwert ist 1.

<a href="" id="-process"></a>**-Prozess**  
CPU-Auslastung pro Prozess zeigt, wie aus Kontextdaten Switch abgeleitet.

<a href="" id="-thread"></a>**-Thread**  
Zeigt CPU-Auslastung pro Thread aus Kontextdaten Switch abgeleitet.

<a href="" id="-exc-dpcisr"></a>**-Exc\_Dpcisr**  
Schließt die Verfügbarkeit, die Auslastung Prozess und die Thread-Berichte in DPC/ISR aufgewendete Zeit. Für diese Option, um die Wirkung muss DPC-Interrupt Tracing aktiviert sein.

<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Zeigt Daten zwischen Mal *T1* und *T2*, beide in Mikrosekunden.

## <a name="remarks"></a>Hinweise


Wenn kein Berichtstyp ausgewählt ist, werden standardmäßig die CPU-Verfügbarkeit im Bericht angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







