---
title: Dumper
description: Dumper
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e5fec87c-6945-4611-8e50-52d279357004
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f29ff89ba1ac9204ac118851c54379274d126990
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dumper"></a>Dumper


Diese Aktion wird eine ANSI-Textdatei das Ablaufverfolgungsprotokoll ETL erzeugt.

``` syntax
-a dumper [-range T1 T2] [-stacktimeshifting] [exc_dpcisr] [-provider id1 id2 …] [-add_rawdata] [-add_pgodata] [-add_inline]
```

## <a name="options"></a>Options


<a href="" id="-ranget1-t2"></a>**-Bereichs** *T1 T2*  
Gibt nur Daten zwischen *T1* und *T2*, beide in Mikrosekunden Mal aus.

<a href="" id="-stacktimeshifting"></a>**-stacktimeshifting**  
Benutzer- und Kernel-Stapel kombiniert Fragmenten und platziert sie nach dem Triggerereignis.

<a href="" id="-exc-dpcisr"></a>**-Exc\_Dpcisr**  
Schließt in DPCs oder ISRs aufgewendete Zeit. DPC und Interrupt Tracing müssen für diese Option, um Wirkung aktiviert sein. Dies betrifft derzeit nur **Cswitch** Ereignisse.

<a href="" id="-providerid1-id2--"></a>**-Provider** *id1 id2...*  
Sichert Ereignisse für den angegebenen Anbieter. Erfordert als Eingabe eine beliebige Anzahl von Anbieter GUIDs.

<a href="" id="-add-rawdata"></a>**-Hinzufügen\_Rawdata**  
Fügt eine Linie unformatierte Informationen vor jeder-Ereignis.

<a href="" id="-add-pgodata"></a>**-Hinzufügen\_Pgodata**  
Jeder Rahmen hinzugefügt PGO Schulungsinformationen.

<a href="" id="-add-inline"></a>**-Hinzufügen\_Inline**  
Fügt einer Linie Funktionsnamen am Ende jeder Rahmen an.

## <a name="remarks"></a>Hinweise


Ereignisse in der Verfolgung werden in Form von Text ausgegeben.

## <a name="example"></a>Beispiel


Es folgt ein Beispiel für diese Aktion mit dem angegebenen Anbieter.

``` syntax
xperf -i trace.etl -o trace.etl.csv -a dumper -provider {315a8872-923e-4ea2-9889-33cd4754bf64} {7dd42a49-5329-4832-8dfd-43d979153a88}
```

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

[Zeit- und Timestamp-Formate](time-and-timestamp-formats.md)

 

 







