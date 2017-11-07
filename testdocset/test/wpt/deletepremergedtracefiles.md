---
title: DeletePreMergedTraceFiles
description: DeletePreMergedTraceFiles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6c9424dd-6ec3-4835-af18-541cec28da76
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d88b882e827bbed2808572376a8e85d96d3a3389
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deletepremergedtracefiles"></a>DeletePreMergedTraceFiles


Gibt an, ob premerged Ereignis ablaufverfolgungsprotokolldateien (ETL) zu löschen.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;[TraceMergeProperty](tracemergeproperty.md)&gt;

               &lt;**DeletePreMergedTraceFiles**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<DeletePreMergedTraceFiles Value = boolean>
</DeletePreMergedTraceFiles>
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
<td><p>Gibt an, ob premerged ETL-Dateien zu löschen.</p></td>
<td><p>boolean</p></td>
<td><p>Nein</p></td>
<td><p>wahr</p></td>
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
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>Enthält Konfigurationen, die angewendet werden, wenn mehrere Profile Aufzeichnungen zusammengeführt werden.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







