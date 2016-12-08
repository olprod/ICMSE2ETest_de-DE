---
title: HeapProcessIds
description: HeapProcessIds
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bc7619b5-11f7-48d1-93f3-5103fbfc52ce
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e50cb7e5c0fa7ad5f6a983332615582101114730
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapprocessids"></a>HeapProcessIds


Stellt eine Auflistung von Heap Prozess-IDs.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[HeapEventProvider](heapeventprovider.md)&gt;

           &lt;**HeapProcessIds**&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;[HeapEventProviderId](heapeventproviderid.md)&gt;

                                   &lt;**HeapProcessIds**&gt;

                              &lt;[HeapEventProvider](heapeventprovider.md)&gt;

                                   &lt;**HeapProcessIds**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<HeapProcessIds Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  HeapProcessId

</HeapProcessIds>
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
<td><p><strong>Verwendung</strong></p></td>
<td><p>Gibt an, ob Elemente <strong>HeapProcessId</strong> festgelegt oder hinzugefügt werden soll.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Gruppe</p></li>
<li><p>Add</p></li>
<li><p>Entfernen</p></li>
</ul></td>
<td><p>Nein</p></td>
<td><p>Gruppe</p></td>
</tr>
</tbody>
</table>

 

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
<td><p>[HeapProcessId](heapprocessid.md)</p></td>
<td><p>Einen Prozess Heap identifiziert eindeutig.</p></td>
<td><p>Erforderlich, mindestens 1.</p></td>
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
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>Stellt einen Heap Ereignisanbieter.</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProviderId](heapeventproviderid.md)</p></td>
<td><p>Stellt eine Heap Ereignis Provider-ID an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







