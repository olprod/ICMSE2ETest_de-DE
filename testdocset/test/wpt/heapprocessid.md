---
title: HeapProcessId
description: HeapProcessId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b0d95f7c-af59-4452-9a60-3ab1e06b072a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3f24db5e55580ecb98bca7f2712e6cb899daf49a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapprocessid"></a>HeapProcessId


Einen Prozess Heap identifiziert eindeutig.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[HeapEventProvider](heapeventprovider.md)&gt;

          &lt;[HeapProcessIds](heapprocessids.md)&gt;

               &lt;**HeapProcessId**

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;[HeapEventProviderId](heapeventproviderid.md)&gt;

                                   &lt;[HeapProcessIds](heapprocessids.md)&gt;

                                        &lt;**HeapProcessId**&gt;

                              &lt;[HeapEventProvider](heapeventprovider.md)&gt;

                                   &lt;[HeapProcessIds](heapprocessids.md)&gt;

                                        &lt;**HeapProcessId**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<HeapProcessId Value = unsignedLong>
</HeapProcessId>
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
<td><p>Anzahl der Heap abgeschlossen.</p></td>
<td><p>unsignedLong</p></td>
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
<td><p>[HeapProcessIds](heapprocessids.md)</p></td>
<td><p>Stellt eine Auflistung von Heap-Prozess-IDs.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







