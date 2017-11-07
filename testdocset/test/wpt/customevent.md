---
title: CustomEvent
description: CustomEvent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4ce7091b-4e6a-40c3-aeff-1c9434310f44
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 19c80247cddf024308c66245263210c6e1a0ec4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customevent"></a>CustomEvent


Stellt ein benutzerdefiniertes Ereignis.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;[TraceMergeProperty](tracemergeproperty.md)&gt;

               &lt;[CustomEvents](customevents.md)&gt;

                    &lt;**CustomEvent**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<CustomEvent Value = "None" | "ImageId" | "BuildInfo" | ...>
</CustomEvent>
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
<td><p>Beschreibt den Wert des benutzerdefinierten Ereignisses.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Keine</p></li>
<li><p>ImageId</p></li>
<li><p>BuildInfo</p></li>
<li><p>VolumeMapping</p></li>
<li><p>EventMetadata</p></li>
<li><p>PerfTrackMetadata</p></li>
<li><p>WinSAT</p></li>
<li><p>NetworkInterface</p></li>
</ul></td>
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
<td><p>[CustomEvents](customevents.md)</p></td>
<td><p>Stellt eine Auflistung von benutzerdefinierten Ereignissen.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird veranschaulicht, wie dieses Element in der Definition eines Trace Merge-Eigenschaft verwendet wird.

``` syntax
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
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







