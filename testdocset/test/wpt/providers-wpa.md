---
title: Anbieter
description: Anbieter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 19c60e7c-2673-4e7c-9b04-978ac94ce812
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e93a58e7493fa0db5fdd7aa43dc43943f558c1be
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="providers"></a>Anbieter


Zeigt verfügbaren Anbieter und Gruppen.

``` syntax
xperf -providers [Installed|I] [Registered|R] [KernelFlags|KF] [KernelGroups|KG] [Kernel|K]
```

## <a name="remarks"></a>Hinweise


Diese Option fragt alle bekannten/installiert und registriert Anbieter als sowie alle bekannten Kernel Flags und Gruppen.

Die Optionen in der folgenden Tabelle werden unterstützt.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ich, installiert</strong></p></td>
<td><p>Enthält installiert/bekannten Anbieter.</p></td>
</tr>
<tr class="even">
<td><p><strong>R registriert</strong></p></td>
<td><p>Enthält registrierte Anbieter.</p></td>
</tr>
<tr class="odd">
<td><p><strong>KF KernelFlags</strong></p></td>
<td><p>Kernel Flags enthält.</p></td>
</tr>
<tr class="even">
<td><p><strong>KG KernelGroups</strong></p></td>
<td><p>Kernel-Gruppen enthält.</p></td>
</tr>
<tr class="odd">
<td><p><strong>K, Kernel</strong></p></td>
<td><p>Umfasst Kernel Flags und Gruppen. Verknüpfung für &quot;KF KG&quot;.</p></td>
</tr>
</tbody>
</table>

 

Wenn keine Optionen angegeben sind, sind alle Anbieter in der Ausgabe enthalten.

## <a name="related-topics"></a>Verwandte Themen


[Xperf-Optionen](xperf-options.md)

 

 







