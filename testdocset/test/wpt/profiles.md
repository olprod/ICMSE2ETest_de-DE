---
title: Profile
description: Profile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 00b0d6dc-d14a-4c70-ab7b-4aa2250c2395
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c8338f3b8c12bb0a2412b8e4dcec84ea4fa418d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profiles"></a>Profile


Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**Profiles**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Profiles>

  <!-- Child elements -->
  SystemCollector,
  EventCollector,
  HeapEventCollector,
  SystemProvider,
  EventProvider,
  HeapEventProvider,
  Profile

</Profiles>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente


### <a name="attributes"></a>Attribute

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[SystemCollector](systemcollector.md)</p></td>
<td><p>Stellt einen Collector des Systems.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>Stellt eine Ereignissammlung.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollector](heapeventcollector.md)</p></td>
<td><p>Stellt eine Ereignissammlung Heap dar.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>["Systemprovider"](systemprovider.md)</p></td>
<td><p>Stellt einen Systemanbieter.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="odd">
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>Einen Ereignisanbieter darstellt.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>Stellt einen Heap Ereignisanbieter.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
</tr>
<tr class="odd">
<td><p>[Profil](profile-wpr.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien und Kollektoren.</p></td>
<td><p>1 bis 4 erforderlich.</p></td>
</tr>
</tbody>
</table>

 

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
<td><p>[WindowsPerformanceRecorder](windowsperformancerecorder.md)</p></td>
<td><p>Stellt Metadaten für die Erstellung des Profils an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


In einem **WindowsPerformanceRecorder** -Element kann nur ein **Profile** -Element definiert werden.

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







