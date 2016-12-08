---
title: TraceMergeProperty
description: TraceMergeProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b3640f46-7bf4-4ee3-8094-ace27f275bd8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 28c2e1e57024550e063c2f3ec73787fe32a8fef1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracemergeproperty"></a>TraceMergeProperty


Enthält Konfigurationen, die angewendet werden, wenn mehrere Profile Aufzeichnungen zusammengeführt werden. Dieses Element ist nur zur internen Verwendung.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;**TraceMergeProperty**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<TraceMergeProperty Id   = IdType
                    Name = string
                    Base = string>

  <!-- Child elements -->
  DeletePreMergedTraceFiles,
  FileCompression
  CustomEvents
</TraceMergeProperty>
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
<td><p>Dieses Element identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen dieses Elements.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt die Basis dieses Elements an. Abgeleitete Elemente haben alle Attribute von der Basis standardmäßig. Sie können diese Attribute außer Kraft setzen, indem sie in den abgeleiteten Elements explizit angeben.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
<th>Anforderung</th>
<th>Mögliche Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[DeletePreMergedTraceFiles](deletepremergedtracefiles.md)</p></td>
<td><p>Gibt an, ob premerged Ereignis ablaufverfolgungsprotokolldateien (ETL) zu löschen.</p></td>
<td><p>Optional</p></td>
<td><p>True, false</p></td>
</tr>
<tr class="even">
<td><p>[FileCompression](filecompression.md)</p></td>
<td><p>Gibt an, ob die ETL-Datei zu komprimieren.</p></td>
<td><p>Optional</p></td>
<td><p>True, false</p></td>
</tr>
<tr class="odd">
<td><p>[CustomEvents](customevents.md)</p></td>
<td><p>Stellt eine Auflistung von benutzerdefinierten Ereignissen.</p></td>
<td><p>Optional</p></td>
<td><p>True, false</p></td>
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
<td><p>[TraceMergeProperties](tracemergeproperties.md)</p></td>
<td><p>Stellt eine Auflistung von Trace Merge Aktionsroutine.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird veranschaulicht eine Trace Merge Eigenschaftendefinition.

``` syntax
<TraceMergeProperty
  Id="TraceMerge_Default"
  Name="TraceMerge_Default">
  <DeletePreMergedTraceFiles
    Value="true"/>
  <FileCompression
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

 

 







