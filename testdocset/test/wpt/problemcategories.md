---
title: ProblemCategories
description: ProblemCategories
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 02997314-797c-468c-b1d7-3650e6f969e3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 19b5df59c583560b3c44059be54fbf2bad397fb5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="problemcategories"></a>ProblemCategories


Stellt eine Auflistung von Problemkategorien. Dieses Element ist nur zur internen Verwendung.

## <a name="element-hierarchy"></a>Hierarchie-Elements


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;**ProblemCategories**&gt;

## <a name="syntax"></a>Syntax


``` syntax
<ProblemCategories Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  ProblemCategory

</ProblemCategories>
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
<td><p>Gibt an, ob <strong>ProblemCategory</strong> Elemente festzulegen oder hinzugefügt werden soll.</p></td>
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
<td><p>[ProblemCategory](problemcategory.md)</p></td>
<td><p>Stellt eine Problemkategorie.</p></td>
<td><p>Erforderlich, 1 oder mehr.</p></td>
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
<td><p>[Profil](profile-wpr.md)</p></td>
<td><p>Stellt eine Auflistung von Problemkategorien und Kollektoren.</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Elemente](elements.md)

 

 







