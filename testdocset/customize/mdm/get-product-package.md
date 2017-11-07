---
title: Abrufen der Produktpaket
description: "Get-Paket Vorgang ruft die Informationen über eine bestimmte Anwendung in der Windows Store for Business."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4314C65E-6DDC-405C-A591-D66F799A341F
ms.openlocfilehash: 2ddc282b8aa3c6445f40c2325c9914d0e8be6096
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-product-package"></a>Abrufen der Produktpaket

Der **erste Produktpaket** Vorgang ruft die Informationen über eine bestimmte Anwendung in der Windows Store für Business ab.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Products/ {Product ID} / {SkuId} /Packages/ {PackageId}</p></td>
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
<td><p>packageId</p></td>
<td><p>string</p></td>
<td><p>Erforderlich.</p></td>
</tr>
</tbody>
</table>
   

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
<p>Ursache: Ungültiger parameter</p>
<p>Details: Zeichenfolge</p></td>
<td><p>ProductId, SkuId oder PackageId können sein.</p></td>
</tr>
<tr class="even">
<td><p>404</p></td>
<td><p>Nicht gefunden</p></td>
<td></td>
<td></td>
<td><p>Typ: Produkt-SKU</p></td>
</tr>
<tr class="odd">
<td><p>409</p></td>
<td><p>Conflict</p></td>
<td></td>
<td><p>Ursache: Nicht gehört</p></td>
<td></td>
</tr>
</tbody>
</table>


## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Der Antworttext enthält [ProductPackageDetails](data-structures-windows-store-for-business.md#productpackagedetails).

 






