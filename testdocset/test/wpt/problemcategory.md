---
title: ProblemCategory
description: ProblemCategory
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 93db9658-1b8a-4713-8cac-702034d017d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 455036a267e2e8e4ba6352fcad6d82d4dbceea20
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="problemcategory"></a>ProblemCategory


Stellt eine Problemkategorie für das Profil. Dieses Element ist nur zur internen Verwendung.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[ProblemCategories](problemcategories.md)&gt;

                    &lt;**ProblemCategory**&gt;-

## <a name="syntax"></a>Syntax


``` syntax
<ProblemCategory Value = "First Level Triage" | "CPU" | "Storage" ...>
</ProblemCategory>
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
<td><p>Beschreibt die Art des Problems.</p></td>
<td><p>Dieses Attribut kann einen der folgenden Werte aufweisen:</p>
<ul>
<li><p>Erste Ebene Ursachenanalyse</p></li>
<li><p>CPU</p></li>
<li><p>Storage</p></li>
<li><p>Netzwerk</p></li>
<li><p>Arbeitsspeicher</p></li>
<li><p>Multimedia</p></li>
<li><p>Energie</p></li>
<li><p>Ein-/ausschalten Übergang</p></li>
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
<td><p>[ProblemCategories](problemcategories.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







