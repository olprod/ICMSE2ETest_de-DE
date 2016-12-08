---
title: Abrufen von Arbeitsplatz
description: "Get-Operation Arbeitsplatz Ruft die Informationen zu einer aktiven Lizenzen für einen angegebenen Benutzer im Windows Store for Business ab."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 715BAEB2-79FD-4945-A57F-482F9E7D07C6
ms.openlocfilehash: 2e417407dae8f9a59d662988328f1d61b8b4ab4d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-seat"></a>Abrufen von Arbeitsplatz

Der **erste Arbeitsplatz** Vorgang ruft die Informationen zu einer aktiven Lizenzen für einen angegebenen Benutzer in der Windows Store für Business ab.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Inventory/ {ProductId} / {SkuId} /Seats/ {Benutzername}</p></td>
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
<td><p>username</p></td>
<td><p>string</p></td>
<td><p>UserPrincipalName (UPN) erfordert. Der Benutzername des Zielbenutzerkontos.</p></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthält [SeatDetails](data-structures-windows-store-for-business.md#seatdetails).

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
<th>"Wiederholen"</th>
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
<p>Ursache: Fehlender Parameter oder ungültiger parameter</p>
<p>Details: Zeichenfolge</p></td>
<td><p>Ungültige kann ProductId, SkuId oder Username enthalten.</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td></td>
<td><p>ItemType: Inventar, Benutzer, Arbeitsplatz</p>
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

 

 





