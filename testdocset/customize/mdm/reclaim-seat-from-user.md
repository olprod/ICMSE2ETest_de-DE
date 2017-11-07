---
title: Freigeben von Benutzer Arbeitsplatz
description: "Bei der Rückgewinnung Sitz von Benutzeraktionen zurückgegeben freigegebenen Arbeitsplätzen für einen Benutzer in der Windows Store für Business."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E2C3C899-D0AD-469A-A319-31A420472A4C
ms.openlocfilehash: a087b900bd75fdb8c4679c7c9550c92f54845b02
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="reclaim-seat-from-user"></a>Freigeben von Benutzer Arbeitsplatz

Der Vorgang **Arbeitsplatz von Benutzer freizugeben** zurückgegeben freigegebenen Arbeitsplätzen für einen Benutzer in Windows Store für Business.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Inventory/ {ProductId} / {SkuId} /Seats/ {Benutzername}</p></td>
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
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthalten [SeatDetails](data-structures-windows-store-for-business.md#seatdetails).

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
<th>Fehlercode</th>
<th>Beschreibung</th>
<th>Wiederholen Sie den Vorgang</th>
<th>Datenfeld</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>400</p></td>
<td><p>Ungültige Parameter</p></td>
<td><p>Nein</p></td>
<td><p>Parametername</p>
<p>Ursache: Ungültiger parameter</p>
<p>Details: Zeichenfolge</p></td>
<td><p>Ungültige kann ProductId, SkuId oder UserName enthalten.</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td><p>Typ: Inventar Benutzer, Arbeitsplatz</p>
<p>Werte: ProductId/SkuId, UserName, ProductId/SkuId/Benutzername</p></td>
<td><p>ItemType: Inventar Benutzer, Arbeitsplatz</p>
<p>Werte: ProductId/SkuId, UserName, ProductId/SkuId/Benutzername</p></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>Ursache: Nicht online</p></td>
<td></td>
</tr>
</tbody>
</table>

 

 





