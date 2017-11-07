---
title: Hier finden Sie lokalisierte Produktdetails
description: Die Get lokalisierter Product Details Vorgang ruft die Lokalisierungsinformationen zur eines Produkts aus dem Windows Store for Business.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: EF6AFCA9-8699-46C9-A3BB-CD2750C07901
ms.openlocfilehash: 0618f220c2381f1ed42be3da5cc0a5484bde23b8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-localized-product-details"></a>Hier finden Sie lokalisierte Produktdetails

Das **Abrufen lokalisierter Produktdetails** Vorgang ruft die Lokalisierungsinformationen zur eines Produkts aus der Windows Store für Business.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Products/ {Product ID} / {SkuId} /LocalizedDetails/ {Sprache}</p></td>
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
<td><p>language</p></td>
<td><p>string</p></td>
<td><p>Erforderlich. Sprache im ISO-Format, wie En-us, En-ca.</p></td>
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
<th>Wiederholen Sie den Vorgang</th>
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
<td><p>Typ: ProductId, SkuId, Sprache</p></td>
</tr>
</tbody>
</table>

 

## <a name="response"></a>Antwort

Die Antwort enthält [LocalizedProductDetail](data-structures-windows-store-for-business.md#localizedproductdetail)an.

 






