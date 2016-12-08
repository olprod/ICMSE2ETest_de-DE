---
title: Abrufen der Produktpakete
description: "Get-Pakete Vorgang werden die Informationen in der Windows Store für Business Applications abgerufen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 039468BF-B9EE-4E1C-810C-9ACDD55C0835
ms.openlocfilehash: 4df80d40cc7d7efed8604fb067431bc7d9304cd5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-product-packages"></a>Abrufen der Produktpakete

Der **Produktpakete Get** -Vorgang ruft die Informationen zu in Windows Store für Business Applications.

## <a name="request"></a>Anforderung

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Methode</th>
<th>Anforderungs-URI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>GET</p></td>
<td><p>https://bspmts.MP.Microsoft.com/v1/Products/ {ProductId} / {SkuId} / Pakete</p></td>
</tr>
</tbody>
</table>

 
### <a name="uri-parameters"></a>URI-Parameter

Die folgenden Parameter können in der Anforderung URI angegeben werden.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Produkt-ID</p></td>
<td><p>string</p></td>
<td><p>Erforderlich. Produkt-ID für eine Anwendung, die durch den Speicher für Unternehmen verwendet wird.</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>Erforderlich. Produkt-ID, die eine bestimmte SKU einer Anwendung angibt.</p></td>
</tr>
</tbody>
</table>
   
 
<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fehlercode</th>
<th>Beschreibung</th>
<th>"Wiederholen"</th>
<th>Datenfeld</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>400</p></td>
<td><p>Ungültige Parameter</p></td>
<td><p>Nein</p></td>
<td><p>Parametername</p>
<p>Ursache: Fehlender Parameter oder ungültiger parameter</p>
<p>Details: Zeichenfolge</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>Ursache: Nicht gehört</p></td>
</tr>
</tbody>
</table>


## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthält [ProductPackageSet](data-structures-windows-store-for-business.md#productpackageset).

 





