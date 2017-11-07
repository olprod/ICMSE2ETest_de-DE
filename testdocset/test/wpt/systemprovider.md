---
title: '&quot;Systemprovider&quot;'
description: '&quot;Systemprovider&quot;'
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 20262ec7-6b20-42cb-903f-1db57a9f1e58
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9cd04d5cc683ae5545f19e3876c6b245e6cf703f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemprovider"></a>"Systemprovider"


Beschreibt die Konfiguration, um den Anbieter im Kernelmodus zu aktivieren. Die Definition des Systems Anbieter gibt an, welche System Schlüsselwörtern, Stapel und Pooltags zu aktivieren.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**SystemProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                            &lt;**SystemProvider**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<SystemProvider Id   = IdType
                Base = string>

  <!-- Child elements -->
  Keywords,
  Stacks,
  PoolTags

</SystemProvider>
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
<td><p>Den Systemanbieter identifiziert eindeutig.</p></td>
<td><p>Zeichenfolge, muss mindestens ein Zeichen sein und darf keine Doppelpunkte (:)) oder Leerzeichen enthalten.</p></td>
<td><p>Ja</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Base</strong></p></td>
<td><p>Gibt an, der Basis des Anbieters System. Abgeleitete Anbieter haben alle Attribute des Anbieters Basis standardmäßig. Diese können überschrieben werden, indem sie in den abgeleiteten Anbieter explizit angeben.</p></td>
<td><p>string</p></td>
<td><p>Nein</p></td>
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
<td><p>[Schlüsselwörter (in "Systemprovider")](keywords--in-systemprovider-.md)</p></td>
<td><p>Stellt eine Auflistung von Schlüsselwörtern und benutzerdefinierte Schlüsselwörter.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="even">
<td><p>[Stapel](stacks.md)</p></td>
<td><p>Stellt eine Auflistung von Stapeln.</p></td>
<td><p>Erforderlich, genau 1.</p></td>
</tr>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>Stellt eine Auflistung von Pooltags.</p></td>
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
<td><p>[Profile](profiles.md)</p></td>
<td><p>Stellt eine Auflistung von Kollektoren, Anbieter und Profilen.</p></td>
</tr>
<tr class="even">
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>Stellt einen System Collector Bezeichner dar.</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>Hinweise


Informationen zum Pooltags definieren finden Sie unter [PoolTag](pooltag.md).

## <a name="example"></a>Beispiel


``` syntax
<SystemProvider Id="system-provider">
  <Keywords>
    <Keyword Value="ProcessThread"/>
    <Keyword Value="Loader"/>
    <Keyword Value="CSwitch"/>
  </Keywords>
  <Stacks>
    <Stack Value="ThreadCreate"/>
    <Stack Value="ReadyThread"/>
    <Stack Value="CSwitch"/>
  </Stacks>
  <PoolTags>
    <PoolTag Value="a*"/>
    <PoolTag Value="b*"/> 
    <PoolTag Value="c*"/> 
    <PoolTag Value="d*"/> 
  </PoolTags>
</SystemProvider>
```

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







