---
title: PostBootDelay
description: PostBootDelay
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: fef41639-e619-456f-95a6-776aa0b0036a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ca63939b95f6f0ec24ddb234944f78c04dd57323
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="postbootdelay"></a>PostBootDelay


Gibt die Länge des die Verzögerung in Sekunden, nach dem Starten eines [OnOffTransitionConfiguration](onofftransitionconfiguration.md) -Elements an.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;[OnOffTransitionConfiguration](onofftransitionconfiguration.md)&gt;

               &lt;**PostBootDelay**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<PostBootDelay Value = SimpleDelayValueType>
</PostBootDelay>
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
<td><p>Beschreibt die Länge der die Verzögerung in Sekunden an.</p></td>
<td><p>Ganze Zahl im Bereich von 1 bis 3600.</p></td>
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


Im folgenden Beispiel wird veranschaulicht, wie dieses Element konfigurieren.

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

[WakeupDelay](wakeupdelay.md)

 

 







