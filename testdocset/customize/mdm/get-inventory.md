---
title: Abrufen von Inventar
description: "Des Vorgangs erhalten Inventory Ruft Informationen aus den Windows Store for Business zu ermitteln, ob neue oder aktualisierte Anwendungen zur Verfügung stehen."
MS-HAID:
- p\_phdevicemgmt.get\_seatblock
- p\_phDeviceMgmt.get\_inventory
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: C5485722-FC49-4358-A097-74169B204E74
ms.openlocfilehash: b6624774acef1280b500991d7b1cfc79081d99f8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-inventory"></a>Abrufen von Inventar

Des Vorgangs **Erhalten Inventory** Ruft Informationen aus den Windows Store for Business zu ermitteln, ob neue oder aktualisierte Anwendungen zur Verfügung stehen.

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
<td><p>{ContinuationToken} https://bspmts.MP.Microsoft.com/v1/Inventory?continuationToken=&amp;ModifiedSince = {ModifiedSince}&amp;LicenseTypes = {LicenseType}&amp;MaxResults = {MaxResults}</p></td>
</tr>
</tbody>
</table>


 

### <a name="uri-parameters"></a>URI-Parameter

Die folgenden Parameter können in der Anforderung URI angegeben werden.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Typ</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>continuationToken</p></td>
<td><p>string</p></td>
<td><p>Null</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>modifiedSince</p></td>
<td><p>DateTime</p></td>
<td><p>Null</p></td>
<td><p>Optional Zur Ermittlung von Änderungen gegenüber einem bestimmten Datum verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>licenseTypes</p></td>
<td><p>Auflistung von [LicenseType](data-structures-windows-store-for-business.md#licensetype)</p></td>
<td><p>{online, offline}</p></td>
<td><p>Optional Eine Auflistung von Lizenztypen</p></td>
</tr>
<tr class="even">
<td><p>maxResults</p></td>
<td><p>Integer-32</p></td>
<td><p>25</p></td>
<td><p>Optional Gibt die maximale Anzahl von Anwendungen, die in einer einzelnen Abfrage zurückgegeben.</p></td>
</tr>
</tbody>
</table>




Es folgen einige Beispiele.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Abfragetyp</th>
<th>Beispielabfrage</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Online und offline</p></td>
<td><p>Https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=online&amp;LicenseTypes offline =&amp;MaxResults = 25</p></td>
</tr>
<tr class="even">
<td><p>Nur Online</p></td>
<td><p>Https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=online&amp;MaxResults = 25</p></td>
</tr>
<tr class="odd">
<td><p>Nur im Offlinemodus</p></td>
<td><p>Https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?licenseTypes=offline&amp;MaxResults = 25</p></td>
</tr>
<tr class="even">
<td><p>Lizenztypen und einem Zeitfilter</p></td>
<td><p>Https:<span></span>//bspmts.mp.microsoft.com/V1/Inventory?modifiedSince=2015-07-13T14%3a02%3a25.6863382-07%3a00&amp;LicenseTypes online =&amp;LicenseTypes offline =&amp;MaxResults = 25</p></td>
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
<p>Ungültiges Datum, Lizenz oder ContinuationToken geändert</p>
<p>Details: Zeichenfolge</p></td>
</tr>
</tbody>
</table>




## <a name="response"></a>Antwort

### <a name="response-body"></a>Antworttext

Die Antwort enthält [InventoryResultSet](data-structures-windows-store-for-business.md#inventoryresultset).

 






