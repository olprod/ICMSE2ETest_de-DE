---
title: PoolTag
description: PoolTag
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e544351c-bb0a-4450-a6d4-5fc230bf684d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3369d9d70f83295944f6cddf17085863d4908bae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="pooltag"></a>PoolTag


Beschreibt die Pooltags zum Analysieren von Poolseiten aktiviert sein.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[PoolTags](pooltags.md)&gt;

                     &lt;**PoolTag**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;[PoolTags](pooltags.md)&gt;

                                     &lt;**PoolTag**&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;[PoolTags](pooltags.md)&gt;

                                     &lt;**PoolTag**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<PoolTag" Value = SystemPoolTagAttributeType>
</PoolTag>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente


### <a name="attributes"></a>Attribute

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Beschreibung</th>
<th>Datentyp</th>
<th>Erforderlich</th>
<th>Standard</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Wert</strong></p></td>
<td><p>Beschreibt den Wert dieses Elements.</p></td>
<td><p>Zeichenfolge, die bis zu vier Zeichen lang sein muss.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>Stellt eine Auflistung von Pooltags.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







