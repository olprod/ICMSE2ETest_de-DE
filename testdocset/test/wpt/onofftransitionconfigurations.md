---
title: OnOffTransitionConfigurations
description: OnOffTransitionConfigurations
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7046c6c0-8e74-47a1-a4ce-47a7dc5a43c0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fa1106ba070654cd7fa4fcd407f2ff3e2f00422d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onofftransitionconfigurations"></a>OnOffTransitionConfigurations


Stellt eine Auflistung von ein-/ausschalten Übergänge.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**OnOffTransitionConfigurations**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<OnOffTransitionConfigurations>

  <!-- Child elements -->
  OnOffTransitionConfiguration

</OnOffTransitionConfigurations>
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
<td><p>[OnOffTransitionConfiguration](onofftransitionconfiguration.md)</p></td>
<td><p>Stellt einen ein-/ausschalten Übergang Konfiguration.</p></td>
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
<td><p>[WindowsPerformanceRecorder](windowsperformancerecorder.md)</p></td>
<td><p>Stellt Metadaten für die Erstellung des Profils an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







