---
title: CellularSettings CSP
description: CellularSettings CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ce8b6f16-37ca-4aaf-98b0-306d12e326df
ms.openlocfilehash: 6e049d70a9540916dac3689ccf423e1e00e6757f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cellularsettings-csp"></a>CellularSettings CSP


Der Dienstanbieter für CellularSettings Konfiguration wird verwendet, um Mobilfunk Einstellungen auf einem mobilen Gerät konfigurieren.

Die folgende Abbildung zeigt den CellularSettings Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz Clientbereitstellung (OMA CP) verwendet. Das Protokoll OMA DM wird mit dieser Konfigurationsdienstanbieter nicht unterstützt.

![Bereitstellung\-Csp\-Cellularsettings](images/provisioning-csp-cellularsettings.png)

<a href="" id="dataroam"></a>**DataRoam**  
Optional Ganzzahl Gibt die roaming-Wert. Gültige Werte sind:

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Wert</th>
<th>Einstellung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Kein Roaming</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Kein Roaming (oder nationalen roaming, falls zutreffend)</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Roaming</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






