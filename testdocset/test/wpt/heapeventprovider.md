---
title: HeapEventProvider
description: HeapEventProvider
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0f2fe538-bfd6-490b-b1c8-8f151153b8ef
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 661e82aba10d7558a4651f7fe05770fe3c67c32d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventprovider"></a>HeapEventProvider


Stellt einen Anbieter von Heap Ereignisse für das Profil.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**HeapEventProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;**HeapEventProvider**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<HeapEventProvider Id   = IdType
                   Base = string>

  <!-- Child elements -->
  HeapProcessIds

</HeapEventProvider>
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
<td><p><strong>ID</strong></p></td>
<td><p>Den Heap Ereignisanbieter identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt den Basiskalender Heap-Provider an.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
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
<td><p>[HeapProcessIds](heapprocessids.md)</p></td>
<td><p>Stellt eine Auflistung von Heap-Prozess-IDs.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
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
<td><p>[HeapEventProviders](heapeventproviders.md)</p></td>
<td><p>Stellt eine Auflistung der Heap Ereignis Anbieter-IDs und Heap Anbieter.</p></td>
</tr>
<tr class="even">
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Abgeleitete Heap Anbieter haben alle Attribute des Anbieters Basis standardmäßig ein. Diese können überschrieben werden, indem sie in den abgeleiteten Anbieter explizit angeben. Weitere Informationen finden Sie unter [Vererbung](inheritance.md).

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







