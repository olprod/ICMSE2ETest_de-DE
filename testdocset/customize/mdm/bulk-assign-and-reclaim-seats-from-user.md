---
title: "Massen zuweisen und freizugeben Arbeitsplätzen von Benutzern"
description: "Das gleichzeitige zuweisen und Arbeitsplätzen von Benutzern, den Vorgang zurückgegeben, freigegeben oder zugewiesen Arbeitsplätzen im Windows Store für Business freizugeben."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 99E2F37D-1FF3-4511-8969-19571656780A
ms.openlocfilehash: edfe6d2d8a2475789fedae09fb751943bc266833
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bulk-assign-and-reclaim-seats-from-users"></a>Massen zuweisen und Freigeben von Arbeitsplätzen von Benutzern

Die Operation **Bulk zuweisen und Arbeitsplätzen von Benutzern freigegeben** zurück freigegeben oder in Windows Store für Business Arbeitsplätzen zugewiesen.

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
<td><p>POST</p></td>
<td><p>Https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory/{productId}/{skuId}/Seats</p></td>
</tr>
</tbody>
</table>

 
### <a name="uri-parameters"></a>URI-Parameter

Folgende Parameter können in den Anforderungs-URI angegeben werden.

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
<tr class="odd">
<td><p>username</p></td>
<td><p>string</p></td>
<td><p>Erfordert UserPrincipalName (UPN). Der Benutzername des Zielbenutzerkontos.</p></td>
</tr>
<tr class="even">
<td><p>seatAction</p></td>
<td><p>[SeatAction](data-structures-windows-store-for-business.md#seataction)</p></td>
<td></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Antworttext enthält [BulkSeatOperationResultSet](data-structures-windows-store-for-business.md#bulkseatoperationresultset).

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
<th>Wiederholen Sie den Vorgang</th>
<th>Datenfeld</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td><p>Typ: Inventar</p>
<p>Werte: ProductId/SkuId</p></td>
</tr>
</tbody>
</table>

 

 





