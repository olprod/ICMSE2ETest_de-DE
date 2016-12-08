---
title: PoolTags
description: PoolTags
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 819088ce-bfda-4866-a97c-a85b768c5f7a
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 19ea66975d92987f116498f7671b853d48ad957e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="pooltags"></a>PoolTags


Stellt eine Auflistung von maximal vier Pooltags. Wenn das Attribut **Operation** angegeben wird, können die **PoolTag** Elemente festzulegen oder zur Auflistung hinzugefügt.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

   &lt;[Profile](profiles.md)&gt;

      &lt;[SystemProvider](systemprovider.md)&gt;

         &lt;**PoolTags**&gt;

&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

   &lt;[Profile](profiles.md)&gt;

      &lt;[Profile](profile-wpr.md)&gt;

         &lt;[Collectors](collectors.md)&gt;

            &lt;[SystemCollectorId](systemcollectorid.md)&gt;

               &lt;[SystemProviderId](systemproviderid.md)&gt;

                    &lt;**PoolTags**&gt;

&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

   &lt;[Profile](profiles.md)&gt;

      &lt;[Profile](profile-wpr.md)&gt;

         &lt;[Collectors](collectors.md)&gt;

            &lt;[SystemCollectorId](systemcollectorid.md)&gt;

               &lt;[SystemProvider](systemprovider.md)&gt;

                    &lt;**PoolTags**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<PoolTags Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  PoolTag

</PoolTags>
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
<td><p><strong>Verwendung</strong></p></td>
<td><p>Gibt an, ob Elemente <strong>PoolTag</strong> festgelegt oder hinzugefügt werden soll.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Gruppe</p></li>
<li><p>Add</p></li>
<li><p>Entfernen</p></li>
</ul></td>
<td><p>Nein</p></td>
<td><p>Gruppe</p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>Untergeordnete Elemente

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
<td><p>[PoolTag](pooltag.md)</p></td>
<td><p>Beschreibt die Pooltags zum Analysieren von Poolseiten aktiviert sein.</p></td>
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
<td><p>["Systemprovider"](systemprovider.md)</p></td>
<td><p>Stellt einen Systemanbieter.</p></td>
</tr>
<tr class="even">
<td><p>[SystemProviderId](systemproviderid.md)</p></td>
<td><p>Stellt eine System Provider-ID an.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







