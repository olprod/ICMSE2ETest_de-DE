---
title: Boot
description: Boot
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c6bf946c-9da7-4147-a37e-c117e1ea1fff
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: eef76519936de09ada2829e8a0b58b2ba1bcf4e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot"></a>Boot


Diese Aktion erzeugt einen XML-Bericht, der die verschiedenen Kriterien in Boot zusammenfasst.

``` syntax
-a boot [-minCPUToShow <n>] [-maxFilesToShow <n>] [-expectedProcessesFile <file name>] [-minIntervalToShow <n>] [-userShellExecutable]
```

## <a name="options"></a>Options


<a href="" id="-mincputoshow-n-"></a>**-MinCPUToShow***&lt;n&gt;*  
* &lt;n&gt; * gibt den minimalen Prozentsatz der CPU-Auslastung im Bereich von 0 bis 100 angezeigt.

<a href="" id="-maxfilestoshow-n-"></a>**MaxFilesToShow -***&lt;n&gt;*  
* &lt;n&gt; * gibt die maximale Anzahl von Dateien angezeigt.

<a href="" id="-expectedprocessesfile-file-name-"></a>**-ExpectedProcessesFile***&lt;Dateiname&gt;*  
* &lt;Dateinamen&gt; * gibt eine Textdatei, die enthält eine Liste der erwarteten Prozessnamen an.

<a href="" id="-minintervaltoshow-n-"></a>**-MinIntervalToShow***&lt;n&gt;*  
* &lt;n&gt; * gibt den Zeitpunkt der kürzeste Intervall in Mikrosekunden angezeigt. Der Standardwert ist 10.

<a href="" id="-usershellexecutable"></a>**-userShellExecutable**  
Benutzer-Shell ausführbare an in das Ablaufverfolgungsprotokoll gesucht werden soll. Der Standardwert ist Explorer.exe.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







