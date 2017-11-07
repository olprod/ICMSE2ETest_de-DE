---
title: OnOffTransitionConfiguration
description: OnOffTransitionConfiguration
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c9b194b8-c179-49da-ac8d-aae373c9d706
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ace632678e9c04ecf5f2676d5a16d70b91976072
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onofftransitionconfiguration"></a>OnOffTransitionConfiguration


Stellt einen ein-/ausschalten Übergang Konfiguration.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;**OnOffTransitionConfiguration**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<OnOffTransitionConfiguration Id = IdType
                              Name = string
                              Type = "On/Off - Boot" | "On/Off - HybridBoot" | "On/Off - Shutdown" | ...>

  <!-- Child elements -->
  PrepareSystem,
  NumberOfRuns,
  PostBootDelay,
  WakeupDelay,
  TransitionTag

</OnOffTransitionConfiguration>
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
<td><p>Identifiziert eindeutig den on/off Übergang Konfiguration.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>Gibt den Namen der Konfiguration.</p></td>
<td><p>string</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Typ</strong></p></td>
<td><p>Gibt den Typ des ein-/ausschalten Übergang.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Ein-/ausschalten - starten</p></li>
<li><p>Ein-/ausschalten - HybridBoot</p></li>
<li><p>Ein-/ausschalten - Herunterfahren</p></li>
<li><p>Ein-/ausschalten - RebootCycle</p></li>
<li><p>Ein-/ausschalten - Standby/fortsetzen</p></li>
<li><p>Ein-/ausschalten - Ruhezustand/fortsetzen</p></li>
</ul></td>
<td><p>Ja</p></td>
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
<td><p>[PrepareSystem](preparesystem.md)</p></td>
<td><p>Gibt an, ob das System ein-/ausschalten Übergang vorzubereiten.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[NumberOfRuns](numberofruns.md)</p></td>
<td><p>Gibt die Anzahl der Läufe im den Übergang ein-/ausschalten.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="odd">
<td><p>[PostBootDelay](postbootdelay.md)</p></td>
<td><p>Gibt die Verzögerung nach dem starten.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
<tr class="even">
<td><p>[WakeupDelay](wakeupdelay.md)</p></td>
<td><p>Gibt die Verzögerung beim künftige aus dem Zustand.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
</tr>
<tr class="odd">
<td><p>[TransitionTag](transitiontag.md)</p></td>
<td><p>Gibt das Übergang-Tag.</p></td>
<td><p>Optional, wird 0 (null) oder 1.</p></td>
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
<td><p>[OnOffTransitionConfigurations](onofftransitionconfigurations.md)</p></td>
<td><p>Stellt eine Auflistung von ein-/ausschalten Übergang.</p></td>
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

 

 







