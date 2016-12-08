---
title: "Abrufen von Arbeitsplätzen"
description: "Get-Operation Arbeitsplätzen Ruft die Informationen zur aktiven Arbeitsplätzen im Windows Store for Business."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 32945788-47AC-4259-B616-F359D48F4F2F
ms.openlocfilehash: 6eb0c2d40da3a1f1fd277a91e6c696a07cef3259
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-seats"></a>Abrufen von Arbeitsplätzen

**Arbeitsplätzen Get** -Vorgang werden die Informationen zur aktiven Arbeitsplätzen in Windows Store für Business abgerufen.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Inventory/ {ProductId} / {SkuId} / Seats?continuationToken = {ContinuationToken}&amp;MaxResults = {MaxResults}</p></td>
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
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>Optional</p></td>
</tr>
<tr class="even">
<td><p>maxResults</p></td>
<td><p>Int32</p></td>
<td><p>Optional Default = 25, Maximum = 100</p></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthält [SeatDetailsResultSet](data-structures-windows-store-for-business.md#seatdetailsresultset)an.

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
<td><p>Ursache: Nicht online</p></td>
</tr>
</tbody>
</table>

 

 





