---
title: TraceMergeProperties
description: TraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7771cdc2-3573-4a3b-a52b-70ef77f706dc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 24eb13751ef5965d605df6efba20873355abb35d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracemergeproperties"></a>TraceMergeProperties


Stellt eine Auflistung von [TraceMergeProperty](tracemergeproperty.md) Elements an. Dieses Element ist nur zur internen Verwendung.

## <a name="element-syntax"></a>Syntax für das Element


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**TraceMergeProperties**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<TraceMergeProperties>

  <!-- Child elements -->
  TraceMergeProperty

</TraceMergeProperties>
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
<th>Requirment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>Enthält Konfigurationen, die angewendet werden, wenn Ereignis Ablaufverfolgungsprotokoll (ETL)-Dateien mehrere Profile zusammengeführt werden.</p></td>
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
<td><p>[WindowsPerformanceRecorder](windowsperformancerecorder.md)</p></td>
<td><p>Stellt Metadaten für die Erstellung des Profils an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird veranschaulicht, wie dieses Element definieren.

``` syntax
<TraceMergeProperties>
  <TraceMergeProperty
    Id="TraceMerge_Default"
    Name="TraceMerge_Default">
    <DeletePreMergedTraceFiles
      Value="true"/>
    <CustomEvents>
      <CustomEvent
        Value="ImageId"/>
      <CustomEvent
        Value="BuildInfo"/>
      <CustomEvent
        Value="VolumeMapping"/>
      <CustomEvent
        Value="EventMetadata"/>
      <CustomEvent
        Value="PerfTrackMetadata"/>
      <CustomEvent
        Value="WinSAT"/>
      <CustomEvent
        Value="NetworkInterface"/>
    </CustomEvents>
  </TraceMergeProperty>
</TraceMergeProperties>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

[Vererbung (engl.)](inheritance.md)

 

 







