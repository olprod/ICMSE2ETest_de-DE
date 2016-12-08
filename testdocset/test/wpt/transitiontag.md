---
title: TransitionTag
description: TransitionTag
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ead6001f-02f3-4a85-a207-7af8e558a8f2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: bd0a8f0ccbf6609448d32cd47304498867da8203
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="transitiontag"></a>TransitionTag


Stellt das Übergang Tag für ein [OnOffTransitionConfiguration](onofftransitionconfiguration.md) -Element.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;[OnOffTransitionConfiguration](onofftransitionconfiguration.md)&gt;

               &lt;**TransitionTag**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<TransitionTag Value = TransitionTagType>
</TransitionTag>
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
<td><p>Zeichenfolge, die im Dateinamen eingefügt wird.</p></td>
<td><p>Eine Zeichenfolge, die keine der folgenden Zeichen enthält:</p>
<ul>
<li><p>Schrägstrich (/)</p></li>
<li><p>Umgekehrter Schrägstrich)</p></li>
<li><p>Doppelpunkt (:).)</p></li>
<li><p>Sternchen (*)</p></li>
<li><p>Fragezeichen (?)</p></li>
<li><p>Senkrechter Strich (|)</p></li>
<li><p>Spitze Klammer rechts (&gt;)</p></li>
<li><p>Doppeltes Anführungszeichen (&quot;)</p></li>
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
<td><p>[OnOffTransitionConfiguration](onofftransitionconfiguration.md)</p></td>
<td><p>Stellt einen ein-/ausschalten Übergang Konfiguration.</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>Beispiel


Im folgenden Codebeispiel wird veranschaulicht, wie dieses Element konfigurieren.

``` syntax
<OnOffTransitionConfiguration
  Id="OnOffTransitionConfiguration_Default_Boot"
  Name="OnOffTransitionConfiguration_Default_Boot"
  Type="On/Off - Boot">
  <PrepareSystem Value="true"/>
  <NumberOfRuns Value="3"/>
  <PostBootDelay Value="120"/>
  <WakeupDelay Value="60"/>
  <TransitionTag Value="Boot"/>
</OnOffTransitionConfiguration>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







