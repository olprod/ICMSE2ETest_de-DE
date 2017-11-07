---
title: "Schlüsselwörter (in &quot;Systemprovider&quot;)"
description: "Schlüsselwörter (in &quot;Systemprovider&quot;)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bf98056c-7863-4430-9522-ac2f74048481
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8a03fcc10d4499bcca1df8f09b8d6ad362de1c92
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keywords-in-systemprovider"></a>Schlüsselwörter (in "Systemprovider")


Stellt eine Auflistung von Schlüsselwörtern. Wenn das **Vorgang** -Attribut angegeben ist, können die **Schlüsselwort** -Elemente festzulegen oder zur Auflistung hinzugefügt.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;**Keywords (in SystemProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;**Keywords (in SystemProvider)**&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;**Keywords (in SystemProvider)**&gt;****

## <a name="syntax"></a>Syntax


``` syntax
<Keywords Operation = OperationEnumeration = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  Keyword,
  CustomKeyword

</Keywords>
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
<td><p>Gibt an, ob die Schlüsselwörter festgelegt oder hinzugefügt werden soll.</p></td>
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
<td><p>[Schlüsselwort (in "Systemprovider")](keyword--in-systemprovider-.md)</p></td>
<td><p>Beschreibt die Kernel Flags, die für den Kernelmodus-Sitzung aktiviert sein können.</p></td>
<td><p>Erforderlich, 1 oder mehr.</p></td>
</tr>
<tr class="even">
<td><p>[CustomKeyword](customkeyword.md)</p></td>
<td><p>Beschreibt eine benutzerdefinierte Schlüsselwortsuche.</p></td>
<td><p>Optional, wird NULL oder mehr.</p></td>
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

 

 







