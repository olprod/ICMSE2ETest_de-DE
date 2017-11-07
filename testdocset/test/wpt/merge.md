---
title: merge
description: merge
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d450807c-ad86-4d1d-a089-0b3cfa86219c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4a87bf2fb40b24b76ce1cde4238393b7e3a94fd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="merge"></a>merge


Zeigt Trace Merge-Optionen.

``` syntax
xperf -merge trace1.etl trace2.etl … merged.etl
```

## <a name="example"></a>Beispiel


Im folgende Beispiel werden die einzelnen Ablaufverfolgungsdateien in "merged.ETL" enthält und fügt Identifikationsinformationen Bild und manifest Ereignisinformationen, die für die sichere Symbol Decodierung erforderlich ist.

``` syntax
-merge trace1.etl trace2.etl … merged.etl
```

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







