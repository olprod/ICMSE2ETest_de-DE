---
title: Dienste
description: Dienste
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 139a09db-6c62-449a-9369-2219cc99e823
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a768599f24288300a234a8d8d7246e712a8e7312
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="services"></a>Dienste


Diese Aktion ergibt eine Textdatei, die im Zusammenhang mit Services Metriken zusammenfasst.

``` syntax
-a services [-range T1 T2] [-poiThreshold_ContainerInit <t>] [-poiThreshold_ImageLoad <t>] [-poiThreshold_ServiceInit <t>]
```

## <a name="parameters"></a>Parameter


<a href="" id="-ranget1-t2"></a>**-Bereich** *T1 T2*  
Zeigt Daten zwischen Mal *T1* und *T2*, beide in Mikrosekunden.

<a href="" id="-poithreshold-containerinit-t-"></a>**PoiThreshold -\_ContainerInit***&lt;t&gt; *  
Container Initialisierung jederzeit größer als *t*, in Mikrosekunden, als ein Interessenbereich Kennzeichen.

<a href="" id="-poithreshold-imageload-t-"></a>**-PoiThreshold\_ImageLoad***&lt;t&gt; *  
Flags beliebiges Bild Ladezeit größer als *t*, in Mikrosekunden, als ein Interessenbereich.

<a href="" id="-poithreshold-serviceinit-t-"></a>**-PoiThreshold\_ServiceInit***&lt;t&gt; *  
Kennzeichen Service Initialisierung jederzeit größer als *t*, in Mikrosekunden, als ein Interessenbereich.

## <a name="remarks"></a>Hinweise


Der Standardwert ist keine Dienste als interessante Aspekte zu kennzeichnen. In Millisekunden werden immer angezeigt.

## <a name="related-topics"></a>Verwandte Themen


[Xperf Aktionen](xperf-actions.md)

 

 







