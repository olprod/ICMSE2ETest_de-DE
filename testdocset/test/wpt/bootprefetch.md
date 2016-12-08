---
title: bootprefetch
description: bootprefetch
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 482e724b-bf10-4181-a77f-40e5fdc8db7e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 18e149dd2865c29ae2fa04e9c8009f862330cdbd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootprefetch"></a>bootprefetch


Diese Aktion sortiert und Ereignisse, die bei Verwendung das **Weiter Trace Capture** -Tool für Boot relevant sind zusammengefasst.

``` syntax
bootprefetch [-summary | -events [-pattern [-type name]] [-range T1 T2] | disktime]
```

## <a name="options"></a>Options


<a href="" id="-xml"></a>**Xml-**  
Zeigt die Ausgabe im XML-Format. Dies funktioniert nur mit derzeit **-Zusammenfassung**.

<a href="" id="-summary"></a>**-Zusammenfassung**  
Zeigt die Zusammenfassung der Boot vorab.

<a href="" id="-events"></a>**-Ereignisse**  
Sichert ReadyBoot Ereignisse mit Earliness Informationen.

<a href="" id="-pattern"></a>**-Muster**  
Verwendet nur in Verbindung mit **-Ereignisse**. Bei der Sicherung von Ereignissen sichert auch überlappende Ereignisse.

<a href="" id="-typename"></a>**-Typ** *Namen*  
Verwendet nur in Verbindung mit **-Muster**. Gibt nur den angegebenen Typ der Ereignisse bei der Sicherung von Ereignissen in Muster anzeigen. *Name* ist einer der folgenden Werte: "Zusammenfassung", "Einlesen", "verpassen", "ausstehender" oder "Schreiben".

<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Verwendet nur in Verbindung mit **-Ereignisse**. Verarbeiten Sie ReadyBoot Ereignisse zwischen Zeiten *T1* und *T2*abgeschlossen.

<a href="" id="-disktime"></a>**-disktime**  
Zeigt die Datenträger Zeit Aufschlüsselung Boot vorab.

## <a name="remarks"></a>Hinweise


Wenn kein Berichtstyp ausgewählt ist, werden standardmäßig die Zusammenfassung angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







