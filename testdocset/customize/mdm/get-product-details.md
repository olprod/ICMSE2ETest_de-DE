---
title: Hier finden Sie Produktdetails
description: "Die Product Details Abrufvorgang Ruft den Produktinformationen aus Windows Store für Business für eine bestimmte Anwendung."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: BC432EBA-CE5E-43BD-BD54-942774767286
ms.openlocfilehash: e1ddf0d1a0b43eeef4b81e33cedc004c3f822c95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-product-details"></a>Hier finden Sie Produktdetails

Der **Hier finden Sie Produktdetails** Vorgang ruft den Produktinformationen aus Windows Store für Business für eine bestimmte Anwendung ab.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Products/ {ProductId} / {SkuId}</p></td>
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
<td></td>
</tr>
</tbody>
</table>

 
## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Die Antwort enthält [Produktdetails](data-structures-windows-store-for-business.md#productdetails)an.

 






