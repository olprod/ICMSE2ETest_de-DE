---
title: FileCompression
description: FileCompression
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fcc2cd71-7246-40f5-ba9c-2ba79b8ffdfc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 59500ff5c9286dcfc96850467b842873c978953b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="filecompression"></a>FileCompression


Gibt an, ob die ETL-Datei komprimiert werden. Dieses Element ist nur zur internen Verwendung.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;[TraceMergeProperty](tracemergeproperty.md)&gt;

               &lt;**FileCompression**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<FileCompression = Value boolean>
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
<td><p>Gibt an, ob die ETL-Datei komprimiert werden.</p></td>
<td><p>Boolean-Wert.</p></td>
<td><p>Nein</p></td>
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
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>Enthält Konfigurationen, die angewendet werden, wenn mehrere Profile Aufzeichnungen zusammengeführt werden. Dieses Element ist nur zur internen Verwendung.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







