---
title: Beenden
description: Beenden
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ebde3a43-c6c9-47d4-b6f1-8b1dae313af3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 118752f3c606b4e87667a437c241ab893a4ab14c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stop"></a>Beenden


Zeigt Trace Stop-Optionen.

``` syntax
xperf [-stop [LoggerNames]|[ProfileFileName!ProfileName|SessionName merged.etl]]|[-stopall]|[-cancel rofileFileName!ProfileName|SessionName [NoDelete]] [-d merged.etl] [-heap|-critsec]
```

## <a name="parameters"></a>Parameter


<a href="" id="-stoploggernames-profilefilename-profilename-sessionname-merged-etl"></a>**-Beenden** *LoggerNames | ProfileFileName! Profilname | Sitzungsname "merged.ETL" enthält*  
Im *LoggerNames*angegebene Protokollierungsmodule deaktiviert, Protokollierungsmodule im Profil *Profilname* definiert, in der Datei *ProfileFileName* deaktiviert und verbindet die ETL-Dateien in "merged.ETL" enthält, oder deaktiviert die Protokollierung *Sitzungsname* definiert, in der Datei *ProfileFileName* und verbindet die ETL-Datei "merged.ETL" enthält.

<a href="" id="-stopall"></a>**-stopall**  
Deaktiviert alle protokollierungssitzungen.

<a href="" id="-cancelprofilefilename-profilename-sessionname--nodelete-"></a>**-Abbrechen** *ProfileFileName! Profilname | Sitzungsname \[NoDelete\] *  
Deaktiviert Protokollierungsmodule im Profil *Profilname* in der Datei *ProfileFileName* definiert und löscht die Ablaufverfolgungsdateien oder deaktiviert die Protokollierung *Sitzungsname* in der Datei *ProfileFileName* definiert und verbindet die ETL-Datei "merged.ETL" enthält. Wenn *NoDelete* angegeben wird, werden die Ablaufverfolgungsdateien nicht gelöscht.

<a href="" id="-dmerged-etl"></a>**-d** *"merged.ETL" enthält*  
Verbindet die ETL-Dateien der Protokollierung beendeten Sitzungen "merged.ETL" enthält. Wenn keine Sitzung explizit beendet wird, wird die NT-Kernel-Protokollierung implizit beendet.

<a href="" id="-boottraceoff"></a>**-boottrace** *deaktiviert*  
Eine Boot Verfolgung deaktiviert.

<a href="" id="-heap"></a>**-Heap**  
Heap-Protokollierung wird beendet.

<a href="" id="-critsec"></a>**-critsec**  
Kritischen Abschnitt-Protokollierung wird beendet.

## <a name="remarks"></a>Hinweise


Derzeit nur ein Heap Trace oder kritischen Abschnitt Trace aktiv sein kann zu einem Zeitpunkt. Aus diesem Grund **-Heap** und **- Critsec** schließen sich gegenseitig aus. Wenn *LoggerNames* nicht angegeben ist oder **-d** ist mit keiner angegeben **-Beenden** noch **-Stopall** vorhanden, die Kernelprotokollierung wurde beendet.

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







