---
title: Kollektoren
description: Kollektoren
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e94d9c16-0aa7-4af3-80df-5ef086e74293
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 103e8b347e7f0e4a9a231a227a9b4fb477b91fa4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="collectors"></a>Kollektoren


Stellt eine Auflistung von System Collector-IDs, Collector Bezeichner und optional Heap Collector Bezeichner.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;**Collectors**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<Collectors Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  SystemCollectorId,
  EventCollectorId,
  HeapEventCollectorId

</Collectors>
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
<td><p>Gibt an, ob Kollektoren festgelegt oder hinzugefügt werden soll.</p></td>
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
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>Stellt einen System Collector Bezeichner dar.</p></td>
<td><p>Optional, wird 0 (null) oder 1. Es muss mindestens ein Collector vom System oder Ereignis.</p></td>
</tr>
<tr class="even">
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>Stellt einen Bezeichner der Ereignis-Sammlung.</p></td>
<td><p>Optional, wird NULL oder mehr. Es muss mindestens eine Collector vom System oder Ereignis.</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollectorId](heapeventcollectorid.md)</p></td>
<td><p>Stellt einen Bezeichner für Heap-Ereignis-Sammlung.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
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
<td><p>[Profil](profile-wpr.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien und Kollektoren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







