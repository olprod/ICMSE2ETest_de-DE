---
title: Offline-Lizenz abrufen
description: "Die offline-Lizenz Abrufvorgang werden die offline Lizenzinformationen eines Produkts aus dem Windows Store für Business abgerufen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 08DAD813-CF4D-42D6-A783-994A03AEE051
ms.openlocfilehash: 80773fece46c5ccfc8219e8aaa3c5d70d8bce6a5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-offline-license"></a>Offline-Lizenz abrufen

Der Vorgang **offline-Lizenz abrufen** Ruft die offline Lizenzinformationen eines Produkts aus dem Windows Store for Business ab.

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
<td><p>https://bspmts.MP.Microsoft.com/v1/Products/ {ProductId} / {SkuId} /OfflineLicense/ {ContentId}</p></td>
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
<td><p>Erforderlich. Gibt ein bestimmtes Produkt, das erworben wurde.</p></td>
</tr>
<tr class="even">
<td><p>skuId</p></td>
<td><p>string</p></td>
<td><p>Erforderlich. Die SKU-Bezeichner.</p></td>
</tr>
<tr class="odd">
<td><p>contentId</p></td>
<td><p>string</p></td>
<td><p>Erforderlich. Eine bestimmte Anwendung identifiziert.</p></td>
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
<td><p>Ursache: Nicht im Besitz nicht offline</p></td>
</tr>
</tbody>
</table>


## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Die Antwort enthält [OfflineLicense](data-structures-windows-store-for-business.md#offlinelicense).

 






